

# Where do the logs of docker container get stored 


In linux , Docker container logs are stored in `/var/lib/docker/containers`



# What happens in the backstage when i run the container in the detached mode ?


1. **Docker daemon takes over**

The docker CLI sends your `docker run -d` command to the docker daemon (dockerd) , which is the background service that manages container. 

2. **Image check and Container Creation** 

Docker checks if the specified image exists locally : 
	- if yes it uses that , 
	- if no it pulls it from Docker Hub (or another registry)


3. **Container lifecycle starts**

The container gets a unique ID , Allocates resources (CPU, memory etc. )



