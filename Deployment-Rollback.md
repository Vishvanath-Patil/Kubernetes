# Deployment & Rollback

## The following are typical use cases of deployments.-

1. Create a deployment to rule out a replica set The replica set creates pod in the background. Check the status of the rollout to see if it succeed or not.

2. Declare the new stable of the parts. by updating the quad template spec. of the deployment, a new replica set is created and deployment manages the moving the parts from the old replica set to the new one at a controller control rate. Each new replica sets update the version of the deployment

3. Rollback to an earlier deployment revision--> If the current state of deployment is not stable, each rollback updates the revision of the deployment.

4. Scale up the deployment to facilities more and load

5. Pause the deployment to apply multiple fixed to its. pod templates spec and then resume it to start a new rollout.

6. Clean up older replica set that you can't need anymore.

7. if there are problems in the deployment, kubernetes will automatically roll back to the previour version, however you can also explicitly rollback to a specific revision as in ourcase to Revision 1 (the OriginalPod version )

8. You can rollback to a specific version specifying it with --to-revision

for Ex-> kubectl rollout undo deploy/mydeployments --to-revision

## Note: That the name of the Replicaset
is always formatted as [Deployment-name]-[Random string]
```shell
kubectl get deploy
```
## when you inspect the deployment in your cluster the following field are display

NAME --> List the names of the deployments in the namespace

READY --> Display how many replicas of the application are available to your users if follows the pattern ready/Desired

UP-TO-DATE --> Display the number of replicas that have been updated to achieve the desired state.

AVAILABLE --> Displays how many replicas of the application are available of your users

AGE --> Display the amount of time that the application has been Running.

To check deployment was created or not
```shell
kubectl get deployment
```
To check how deplooyment creates RS and pod
```shell
kubectl describe deploy mydeployment
```
```shell
kubectl get rs
```
To Scale up or Scale down
```shell
kubectl scale --replicas=1 deployment mydeployment
```
To Check what is running inside container or logs 
```shell
kubectl logs <POD_NAME>
```
```shell
kubectl rollout status deployment mydeployment
```
```shell
kubectl rollout history deployment mydeployment
```
```shell
kubectl rollout undo deployment
```
# Failed Deployment Possible Reasons 

Your deployment may get stuck trying to deploy its newest ReplicaSet without ever Completing This can Occur Due to Some of the following factors.

1. Insufficient Quota
2. Readiness probe error
3. Image pull error
4. Insufficient permission
5. Limit Ranges
6. Application runtime misconfiguration

# Deployment YAML File
```shell
mydeployment.yaml
```
```shell
kind: Deployment
apiVersion: apps/v1
metadata:
   name: mydeployments
spec:
   replicas: 2
   selector:     
    matchLabels:
     name: deployment
   template:
     metadata:
       name: testpod
       labels:
         name: deployment
     spec:
      containers:
        - name: c00
          image: ubuntu
          command: ["/bin/bash", "-c", "while true; do echo Technical-Guftgu; sleep 5; done"]
```
