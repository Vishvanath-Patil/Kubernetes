# Namespace

1. You can name your object, but if many are using the cluster, then it would be difficult for managing.

2. A namespace is a group of related elements that you. have a unique name or identifier namespace is used to uniquely identify one or more names from other similar names of different objects, groups or the namespace in general.

3. Kubernetes namespace helps different project. teams are customer to share a covernet's cluster and provides.

## A scope of every namespace.

1. A mechanism to. attach authorization and policy To subsection of the cluster.

By default, kubernetes cluster will. instantiate a default namespace when provisioning the cluster to hold the default set of parts services. and deployments used by the cluster.

We can use resource quota on specifying how many resources each namespace can use.

Most Kubernetes Resources (example parts services replication controller and others) air in some namespace and low level resources such as nodes and persistent volumes. They're not. in any namespace.

Namespaces air intended for. use in environment with many uses spread across multiple teams or projects for cluster with a feud to 10s of users. You should not need to create or think. about namespace and all

# Create new namespace.
Let us assume we have said coverage cluster for dev and production. Use class.
The dev team would like. to maintain a space in the cluster where they can get a view on the list of parts services and deployments they use to build and run their application in this. no restrictions airport on who can or cannot modify resources to enable assail deployment.
For prod team, we can enforce strict procedures on who can or cannot manipulate the set of parts services and deployments.
### Command to list namespaces
```shell
kubectl get ns
```
## Command fetch pods from default namespace
```shell
kubectl get pods 
```
## Command to Create Namespace
```shell
kubectl create namespace <Namespace-Name>
```
```shell
kubectl create nampespace Dev
```
```shell
kubectl create namespace PPE-Stage
```
## Command to fetch pods from specific namespace i.e Dev, Prod, PPE-Stage
```shell
kubectl get pods -n <NamespaceName>
```
## Creating ns using yaml file
`vi devns.yml`
```shell
apiVersion: v1
kind: Namespace
metadata:
   name: dev
   labels:
     name: dev
```
`vi pod.yml`

```shell
kind: Pod                              
apiVersion: v1                     
metadata:                           
  name: testpod                  
spec:                                    
  containers:                      
    - name: c00                     
      image: ubuntu              
      command: ["/bin/bash", "-c", "while true; do echo Technical Guftgu; sleep 5 ; done"]
  restartPolicy: Never
```
### Create a pod inside dev namespace   
```shell
kubectl apply -f pod.yml -n dev
```
```shell
kubectl get pods -n dev
```
### Set context for namespace
```shell
kubectl config set-context $(kubectl config current-context) --namespace=dev
```
### kubeconfig view 
```shell
kubectl config view | grep namespace
```
# Resource Qouta 
## Managing Compute Resources for containers.

1. A pod in Kubernetes will run with no limits on CPU and memory.

2. You can optionally specify how much CPU and Memory(RAM) each container needs.

3. Scheduler decides about which nodes to place pod, only if the Node has enough CPU Resources available to specify the Pod CPU request.

4. CPU is specified in units of Cores and memory is specified in units of bytes.

## Two types of container can be set for each resource type -request limit.

1. A request is the amount of that resources the system will guarantee for the container and Kubernetes will use this value to decide on which node to place the pod.

2. A limit is the maximum amount of resources that kubernetes will allow the container to use in the case that request is not set for container. It default to limits. if limit is not set, then if default to zero.

3. CPU values are specified in Milli CPU and memory in MiB.

4. A Kubernetes cluster can be divided into namespaces if a pod is created in a namespace that has a default cpu limit and the container does not specify its own cpu limit, then the container is assigned the default CPU limit.

5. Namespaces can be assigned resources quota objects. This will limit the amount of usage allowed to the objects in that namespaces.

### You Can Limit

1. Compute
2. Memory
3. Storage

## Here, are two restrictions that a resource quota Imposes on a namespaces.

1. Every container that runs in a namespaces must have. its own CPU limit.

2. The total amount of CPU used by all containers in the namespace must not Exceed a specified limit.
