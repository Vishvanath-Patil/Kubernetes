
# HealthCheck /LivenessProbe

A pod. is considered ready when all of its container a ready

In order to verify if a container in A pod is healthy and ready to serve traffic, Kubernetes provides for a range of healthy checking mechanism.

Healthex or proofs air carried out by the equivalent to determine when to restart a container. (For all liveness probe.)

And used by service and deployments to determine if a part should receive traffic.

For example: Liveness probe could catch a deadlock. where an application is running. but unable to make progress restarting. a container in such a state can help to make the application more available despite bugs.

One use of readiness probe is to control which part's air used as vacant for services when a pod is not ready. It is removed from service load balancer.

For running health checks, we would use Cmd's specific to the application.

If the CMD succeeds. it returns zero and the cublet consider the container to be alive and healthy. If the command returns non zero value, the cumulative kills the podium. and recreate it.

## liveness.yml
```shell
apiVersion: v1
kind: Pod
metadata:
  labels:
    test: liveness
  name: mylivenessprobe
spec:
  containers:
  - name: liveness
    image: ubuntu
    args:
    - /bin/sh
    - -c
    - touch /tmp/healthy; sleep 1000
    livenessProbe:                                          
      exec:
        command:                                         
        - cat                
        - /tmp/healthy
      initialDelaySeconds: 5          
      periodSeconds: 5                                 
      timeoutSeconds: 30
```
