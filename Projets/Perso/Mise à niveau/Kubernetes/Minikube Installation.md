
# Minikube + WSL + 

https://gist.github.com/wholroyd/748e09ca0b78897750791172b2abb051

https://devopssec.fr/article/minikube-installation-manipulation-cluster-kubernetes


# Guide pero : install minikube on WSL and run with docker

From : https://gist.github.com/wholroyd/748e09ca0b78897750791172b2abb051

follow step 1 to 6

### Ubuntu Preparation

[](https://gist.github.com/wholroyd/748e09ca0b78897750791172b2abb051#ubuntu-preparation)

1. Run series of commands to get right build of Docker installed
    - Removes the old crap, gets the dependencies right, adds Docker key, adds Docker repo, installs the new hotness

```
sudo apt-get remove docker docker-engine docker.io containerd runc
sudo apt-get update
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
sudo apt-get update
sudo apt-get upgrade -y
sudo apt-get install docker-ce docker-ce-cli containerd.io -y
```

Install minikube

```
curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
chmod +x ./minikube
sudo mv ./minikube /usr/local/bin/
minikube config set driver docker
```

Config docker user and run minikube

1. **Add your user to the Docker group:**
        
    `sudo usermod -aG docker $USER`
    
2. **Apply the new group membership without logging out and back in:**
    `newgrp docker`
    

Alternatively, you can log out and log back in to apply the group changes.

3. **Verify your user is added to the Docker group:**   
    `groups $USER`
        
4. **Restart Minikube:**    
    `minikube start`


Installer Kubectl

```shell
curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl && \ 
chmod +x kubectl
```
