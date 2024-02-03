# Default range Resource Allocation Per Container
CPU
min cpu request = 0.5
max CPU limit = 1
MEMORY
min memory request = 512miB
max Memory Limit = 1GB

you can define 
cpu request = 200m
memory request = 600MiB

Note: Always cpu or Memory request should be less than limit
 Case1: if you are not defining any limit it will take default values
 
 cpu request = 400m
 memory request = 600MiB
 #### Not defining any limit 
 cpu = 1
 memory = 1GB

## Horizontal pod auto scaler.

Kubernetes has the possibilities to automatically scale parts based on observed. CP utilization, which is horizontal pod auto Scaling..

Scaling can be done only for scalable objects like controller, deployment or replica set.

HPA Is implemented as Kubernetes API resource and a controller.

The controller periodically checks the number of replicas in a replication.

Controller or deployment to match the absorbed average CP utilization to the target specified by users.

--> The HPA is implemented as controlled loop with a period controlled by the controller manager. Horizontal-pod-autoscaler-sync-period flag (Default default value of 30 second).

During each period, the controller manager queries the resources utilization against the Matrics specified in each horizontal pod- autoscalar definition.

Horizontal Pod Autoscaler
=========================
--> For Per-pod Resource Matrix ( like CPU ), The Controller fetches the matrics from the resources matrics API for each pod targeted by the horizontal pod scaler.

--> Then, if a target utilization value is set, the controller calculates the utilization value as a percentage of equivalent resource request on the containers in each pod

--> If a target raw-value is set, the raw metrics values are used directly. The controller then takes the. mean of the utilization. or the raw value across all targeted pods, and produced the ratio used to scale the number of desired replicas.

Colddown period to wait before another Downscale. operation can be performed is controlled by --horizontal-pod-autoscalar-downtime stabilization flag (Default Value of 5min)

Metric server needs to be deployed in the cluster to provide metrics, via The resources matrics API.
```shell
--kubelet--insecure-tls
```
```shell
kubelet autoscale deployment mydeploy --cpu-percent=20 --min=1 --max=10
```
```shell
apiVersion: v1
kind: LimitRange
metadata:
  name: mem-min-max-demo-lr
spec:
  limits:
  - max:
      memory: 1Gi
    min:
      memory: 500Mi
    type: Container
```
```shell
apiVersion: v1
kind: Pod
metadata:
  name: constraints-mem-demo
spec:
  containers:
  - name: constraints-mem-demo-ctr
    image: nginx
    resources:
      limits:
        memory: "800Mi"
      requests:
        memory: "600Mi"
```

- If request is not specified & limit is given, then request = limit
```shell
wget https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml -O metrics-server.yaml
```
`deployhpa.yml`

```shell
kind: Deployment
apiVersion: apps/v1
metadata:
   name: mydeploy
spec:
   replicas: 1
   selector:
    matchLabels:
     name: deployment
   template:
     metadata:
       name: testpod8
       labels:
         name: deployment
     spec:
      containers:
        - name: c00
          image: httpd
          ports:
          - containerPort: 80
          resources:
            limits:
              cpu: 500m
            requests:
              cpu: 200m
```
```shell
kubectl autoscale deployment mydeploy --cpu-percent=20 --min=1 --max=10
```
