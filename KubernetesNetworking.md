## Communication Between Containers 
kubernetes Netwrking address four concerns
1. Containers within pod use networking to communicate via loopback
2. Cluster networking provides Communication between different pods
3. The Service Resources lets you expose an application running in pods to be reachable from outside you cluster
4. Contrainer to Container Communication on Same pod happens though localhost within the containers.
   
pod.yaml
```shell

kind: Pod
apiVersion: v1
metadata:
  name: testpod
spec:
  containers:
    - name: c00
      image: ubuntu
      command: ["/bin/bash", "-c", "while true; do echo Hello-Bhupinder; sleep 5 ; done"]
    - name: c01
      image: httpd
      ports:
       - containerPort: 80
```
Login to `c00` Container
```shell
kubectl exec testpod -it -c c00 -- /bin/bash
```
Run commads inside container
```shell
apt update && apt install curl
```
```shell
curl localhost:80
```
Delete pod.yaml
```shell
kubectl delete -f pod.yaml
```
## Communication Different Pods within Cluster
1. Pod to Pod Communication on same worker node happens through Pod IP
2. By Default Pod's IP will not be accessable Outside the node.
pod1-nginx.yaml //installed nginx
```shell
kind: Pod
apiVersion: v1
metadata:
  name: nginx
spec:
  containers:
    - name: c01
      image: nginx
      ports:
        - containerPort: 80
```
```shell
kubectl apply -f nginx.yaml
```
## pod2-https.yaml

```shell
kind: Pod
apiVersion: v1
metadata:
  name: httpd
spec:
  containers:
    - name: c01
      image: httpd
      ports:
        - containerPort: 80
```
```shell
kubectl apply -f nginx.yaml
```
```shell
kubectl get pods
```
```shell
kubectl get pods -o wide
```
```shell
curl 10.0.8.99:80
```

# Object - Services 

1. When using RC spots air terminated and created during scaling or replication operations.

2. When using deployments while updating the image version, the pods are terminated and new parts take the place of the other pods.

3. Pods are very dynamic. They come and go on the Kubernetes cluster and on any of the available nodes. And it would be difficult to access the parts as the pod ip change once it is recreated.

4. Survey subject is an logical breeds between pods and end users. Which provides virtual IP?

5. Service allows client to reliably connect to the containers using in the pod, using the virtual ip.

6. The virtual ip is not an actual ip connect to the network. Interface, but its purpose is to purely forward traffic to the one or more pods.

7. kube-Proxy is the one which keeps the mapping between the virtual IP and the parts up to date, which queries the api servers to learn about new services in the cluster.
Although each pod has unique ip address. Those ips are not exposed outside the cluster.
Services helps to expose the virtual IP map to the pods and allows application to receive traffic.

Labels are used to select which air the pods to be put under the surface.

Creating a service will create an endpoint to access the pods. Replication in it.

Services can be exposed in different ways by specifying a type in the service spec

1. ClusterIP
2. NodePort
3. LoadBalancer - Created by cloud provider that will route external traffic to every node on the node port (eg : ELB on AWS)


Headless--> Creates several endpoints that are used to Phudos DNS Records. Each dns record is bound to a pod.

By default service can only run between ports. 3000 to 32767

The set of pods targeted by services is usually determined by the selector.

# NodePort
Makes a service accessable from Outside the Cluster
Exposes the Service on the Samr Port of each selected node in the Cluster using NAT


