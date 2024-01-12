# 04_setup_ansible
Ansible is an open-source automation tool that is used for configuration management, application deployment, task automation, and orchestration. Developed by Red Hat, Ansible simplifies complex tasks and processes, allowing users to manage and automate infrastructure more efficiently.

## Objectives
- Setup Ansible for this workshop to automate tasks in the future.

## Expected Outcome
- Ansible is ready to use.

## Prerequisites
- no prerequisites

## Installation
> [!NOTE]
> The following instruction for the [helper] only.

Install ansible packages
```sh
dnf install -y epel-release 
dnf install -y ansible 
```

## Verify
Run this command to get ansible version
```sh
ansible -version 
```
The response should be like this
```sh
# ansible --version
ansible [core 2.16.2]
  config file = /etc/ansible/ansible.cfg
  configured module search path = ['/root/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python3.11/site-packages/ansible
  ansible collection location = /root/.ansible/collections:/usr/share/ansible/collections
  executable location = /bin/ansible
  python version = 3.11.5 (main, Oct 25 2023, 14:45:39) [GCC 8.5.0 20210514 (Red Hat 8.5.0-21)] (/usr/bin/python3.11)
  jinja version = 3.1.2
  libyaml = True 
```