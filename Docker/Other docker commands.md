
#### **Docker container attach** : 


Usage : `docker container attach <Container_id>`


or 

			docker attach <container_id>

Docker attach is used to connect our terminal to docker container. 
The attach command displays the output of containers ENTRYPOINT and CMD process. 



#### Docker Container diff : 



Inspect changes to files or directories on a container's file system. 


			docker diff <container_id> 
			or 
			docker container diff <container_id>


List the changed files and directories in a container file system since the container was created. 



#### Docker Container Export : 



Exports a container file system as a **tar archive** . 


**Tar archive** : A file that contains layers of docker images. Each layer itself is a tar file , and when all these layers are extracted to the same location , they form the filesystem of the container. 