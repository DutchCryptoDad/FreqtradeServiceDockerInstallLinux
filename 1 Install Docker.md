We will be installing Docker Community Edition, which is free to use and open source.

I will not be using the apt cache system but want to manually execute every step of the way.

## Download

Download the package for my distribution

Compare my Linux Mint version with Ubuntu version to determine which Docker package to download on:  
https://en.wikipedia.org/wiki/Linux_Mint

Linux Mint Uma (20.2) is based on Ubuntu Focal Fossa (20.04) in my case.

Then:

Go to https://download.docker.com/linux/ubuntu/dists/focal/pool/stable/amd64/

And download the following packages manually (these are the latest versions):

* docker-ce_20.10.9~3-0~ubuntu-focal_amd64.deb 
* docker-ce-cli_20.10.9~3-0~ubuntu-focal_amd64.deb
* containerd.io_1.4.9-1_amd64.deb

Or download via the terminal with wget:

```
cd Downloads
wget https://download.docker.com/linux/ubuntu/dists/focal/pool/stable/amd64/docker-ce_20.10.9~3-0~ubuntu-focal_amd64.deb  \
https://download.docker.com/linux/ubuntu/dists/focal/pool/stable/amd64/docker-ce-cli_20.10.9~3-0~ubuntu-focal_amd64.deb \
https://download.docker.com/linux/ubuntu/dists/focal/pool/stable/amd64/containerd.io_1.4.9-1_amd64.deb \
https://download.docker.com/linux/ubuntu/dists/focal/pool/stable/amd64/docker-ce-rootless-extras_20.10.9~3-0~ubuntu-focal_amd64.deb \
https://download.docker.com/linux/ubuntu/dists/focal/pool/stable/amd64/docker-scan-plugin_0.9.0~ubuntu-focal_amd64.deb
```

## Installation

Install the downloaded packages with:

```
sudo apt install ./containerd.io_1.4.9-1_amd64.deb ./docker-ce-cli_20.10.9~3-0~ubuntu-focal_amd64.deb ./docker-ce-rootless-extras_20.10.9~3-0~ubuntu-focal_amd64.deb ./docker-scan-plugin_0.9.0~ubuntu-focal_amd64.deb ./docker-ce_20.10.9~3-0~ubuntu-focal_amd64.deb
```

## Verify

Verify that Docker Engine is installed correctly by running the hello-world image:

```
sudo docker run hello-world
```

Which produces the following result:

```
sudo docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
2db29710123e: Pull complete 
Digest: sha256:cc15c5b292d8525effc0f89cb299f1804f3a725c8d05e158653a563f15e4f685
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```

Now you can remove or archive the downloaded Docker .deb installation files.

## Download and install Docker Compose

Docker compose is necessary for downloading and installing the Freqtrade Docker container.


```
sudo wget -O  /usr/local/bin/docker-compose https://github.com/docker/compose/releases/download/v2.1.1/docker-compose-linux-x86_64
sudo chmod +x /usr/local/bin/docker-compose
```

## More

More on installing Docker see:
 
https://docs.docker.com/engine/install/ubuntu/
