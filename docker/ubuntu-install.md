---
title: Install Docker on Ubuntu
tags:
  - docker
  - ubuntu
---

# Installing Docker on Ubuntu

## Install using the repository

Before you install Docker Engine for the first time on a new host machine, you need to set up the Docker repository. Afterward, you can install and update Docker from the repository.

### SET UP THE REPOSITORY

Update the `apt` package index and install packages to allow `apt` to use a repository over HTTPS:
```bash
$ sudo apt-get update

$ sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
```

Add Docker’s official GPG key:
```bash
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

Set up **stable** repository.
```bash
$ sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
```

### INSTALL DOCKER ENGINE

Update the `apt` package index, and install the latest version of Docker Engine and containerd, or go to the next step to install a specific version:
```bash
$ sudo apt-get update
$ sudo apt-get install docker-ce docker-ce-cli containerd.io
```

Verify that Docker Engine is installed correctly by running the `hello-world` image.
```bash
$ sudo docker run hello-world
```

## Install Docker-Compose

```bash
sudo curl -L "https://github.com/docker/compose/releases/download/1.28.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

Apply executable permissions to the binary:

```bash
sudo chmod +x /usr/local/bin/docker-compose
```

## Post Installation Steps

Create the `docker` group.
```bash
$ sudo groupadd docker
```

Add your user to the docker group.
```bash
$ sudo usermod -aG docker $USER
```

### Configure Docker to start on boot
```bash
$ sudo systemctl enable docker.service
$ sudo systemctl enable containerd.service
```
