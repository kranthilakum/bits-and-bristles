---
title: "A Reference Guide to Docker"
date: 2021-02-10T09:55:46+05:30
draft: false
categories:
- "docker"
tags:
- "docker"
- "container"
- "containerization"
- "virtualization"
- "linux"
---

Docker is a set of platform-as-a-service products that use OS-level virtualization to deliver software in packages called containers.

Containers are isolated from one another and bundle their own software, libraries and configuration files; they can communicate with each other through well-defined channels.

**shows client and server version**

`$ docker version`

**pulling new image from registry** - library/hello-world

```
$ docker pull hello-world:latest
$ docker pull alpine:3.4
$ docker pull debian:latest
```

**re-tag a local image with a new image name and tag**

```
# create a tagged target image from source image
$ docker tag SOURCE_IMAGE NAMESPACE/TARGET_IMAGE:TAG
$ docker tag alpine:3.4 krakum/alpine:3.4.1
```

NAMESPACE : Docker registry account name IMAGE: Image name or Image ID TAG: Version label or tag

**push your tagged image to Docker registry**

`$ docker push krakum/alpine:3.4.1`

**pull your tagged image from Docker registry**

`$ docker run krakum/alphine:3.4.1` downloads image, creates a container and starts it show all images stored locally

`$ docker images` show all containers

`$ docker ps -a` list the running containers

`$ docker network ls` run container and echo output

`$ docker run debian echo "hello world"` run container and echo output to file

```
$ docker run debian echo "hello world"
$ hello world.txt`
```

ping localhost (127.0.0.1) `$ docker run debian ping localhost -c 10`

**Inspect an image or container**

`$ docker inspect IMAGE/CONTAINER` view history of an image or container

`$ docker history IMAGE/CONTAINER` start a container

`$ docker start CONTAINER` stop a container

`$ docker stop CONTAINER` Stop the container before attempting removal or use. You cannot remove a running container.

Stop a running container through SIGKILL `$ docker kill CONTAINER`

### Remove one or more containers or images

`$ docker rm CONTAINER-1 CONTAINER-2 CONTAINER-3` delete all running and stopped containers

`$ docker rm -f $(docker ps -aq)` remove one or more images

`$ docker rmi IMAGE`

### Run nginx image in a container

`$ docker run nginx` Unable to find image 'nginx:latest' locally. latest: Pulling from library/nginx. Status: Downloaded newer image for nginx:latest browse to localhost:8085 and see a message

`$ docker run -d -p 8085:80 nginx` local port 8085 is mapped to container port 80. -d option runs container in background and print container ID -p option publishes a container's port(s) to the host

### Run a container

`docker run --rm -it ---name -p 8080:80 -v ~/dev:code alpine:3.4 /bin/sh` --rm : remove container automatically after it exits -it : connect the container to terminal --name NAME : name the container -p 8080:80 : expose port 8080 externally and map to port 80 -v ~/dev:/code : create a host mapped volume inside the container alpine:3.4 : the image from which the container is instantiated /bin/sh : the command to run inside the container

### Run a container as background process

`$ docker run debian` run a container and enter an interactive terminal

`$ docker run -it debian bash` run a container named debian_container with debain image

`$ docker run --name debian_container --rm -i -t debian bash` --rm option automatically removes the container when the terminal exits -t option allocates a pseudo-TTY -i option keeps STDIN open

Runs debian image in a container named debian_container and opens an interactive bash shell

`$ docker run --name debian_container -it debian`

runs a named container as background process

`$ docker run --name debain_container debian` execute an interactive bash shell on the container

`$ docker exec -it debian_container bash` run cassandra container

`$ docker run --name some-cassandra -d cassandra:tag` tag is a specific Cassandra version e.g. 2.1, 2.2, 3, latest

### Log information by a running container

`$ docker logs` print the last 100 lines of a container's logs

`$ docker logs ---tail 100 CONTAINER` It shows the command's STDOUT and STDERR Logging Drivers Logging Drivers get you information from running containers and services. Each Docker daemon has a default Logging Driver (json-file). Other logging drivers include syslog, journald, gelf, fluentd, awslogs, splunk, etwlogs, etc.

### Find current default logging driver for Docker daemon

`$ docker info | grep 'Logging Driver'` find current logging driver for a running container

```
$ docker inspect CONTAINER | grep 'LogConfig'
$ docker inspect -f '{{.HostConfig.LogConfig.Type}}' CONTAINER
```

configure a container to use a different logging driver than the default

```
$ docker run\
 --log-driver=syslog
 --log-opt syslog-address=tcp://192.168.0.42:123\
   --log-opt syslog-facility=daemon\
 debian
```

sends the container's logging output to a syslog remote server

### Get a live stream of container's runtime metrics

`docker stats` Login to a Docker Registry (e.g. DockerHub, Artifactory, etc.)

`$ docker login REGISTRY_ADDRESS:PORT` Docker Orchestration list the nodes participating in a swarm

`$ docker node ls` list the services running in a swarm

`$ docker service ls` list the tasks of a service

`$ docker service ps CONTAINER`

### Terminology

-   **Base image** is an image that has no parent.
-   **UNIX and Linux commands** typically open three I/O streams when they run, called STDIN, STDOUT, and STDERR. STDIN is the commmand's input stream, which may include input from the keyboard or input from another command. STDOUT is usually a command's normal output, and STDERR is typically used to output error messages.
-   **Copy-on-write strategy (COW)**, also referred to as implicit sharing or shadowing is a resource-management technique used in computer programming to efficiently implement a duplicate or copy operation on modifiable resources. Its main use in sharing the virtual memory of operating system processes, in the implementation of the fork system call.
-   **Unification of filesystems** is the concept of mounting several filesystems on a single mount point with the resulting mount showing the logical combination of all the filesystems.
-   **Union file system** implement a union mount and operate by creating layers.
-   **Image** contains a union of layered filesystems stacked on top of each other. It contains layers of filesystems typically predicated on a base image under a writable layer, and built up with layers of differences from the base image.
-   **Container** is a runtime instance of an image. It consists of image execution environment. Multiple containers can share access to the same image and make container specific changes on a writable layer which is deleted when the container is removed.

### Links

-   [Docker](https://www.docker.com/)
-   [Docker Registrator](https://github.com/gliderlabs/registrator)
-   [Artifactory: a private Docker registry](https://www.jfrog.com/artifactory/)
-   [Docker Hub](https://hub.docker.com/)
-   [Marathon](https://mesosphere.github.io/marathon)
-   [Mesos: Distributed system kernel](http://mesos.apache.org/)
-   [ZooKeeper: leader election for Marathon](https://zookeeper.apache.org/)
-   [Consul: configuration and service discovery](https://www.consul.io/)
-   Elasticsearch, Logstash & Kibana (ELK)
-   [Advanced Bash Scripting by Mendel Cooper](http://www.tldp.org/LDP/abs/html/)
-   [Control Groups (cgroups): a Linux Kernel feature](https://www.kernel.org/doc/Documentation/cgroup-v1/cgroups.txt)

-   [Github](https://www.github.com/kranthilakum)
-   [Linkedin](https://www.linkedin.com/in/kranthilakum/)
-   [StackOverflow](https://stackoverflow.com/users/1509209/kranthi-lakum)
-   [Twitter](https://twitter.com/krantlak)
-   [Facebook](https://www.facebook.com/kranthilakum)
-   [Instagram](https://www.instagram.com/krantlak)
-   [Pinterest](https://pinterest.com/kranthilakum)
-   [Flickr](https://www.flickr.com/photos/prince-apple/)