# 03_setup_monitoring_k8s
Metrics Server is a scalable, efficient source of container resource metrics for Kubernetes built-in autoscaling pipelines.


## install Metric servers
```sh
kubectl apply -f https://raw.githubusercontent.com/chayapon-s/kbtg-infra-kampus-bootcamp2024/main/instruction_day1/yaml/metric-server-k8s.yml
```

## Verify
Now you can verify that all objects exist and can collect CPU/Memory metrics.
### Get pod metrics
```sh
kubectl top pod
```

The response should be like this:
```sh
NAME                               CPU(cores)   MEMORY(bytes)
wordpress-66d6c4fd9-7nzgm          1m           125Mi
wordpress-mysql-86b9f64c4c-qzdll   4m           509Mi
```
### Get node metrics
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