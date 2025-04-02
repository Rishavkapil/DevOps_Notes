

## Problems With Docker 

**Single Host Nature of Docker Container** 

**Auto Healing :**  Without user intervention , your container should start itself. 

**Auto Scaling :** 

 if we have create an instance and have installed docker on it and there is container running on top of that and lets say we have allocated 4gb ram and 4cpu to that instance . But lets assume that all the resources are consumed by the container . so lets say there's a time when the traffic on the container or server increased . so there are two ways to scale up the resources one is **manually**  and other is by **auto scaling** . 

Docker doesn't support auto scaling for that we need kubernetes. 


### Kubernetes solves this problem

By default Kubernetes is a **cluster** and cluster is basically **group of nodes** 

Kubernetes in General is installed in **master-node architecture** 

![[Pasted image 20250402145940.png]]




ok but **why do we need cluster ?**
like in previous problem with docker if there are 100 containers and one container is using all the resources, by creating **cluster** , it will automatically put the second container in other node. 



2.  **Auto Healing Problem** : so kubernetes has something called as **replica sets or replication controller** . By using replica set we can auto scale the resources. Kubernetes basically depends on .yaml files. So we increased the replica sets from 1 to 10. 
	kubernetes also support something as **HPA** (Horizontal pod autoscaler). 

**Horizontal Pod autoscaler** is a kubernetes resource that automatically scales number of pods in scalable resources like deployments and replica sets based on observed metrics. 


Kubernetes has the feature of **auto scaling**  even if the container is going down , the kubernetes will automatically . 
when ever the API server receives a signal that server is going down, it immediately starts a new container. 