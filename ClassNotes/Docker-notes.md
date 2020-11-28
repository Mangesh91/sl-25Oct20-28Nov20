

## Agenda

    Virtualization Overview (Containers vs VM)
    Installation
    Docker Architecture
        - Images
        - Containers
        - Daemon
        - Docker Client
        - Docker Registry (Dockerhub)
    Docker commands
    
    Creating Docker images (Dockerfile)
    Docker Networking
    Docker Volumes
    Docker Compose


## Keywords
    Monolithic vs Microservices Architecture
    Containers
    Hypervisor
        - VMware ESXi
        - MS HyperV 
        - RedHat KVM
        - Oracle VirtualBox
    Older Container (like) Technology
        - chroot
        - bsd jails
        - solaris zones

docker-ce   ---> Community Edition
docker-ee   ---> Enterprise Edition

Mirantis acquired docker EE

Openstack


## Introduction

Docker != Container

**Container Runtime**
    Docker
    rkt
    CoreOS
    runc
    containerd

**Orchestration Platforms**
    - On Premise
        Kubernetes
        Openshift
        Docker Swarm
        Mesosphere
    - Cloud Based (Hosted Kubernetes)
        EKS
        ECS
        AKS
        GKE

Virtual Machines    ---> Hardware level Virtualization
Containers          ---> OS / Kernel Level Virtualization

## Compute Evolution

Physical Machines ---> Virtual Machines ---> Containers ---> Serverless

IT Resources
    - Compute and Memory
    - Networking
    - Storage

## Docker Architecture
    - Docker Host
    - Docker Daemon
    - Images
    - Containers
    - Docker Client
    - Docker Registry (Dockerhub)
        

Templates --> Virtual Machines 
AWS AMIs --> EC2 instances
Docker Images --> Container


VMware Templates
Virtual Box --> Images
OpenStack ---> Images
AWS --> AMIs


## Installation

Linux:
curl -fsSL https://get.docker.com | sh
Mac:
https://docs.docker.com/docker-for-mac/install/
Windows:
https://docs.docker.com/docker-for-windows/install/


## Docker Commands
docker info
docker pull
docker run
        -i - interactive
        -t - tty or terminal
        -d - detached or daemonized mode
exit --> stops the container and exits to docker host
ctrl+P+Q --> exits to docker host without stopping the container

docker rm  --> remove container ---> docker container rm
docker rmi --> remove image ---> docker image rm
docker tag


Dockerfile --> Docker image (docker build) ---> Docker container (docker run)

## Dockerfile

FROM ubuntu:latest

LABEL maintainer="sk12k@sl.com"

RUN apt-get update
RUN apt-get install -y python3

COPY myapp.py /tmp/myapp.py

COPY <source> <destination>

ADD <source> <destination> 

EXPOSE 80
EXPOSE 443
EXPOSE 8080

ENV

CMD ./myapp.py

ENTRYPOINT

## Sample Dockerfile

FROM ubuntu:latest

LABEL maintainer="sk12k@sl.com"

RUN apt-get update
RUN apt-get install -y python3

**Run the following command to create an image from dockerfile**

docker build -t myimage:tag .


## Class Exercise

1. Create DockerHub account, if you don't have already. (hub.docker.com)

2. Pull any image (ubuntu / nginx / alpine / busybox)

3. Create a container (docker run)

4. make some changes inside your container
Hint: Create a file/user etc.

5. Save that container as a new image on your Docker host
docker container commit <container-id> <image-name:tag>

6. Push the image to your docker hub account
Hint: docker image push





## Practice:
    - Generic Commands (legacy)
    - container management commands
    - image management commands
    - network management commands





## References:
https://docs.docker.com/engine/images/architecture.svg
https://docs.docker.com/engine/reference/builder/