# ConfigMap
1. While performing application deployments on covert cluster. Sometimes we need to change the application configuration file depending on environments like dev qa stage or prod.

2. Changing this application configuration file. means we need to change source code, commit the change, creating new image, and then go through complete deployment process.

Hence, these configurations should be decoupled from image content in order to keep. application portable.

This is where covert configmap comes handy. It allows us to handle configuration files much more efficiently.

3. Configmaps are useful for storing and sharing nonsensical, unencrypted configurations, information use secrets otherwise.

4. Configmap can be used to store fine gained information like individual properties or entire config file.

5. Configmap are not intended. to act as replacement for properties file.

Configmap can be accessed In two ways.:-

1. As environment variable.
2. As volume in the Pod

   Steps to Create ConfigMap
   ### Step 1:
   #### create sample.conf
   ```shell
   vi sample.conf
   ```
   ### Step 2:
   ```shell
   kubectl create configmap mymap --from-file=sample.conf
   ```
   #### depploymentconfigmap.yml
```shell
apiVersion: v1
kind: Pod
metadata:
  name: myvolconfig
spec:
  containers:
  - name: c1
    image: centos
    command: ["/bin/bash", "-c", "while true; do echo Technical-Guftgu; sleep 5 ; done"]
    volumeMounts:
      - name: testconfigmap
        mountPath: "/tmp/config"   # the config files will be mounted as ReadOnly by default here
  volumes:
  - name: testconfigmap
    configMap:
       name: mymap   # this should match the config map name created in the first step
       items:
       - key: sample.conf
         path: sample.conf
```

```shell
kubectl get pods
```
```shell
kubectl apply -f deploymentconfig.yml
```
Login to container
```shell
kubectl exec <PODNAME> -it /bin/bash
```
### ConfigMap Accessing though Environment Variable
```shell
kubectl apply -f deployenv.yml
```
```shell
apiVersion: v1
kind: Pod
metadata:
  name: myenvconfig
spec:
  containers:
  - name: c1
    image: centos
    command: ["/bin/bash", "-c", "while true; do echo Technical-Guftgu; sleep 5 ; done"]
    env:
    - name: MYENV         # env name in which value of the key is stored
      valueFrom:
        configMapKeyRef:
          name: mymap      # name of the config created
          key: sample.conf            
```
```shell
kubectl get pods
```
```shell
kubectl exec <PODNAME> -it -- /bin/bash
```
```shell
env
```
```shell
echo $MYENV
```

SECRETS
=======
You don't want sensitive information such as database password or in api key kept around in. clear test.

Secrets provide you with a mechanism to use such information in a safe and reliable way with the following properties:-

1. Secrets air namespaced object. that is exist in the contest of namespace.
2. You can access them via a volume or an environment variable from a container running in a pod.
3. The secret data on nodes is stored in tempFS volumes bracket. tempFS is a file system which keeps all files in virtual memory. Everything in tempFS is temporary in the. sense that no file will be created on your hard drive.
4. A per secret size limit of 1MB exists.
5. The API server stores secrets as plaintext in ETCD.
## Secrets can be created.
1. From a text file.
2. From a yaml file.

   ### Steps Create Secrets
   #### Create files in local system (worker-node)
   ```shell
   echo "root" > username.txt ; echo "mypassword123" > password.txt
   ```
   #### Create Secret
   ```shell
   kubectl create secret generic mysecret --from-file=username.txt --from-file=password.txt
   ```
   ```shell
   kubectl get secret
   ```
   ```shell
   kubectl describe secret <SECRET-NAME>
   ```
   ### deploysecret.yml
   ```shell
   apiVersion: v1
kind: Pod
metadata:
  name: myvolsecret
spec:
  containers:
  - name: c1
    image: centos
    command: ["/bin/bash", "-c", "while true; do echo Technical-guftgu; sleep 5 ; done"]
    volumeMounts:
      - name: testsecret
        mountPath: "/tmp/mysecrets"   # the secret files will be mounted as ReadOnly by default here
  volumes:
  - name: testsecret
    secret:
       secretName: mysecret
    ```
```shell
kubectl get pods
```
```shell
kubectl exec <POD-NAME> -it -- /bin/bash
```
```shell
cd tmp
```

