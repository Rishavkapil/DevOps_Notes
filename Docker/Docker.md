
Docker is an open platform for developing , shipping and running applications using **containers.** Containers are light-weighted self sufficient environment that can hold everything needed to run a piece of software.
	A developer defines all the applications and it’s dependencies in a Dockerfile which is then used to build Docker images that defines a Docker container.



Initially there was one server for one application and if someone want to run more applications then he/she has to buy a new server for running that application.

VMware solved this problem with the help of virtual machines. 

Virtual machines solved this problem of one application on one server. But it has some other problems also . 
Virtual machines required their seperate operating system to run. 


Lets understand some other problems after these




## Why Containerisation

suppose i'm a developer and i have created a website and i want feedback from my friend of my website. Then i gave my code to my friend and now when he tried to run my code it shows some errors like "Reactjs not found " , "node not found , mongodb not found ," etc. 


So to solve this we do all this in one container 

what if there was a way to describe your projects configurations in a single file ?
configurations means what db are we using , what dependencies do we need , what versions of dependencies do we need etc. 

That single file is called **Docker file**. 
Formal Definition of Containerisation : 
Containerisation involves self sufficient software packages that perform consistently regardless of the operating system that they run on.
Its basically taking the snapshot of the machine, file system and letting you use and deploy it as a construct. 


###### Hypervisor
Hypervisor is used to create multiple machines on a host operating system and it manages virtual machines. 


###### Registry 
it is a place where you can deploy an image Docker hub is a type registry , AWS has its own registry 