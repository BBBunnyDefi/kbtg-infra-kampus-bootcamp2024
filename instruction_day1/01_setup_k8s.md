# 01 Setup Kubernetes Cluster

<!-- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -->
...

## Getting Started
This tutorial demonstrates how to provision k8s cluster 

## Objectives
- Create kubernetes cluster which 1 master node and 2 worker nodes
- Deploy kubernetes component to worker node such as, kubectl, kubelet, kubeadm and calio network

## Expected Outcome
- the Kubernetes cluster has provisioned completed

## 1) Control Plane Installation
> [!NOTE]
> These instruction is apply for master node (k8s-master01)

### Disable selinux 
```sh
#vi /etc/selinux/config 
SELINUX=disabled 
```

### Install NTP ( Chrony ) 
install chrony package
```sh
dnf install chrony -y 
```
modify configuration file to sync time with server.
```sh
#vi /etc/chrony.conf 
server 158.108.212.149 
```
restart chrony service to apply the effect
```sh
systemctl –now enable chronyd 
```

### Update all packages
```sh
dnf update -y
```
### Set local DNS 
```sh
# Use the private IP address of the EC2 instance to map host file.
# vi /etc/hosts
10.1.10.55  	Master-55.local 
10.1.10.56  	worker-56.local 
10.1.10.57  	worker-57.local 
```
### Disable Swap 
```sh
swapoff -a; sed -i '/swap/d' /etc/fstab 
```
### Install Docker
```sh
# install docker packages
yum install -y yum-utils device-mapper-persistent-data lvm2 
yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo 
yum install -y docker-ce 
# restart docker service
systemctl enable --now docker 
```
### Remove config and restart container (to fix issue)
```sh
rm -rf  /etc/containerd/config.toml 
systemctl restart containerd 
```
### Add the Kubernetes repository to the Linux repository.
```sh
cat >>/etc/yum.repos.d/kubernetes.repo <<EOF 
[kubernetes] 
name=Kubernetes 
baseurl=https://packages.cloud.google.com/yum/repos/kubernetes-el7-x86_64 
enabled=1 
gpgcheck=1 
repo_gpgcheck=1 
gpgkey=https://packages.cloud.google.com/yum/doc/yum-key.gpg 
       https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg 
EOF 
```
### Install Kubernetes packages, including Kubelet, kubeadm, and kubectl.
```sh
yum install -y kubeadm
```
### Enable Kubelet service 
```sh
systemctl enable --now kubelet
```
### Initialize Kubernetes Cluster 
```sh
# Initialize kubernetes cluster
kubeadm init --apiserver-advertise-address=10.1.10.55 --pod-network-cidr=192.168.0.0/16
```
### Deploy Calico Network 
```sh
kubectl create -f https://docs.projectcalico.org/manifests/calico.yaml
```

Waiting for 5 minutes for the control plane to be ready
### Create K8S join command
```sh
kubeadm token create --print-join-command 
```