## Communication Between Containers 
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
```shell
apt update && apt install curl
```

