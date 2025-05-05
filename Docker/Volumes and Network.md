

**Why do we need volume ?**

Volumes in docker are used to persist data generated and used by Docker containers. Without volumes, any data inside a container would be lost if container stops.

We want local databases to retain information across restarts thats why we need volumes. 

Docker makes sure that everything runs inside the containerized environment and if you ever bring down the container , all the data inside that container would be lost. 
When ever you restart the system you get a fresh container. 


We want one docker container to talk to another docker container thats why we need networks in docker




So **what is a VOLUME ??**

A volume is a logical space inside a docker where you can put bunch of data.


So now **How to create a volume ?** 

		
		 docker volume create volume_database


BY running the above command we have created a logical space i.e volume in our docker engine. 


**Docker engine :**  Docker engine is a core component of docker platform , it provides runtime environment for containers , allowing users to build , run and manage containerized applications. 


next step is 

		sudo docker run -v volume_database:/data/db -p 27017:27017 mongo


this means run the mongo with volume mapped to /data/db 

/data/db is where mongo dumps its data


whenever you run `docker run mongo` the place where all the data is stored inside that container is /data/db





**`sudo docker exec -it container_id  /bin/bash`**


the above commnd lets you go inside that container



These VOLUMES will retain even if the docker container is down 
and it will only get deleted manually. 


**To remove the volume** 


			docker volume rm volume_database



Every container has its own network . If we do `ping localhost` inside a container it refers to the localhost of container itself not the localhost of system/machine.





![[Pasted image 20250212151317.png]]



if we run localhost or 12.0.0.1 on any machine that means the address of that machine itself 
like if we run localhost inside the container that means the address of that container itself. 


![[Pasted image 20250212151731.png]]





To make this possible to make our container talk to our database locally we need to setup the network between them. 


Now **how to create a network ?**


	 docker network create my_custom_network


creates  a bridge driver

| Bridge driver                                          | Host driver                                         |
| ------------------------------------------------------ | --------------------------------------------------- |
| Provides network isolation between hosts and container | No isolation                                        |
| Containers get their own IP address                    | Containers use host's IP address                    |
| Slightly lower performance due to NAT                  | Higher Performance                                  |
| Default Network for containers unless specified        | Must be explicitly specified using `--network host` |



when we are creating the container 
we do 

	docker run -p 3000:3000 --name backend --network my_custom_network <img_tag>


why would we give **--name backend**  ?

because this is how one container finds the other container if we don't give a name it will be assigned a random ID so it will be very hard to find any particular container





#### Note : After every change in index.js file you need to rebuild the image



	