Deployment & Rollback
=====================
The following air typical use cases of deployments.-

Create a deployment to rule out a replica set The replica set creates pod in the background. Check the status of the rollout to see if it succeed or not.

Declare the new stable of the parts. by updating the quad template spec. of the deployment, a new replica set is created and deployment manages the moving the parts from the old replica set to the new one at a controller control rate. Each new replica sets update the version of the deployment

Rollback to an earlier deployment revision--> If the current state of deployment is not stable, each rollback updates the revision of the deployment.

Scale up the deployment to facilities more and load

Pause the deployment to apply multiple fixed to its. pod templates spec and then resume it to start a new rollout.

Clean up older replica set that you can't need anymore.

if there are problems in the deployment, kubernetes will automatically roll back to the previour version, however you can also explicitly rollback to a specific revision as in ourcase to Revision 1 (the OriginalPod version )

You can rollback to a specific version specifying it with --to-revision

for Ex-> kubectl rollout undo deploy/mydeployments --to-revision

Note: That the name of the Replicaset
is always formatted as [Deployment-name]-[Random string]
kubectl get deploy
