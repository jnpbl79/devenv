# Installing Docker on Ubuntu

```shell
$ curl -fsSL get.docker.com -o get-docker.sh
$ sudo sh get-docker.sh
```

Verify that Docker Engine is installed correctly by running the `hello-world` image.
```bash
$ sudo docker run hello-world
```

In order to upgrade Docker, you will need to use the package manager on your host. Rerunning the script can cause issues if it attempts to re-add repositories that were already added. See the previous recipes to learn how to upgrade Docker on CentOS and Ubuntu using their respective package managers.

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

-----
 - [Installing Docker on Linux with an automated script](https://subscription.packtpub.com/book/virtualization_and_cloud/9781788626866/1/ch01lvl1sec15/installing-docker-on-linux-with-an-automated-script)
 - [Install Docker Engine on Ubuntu](https://docs.docker.com/engine/install/ubuntu/)
 - [Post-installation steps for Linux](https://docs.docker.com/engine/install/linux-postinstall/)
