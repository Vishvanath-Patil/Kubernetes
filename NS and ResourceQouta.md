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
