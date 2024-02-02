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
