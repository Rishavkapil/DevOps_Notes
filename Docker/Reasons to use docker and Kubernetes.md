
1. Node node found error 


2. if there are two Processes and both are given equal number of resources, and if one process requires less resources and other requires more, then there is resource wastage. Docker solves this problem by containerizing the processes, only giving the required number of resources to the processes to reduce the resource wastage.


3. Instead of running different services on different servers, we can run multiple services on same server using the containers. 



Now why to use kubernetes 



Suppose i want to run container , i can easily run that using `docker run <container_name>`


Now suppose i want to run 1000 containers , i will not be running this command 1000 times., OK Lets say you created 1000 containers by running the command 1000 times, Now what if i only need 400 Containers and rest 600 containers are useless, so now should i sit and delete them  all or stop them all ?

Kubernetes can do this easiy. 

and suppose one Container cna handle only 50 requests and there are only 4 containers available , kubernetes can automatically scale up the containers.


i.e **Kubernetes can handle auto scalling .**






