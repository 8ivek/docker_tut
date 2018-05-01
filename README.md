# Docker for beginners
Docker for beginner

# You will learn
Setting up docker environment with separate servers for:
- <a href="https://www.nginx.com" target="_blank">Nginx</a> based server: for running <a href="https://nodejs.org" target="_blank">nodejs</a>
- DB server: for running <a href="https://couchdb.apache.org" target="_blank">couchDB</a>
- Cache server: for running <a href="https://redis.io" target="_blank">Redis</a>

# Docker Concepts

### Image
An __image__ is an executable package that includes everything needed to run an application.
It is basically a Dockerfile.

### Container
A __container__ is a runtime instance of an image what the image becomes in memory when executed.

# Docker cheat sheets
### List Docker CLI commands
docker
docker container --help

### Display Docker version and info
docker --version
docker version
docker info

### List Docker images
docker image ls

### Build Docker image
docker build -t <image-name> .
 using: 
> docker build -t <image-name> .

our example: 
> docker build -t bivek/nodeserver .
> docker build -t bivek/couchdb .

### Execute Docker image
> docker run <image-name>
- mapping your machine’s port 4000 to the container’s published port 80 using -p

example:
> docker run -p <host_port>:<container_port> <image-name>
example for multiple port:
> docker run -p <host_port1>:<container_port1> -p <host_port2>:<container_port2>

our example:
> docker run -p 3000:3001 bivek/nodeserver
> docker run -d -p 5984:5984 -v ~/couchdb:/usr/local/var/lib/couchdb bivek/couchdb
__intentionally doing 5984__

### Get inside bash of docker
> docker exec -it CONTAINER_ID bash

> docker exec -it bivek/couchdb bash

### Running docker composer

> docker-compose up
> docker-compose up --build

### List Docker containers (running, all, all in quiet mode)
- docker container ls
- docker container ls --all
- docker container ls -aq

### Remove all images
> docker system prune -a

