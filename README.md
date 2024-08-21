# KubernetesHelm

## Table of content

- [Udemy courses](#udemy-course)
- [Install Kubernetes on Linux](#install-kubernetes-on-linux)
  - [Docker](#docker)
  - [Kubectl](#kubectl)
  - [Minikube](#minikube)
- [Yml](#yaml)
- [Commands](#commands)
- [Comments](#comments)

## Udemy course

**[`^ top ^`](#kuberneteshelm)** | **[`^ Table of content ^`](#table-of-content)**

- [https://www.udemy.com/course/learn-kubernetes](https://www.udemy.com/course/learn-kubernetes)
- [https://www.udemy.com/course/certified-kubernetes-application-developer](https://www.udemy.com/course/certified-kubernetes-application-developer)

## Install Kubernetes on Linux

**[`^ top ^`](#kuberneteshelm)** | **[`^ Table of content ^`](#table-of-content)**

### Docker

```
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/debian/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/debian \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

```
sudo docker run hello-world
```

### Kubectl

```
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256"
echo "$(cat kubectl.sha256)  kubectl" | sha256sum --check
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
kubectl version --client
kubectl version --client --output=yaml

```

### Minikube

```
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64
minikube start --driver=docker
minikube config set driver docker
kubectl get po -A
minikube kubectl -- get po -A
sudo usermod -aG docker $USER && newgrp docker
```

## Yml

**[`^ top ^`](#kuberneteshelm)** | **[`^ Table of content ^`](#table-of-content)**

```
apiVersion: v1
kind: Pod
metadata:
  name: myapp-pod
  labels:
    app: myapp
    type: front-end

spec:
  containers:
    -  name: nginx-container
       image: nginx
```

| Type       | Version |
| ---------- | ------- |
| Pod        | v1      |
| Service    | v1      |
| ReplicaSet | apps/v1 |
| Deploymnet | apps/v1 |

## Commands

**[`^ top ^`](#kuberneteshelm)** | **[`^ Table of content ^`](#table-of-content)**

```
kubectl create -f object-defenition.yml
```

```
kubectl get pods
kubectl describe pod myapp-pod
```

## Comments

**[`^ top ^`](#kuberneteshelm)** | **[`^ Table of content ^`](#table-of-content)**
