

#### Docker daemon : 

The docker daemon (dockerd ) is the background service that manages Docker container on a system. 
It is responsible for : 

- Building and running Containers 
- Managing container lifecycle (start, stop, restart etc. )
- Handling images, volumes , networks and more. 
- Interacting with the **Docker CLI** (docker command)


**Example**  

when you run : 

	docker run nginx 

The CLI sends request to docker daemon , which 
- pulls nginx image (if not present )
- Creates a container 
- Starts the Container


#### Docker CLI

- Command line tool used to interact with the docker 
- Sends commands like docker run , docker build to the docker daemon. 

#### Docker Images 

- Read-only templates used to create containers 
- Built using a dockerfile 
- Eg: nginx:latest, python:3.10


#### Docker Containers 

- Running instances of docker images. 
- Lightweight and isolated environments. 
- You can create, start , stop or delete them. 

#### Docker Volumes 

* Used for persistent storage
* Volumes survives container restarts or deletions. 


#### Docker Networks


- Allow containers to communicate with each other . 
- Docker automatically creates bridge network by default but you can create your custom networks. 

- **Bridge Network** : A Bridge network in docker is the default network type for containers on a single host. It allows container to communicate with each other internally using a **Private IP addresses .** 

- when you run a container without specifying a  network , Docker connects it to **default bridge network.** 
- Container on the same bridge network can talk to each other 


#### Docker Compose 

A tool to define and run multi-container docker applications 
Example : a web app with frontend , backend and database. 


#### Registries

- A cloud based image repositories where you can push and pull images.
- DockerHub is the default registry 



