## Statefulsets are Kubernetes Resource that allow us to deploy and manage stateful application.
Statefulset are almost Similar to Deployment But Few Additional Feature provides StatefulSets 
1. StatefulSets assign stable and predictable hostnames to pods
2. Ordered Deployment and Scaling:
StatefulSets ensure the ordered creation, scaling, and termination of pods. Each pod is assigned an index, and pods are deployed or scaled in a sequential manner,
maintaining a predictable order.

Example:-
![image](https://github.com/Vishvanath-Patil/Kubernetes/assets/130968991/b95cf9b4-b0a3-44b0-b389-26588dc22622)

it creates pods in sequential manner means one after another
it maintain same names/lables to the pods even if pod deleted and Re-created some other nodes also
like deployment here also we can set replica
StatefulSet Application Ex: Persistant Storage, DB 

## IMPORTANT
### Features:
#### Stable Network Identifiers (Hostname):
StatefulSets assign stable and predictable hostnames to pods, incorporating an ordinal index based on the order of deployment.
This is crucial for stateful applications requiring consistent network identities.

#### Ordered Deployment and Scaling:
StatefulSets ensure the ordered creation, scaling, and termination of pods. Each pod is assigned an index, and pods are deployed or scaled in a sequential manner, 
maintaining a predictable order.

#### Persistent Volume Claim (PVC) Templates:
StatefulSets come with support for PVC templates. Each pod in the StatefulSet gets its own Persistent Volume Claim based on the template, 
allowing for persistent storage that is unique to each pod.

#### Headless Service:
StatefulSets automatically create a headless service by default. This service facilitates DNS-based discovery for each pod, using its stable hostname. 
This is essential for communication and coordination in stateful applications.

#### Pod Identity Retention:
Even after a pod is deleted, StatefulSets retain its identity (hostname) until the StatefulSet itself is deleted. 
This ensures that the stable identity of pods is maintained over time.

#### StatefulSet Controller:
While both Deployments and StatefulSets have controllers, the StatefulSet controller has additional logic to handle the unique requirements of stateful workloads, 
such as ensuring ordered operations and maintaining persistent identities.

#### Volume Initialization:
StatefulSets support volume initialization, allowing you to specify an init container that runs during the pod's startup. 
This is useful for preparing or syncing data before the main application container starts.

