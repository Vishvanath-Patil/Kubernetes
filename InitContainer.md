init container are specilized container that run before appl container in a pod

init container always run to completion

if a pod's init container fails, kubernetes repeatedly restarts the pod until the init container succeeds

init container do no support readiness Probe

Use Cases
=========

Seeding a Database

Delaying the application launch untill the dependencies are ready.

Clone a git repository into a Volume

Generate Configuration file dynamically.

Pod Conditions
==============
 A pod has a pod status, which has an array of Pod conditions though which the pod has or has not passed

--> Using "kubectl describe pod <PODNAME>
you can get contion of a pod

These are the possible Types
============================

PodScheduled: the pod has been schedule to a node
============

Ready: The pod is able to serve request and will be added to the load Balancing pools of all matching Services

Intialized:- All init containers have started successfully.

Unschedured:- The scheduler cannot schedule the pod right now, fot ex: due to lacking of Resources or Other Constarins

ContainerReady: All Containers in the pod are ready.
