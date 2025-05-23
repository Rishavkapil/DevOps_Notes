

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




## What is the difference between entrypoint and CMD in Docker ?


Both are used to specify **what command should be run when a container is started** .

**Imagine kitchen Scenario**


`EntryPoint` -> the appliance (like a blender)

This is what always runs , like plugging in and turning on the blender . It's fixed. 

`Cmd` -> The ingredients (like fruits)

These are default ingredients for blender , You can change them if you want. 


***What happens when you use them***

**Only CMD**

			FROM ubuntu
			CMD ["echo", "Hello World"]

This means: "By default, run `echo Hello World`"


				docker run myimage
				# Output: Hello World
				
				docker run myimage echo Bye
				# Output: Bye   ← You replaced the CMD

**Only entrypoint**

			FROM ubuntu
			ENTRYPOINT ["echo", "Hi"]


This means: "Always run `echo` and always say `Hi`, unless someone adds more."

				docker run myimage
				# Output: Hi
				
				docker run myimage Bye
				# Output: Hi Bye   ← You **added** to it, didn’t replace it.

**Both entrypoint and cmd**

					FROM ubuntu
					ENTRYPOINT ["echo"]
					CMD ["Hello"]


Means:
- Always run `echo` (ENTRYPOINT = blender)    
- Default word is `Hello` (CMD = fruit)


				docker run myimage
				# Output: Hello   ← echo Hello
				
				docker run myimage Hi
				# Output: Hi      ← echo Hi (you replaced CMD only)



## What happens when you run a docker container ?


**Step 1 : Docker image pull**

when you run : 

	docker run ubuntu


- Docker checks the local image cache to see if ubuntu is available 
- IF NOT  docker contacts the docker registry (DockerHub default) and : 
	- authenticates it , if needed 
	- Downloads the image layers (each image is made up of layered file systems)
	- stores them in `/var/lib/docker/overlay2`


**Step 2 : Container Creation**


Docker uses **UnionFS** to create container from the image by : 

- Creating a read-write layer on top of the read-only image layers
- setting up containerID , metadata , and mounting the root file system.


	Now What is **UNIONFS** ?
		**UNIONFS** is a technology that allows multiple layers of the file system to be combined into a single , unified view. 


**Step 3 : Setting up the namespaces (Isolation)


Docker isolates containers using Linux Namespaces 
