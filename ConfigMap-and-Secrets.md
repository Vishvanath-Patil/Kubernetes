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
