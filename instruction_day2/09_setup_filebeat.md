# 09_setup_filebeat
You deploy Filebeat as a DaemonSet to ensure there’s a running instance on each node of the cluster.

The container logs host folder (/var/log/containers) is mounted on the Filebeat container. Filebeat starts an input for the files and begins harvesting them as soon as they appear in the folder.

Everything is deployed under the "infra-logging" namespace.
<!-- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -->


## Objectives
- Send cont
ainer logs to the ELK system and display them on the Kibana console.

## Expected Outcome
- Container logs appear on the Kibana console.


## Prerequisites
- Must finish task: 01_setup_k8s, 02_deploy_simple_apps.md


## Installation
### 1. Create New Namespace for logging 
```sh
kubectl create namespace logging
```

### 2. Apply a custom role to grant Filebeat permission to retrieve container logs.
```sh
kubectl apply -f https://raw.githubusercontent.com/chayapon-s/kbtg-infra-kampus-bootcamp2024/main/instruction_day2/yaml/filebeat-role.yml
```

### 3. Download the ConfigMap and modify the Filebeat configuration for each group.
```sh
curl -LO https://raw.githubusercontent.com/chayapon-s/kbtg-infra-kampus-bootcamp2024/main/instruction_day2/yaml/filebeat-configmap.yml
```

modify filebeat-configmap.yml at line23: change value from bbtg-group-x to 'bbtg-group-<group_number>'
```sh
vi filebeat-configmap.yml
```

apply the filebeat configuration.
```sh
kubectl apply -f filebeat-configmap.yml
```

### 3. Deploy filebeat agent as daemonset
```sh
kubectl apply -f https://raw.githubusercontent.com/chayapon-s/kbtg-infra-kampus-bootcamp2024/main/instruction_day2/yaml/filebeat-daemonset.yml
```

## Verify
Now you can verify that all filebeat pods exist.
```sh
kubectl get pod -n logging
```

The response should be like this:
```sh

```