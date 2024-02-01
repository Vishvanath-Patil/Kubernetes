# Minikube Installation on Ubuntu 22.04 LTS (EC2)
## Pre-Requites 
1. Choose Ubuntu 22.04 LTS ( t2.medium ) because min 2 CPU and 4 GB Memory and 20GB Free Disk Space
2. Docker or VirtualBox
3. curl
4. Kubectl
   

## Docker Installation 
``` shell
sudo apt-get update
sudo apt install docker.io
sudo chown $USER /var/run/docker.sock
sudo usermod -aG docker $USER
systemctl status docker
docker ps
```

## Ensure that curl is also installed:
``` shell
sudo apt-get update && sudo apt-get install -y curl
```

## Kubectl Installation
``` shell
curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/1.19.6/2021-01-05/bin/linux/amd64/kubectl
chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin
kubectl version --short --client
```

# Installing Minikube:
## Step 1: Install VirtualBox (if not already installed)
``` shell
sudo apt-get update
sudo apt-get install -y virtualbox virtualbox-ext-pack
```
## Step 2: Install Minikube
### Download the latest version of Minikube using curl:
``` shell
curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 \
&& chmod +x minikube && sudo mv minikube /usr/local/bin/
```
## Step 3: Start Minikube
### Begin Minikube with the following command, setting VirtualBox as the VM driver:
``` shell
minikube start - vm-driver=virtualbox
```
### 2. Confirm the status of your Minikube cluster:
``` shell
minikube status
```
