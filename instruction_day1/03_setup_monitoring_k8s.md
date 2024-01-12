# 03_setup_monitoring_k8s
Metrics Server is a scalable, efficient source of container resource metrics for Kubernetes built-in autoscaling pipelines.
![Slide4](https://github.com/chayapon-s/kbtg-infra-kampus-bootcamp2024/assets/49383429/9c0b5b49-3de9-407d-a349-3f0a233372fe)


## 1) install Metric servers
```sh
kubectl apply -f https://raw.githubusercontent.com/chayapon-s/kbtg-infra-kampus-bootcamp2024/main/instruction_day1/yaml/metric-server-k8s.yml
```

### Verify
Now you can verify that all objects exist and can collect CPU/Memory metrics.
Get pod metrics
```sh
kubectl top pod
```

The response should be like this:
```sh
NAME                               CPU(cores)   MEMORY(bytes)
wordpress-66d6c4fd9-7nzgm          1m           125Mi
wordpress-mysql-86b9f64c4c-qzdll   4m           509Mi
```
Get node metrics
```sh
kubectl top nodes
```

The response should be like this:
```sh
NAME                 CPU(cores)   CPU%   MEMORY(bytes)   MEMORY%
k8s-master01.local   182m         9%     1849Mi          24%
k8s-worker01.local   93m          4%     1871Mi          24%
k8s-worker02.local   69m          3%     1526Mi          20%
```

## 2) Setup Prometheus for kubernetes cluster
### Prepare Prometheus packages
```sh
git clone https://github.com/bibinwilson/kubernetes-prometheus 
```

### Prepare kubernetes resources for prometheus
```sh
kubectl create namespace monitoring 
kubectl create -f clusterRole.yaml 
kubectl create -f config-map.yaml 
kubectl create  -f prometheus-deployment.yaml 
kubectl get deployments --namespace=monitoring 
kubectl get pods --namespace=monitoring 
kubectl create -f prometheus-service.yaml --namespace=monitoring 
```
Verify that the Service is running by running the following command:
```sh
kubectl get svc -n monitoring
```
The response should be like this:
```sh
NAME                 TYPE       CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE
prometheus-service   NodePort   10.99.133.163   <none>        8080:30000/TCP   2m4s
```

### Copy the Public IP address for master node, and load the page in your browser to view your site with port 30000
```sh
http://<master-ipaddress>:30000
```
