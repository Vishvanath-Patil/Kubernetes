# Persistant Volume
## Some Important Points
In a typical IT environment, storage is managed by the storage/ system administrator 

The End User will just get instructions to use the storage, but does not have to Worry about the underlying storage management

In the Containerzed World, We would like to follow similar rules but it becomes challenging, given the many volume types 

we have seen eralie kubernetes resolves this problem with the Persistent Volume (PV) subsystem.

A Persistant Volume (PV) is a cluster-wide resource that you can use to store data in a way that it persist beyond the lifetime of a pod

The PV is not Backed by locally attcahed storage on a worrker node but by networked storage system such as EBS or NFS or distributed filesystem like Cegh

K8s provides APIs for users and administartor to manage and consume storage to manage the Volume, it uses the Persistent

Volume API resource type and to Consume it, uses the PersistentVolume-Claim APIresoursce type.

PersistantVolumeClaim

In Order to use a PV you need to Cliam it first, Using a Persistant Volume Claim (PVC)

The PVC request a PV wuth your desired specification (size, access modes, speed etc..) from kubernetes and Once a Suitable Persistant Volume is found it is bound to a PersistantVolumeClaim

After a successfull bound to a pod, you can mount it as a Volume.

After a suucesful bound to a pod, you can mount it as a volume

Once a user finishes its works, the attached PersistantVolume can be released The Underlying PV can there be reclaimed and Recycled for future usage.

AWS EBS
=======
An AWS EBS Volumemounts an AWS EBS Volume into your pod Unlike
emptydir, which is erased when a pod is removed, the content of an EBS Volume are preserved and the Volume is merely Unmounted

These are Some Restictions:

1. The nodes on which Pods are running must be AWS EC2 instances

2.Those instance need to be in the same region and avilability Zine as the EBS Volume.

3.EBS Only supports a single EC2 instance mouting a Volume.
# Lab
## Here used AWS EBS Volume which `volumeID` Copied to PV.yml file
pv.yml
```shell
apiVersion: v1
kind: PersistentVolume
metadata:
  name: myebsvol
spec:
  capacity:
    storage: 1Gi
  accessModes:
    - ReadWriteOnce
  persistentVolumeReclaimPolicy: Recycle
  awsElasticBlockStore:
    volumeID:           # YAHAN APNI EBS VOLUME ID DAALO
    fsType: ext4
```
```shell
kubectl apply -f pvc.yml
```
```shell
kubectl get pv
```
```shell
kubectl get pods
```
# Persistance Volume Claim
## pvc.yml
```shell
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: myebsvolclaim
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 1Gi
```
```shell
kubectl apply -f pvc.yml
```
# Deploymentpvc.yml
```shell
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: myebsvolclaim
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 1Gi
```
```shell
kubectl apply -f Deploymentpvc.yml
```
## Task
```shell
kubectl get pods
```
## Login to ubuntu Container
```shell
kubectl exec <PODNAME> -it -- /bin/bash 
```
## Create Directory on container
```shell
cd /tmp/persistant
```
vi testfile
add some content
Esc + wq:
```shell
kubectl delete pod <PODNAME>
```
Login to new pod check the tmp/persistant data




