
## What is Ingress

**Ingress** in kubernetes is a mechanism used to present services and applications externally from within a cluster , managing external access to services within a cluster , typically for HTTP and HTTPS traffic. 

**Ingress controller** is just a **load balancer** . and sometimes it can be a **load balancer + API gateway**.



## Why ingress has to be created 


There were two major problems without ingress controller : 

1. **Enterprise and TLS Load Balancing** : 
	1. It was missing sticky sessions
	2. It was missing TLS based load balancing(ie secure load balancing like HTTPS)
	3. It was missing path based load balancing
	4. It was missing host based load balancing
	5. It was missing ratio based Load balancing (where traffic is distributed among servers based on a predefined ratio)
		etc. 


2. **Load Balancers**: 
		If you are using Load balancers as a service then cloud provider will charge you for each of the service(if you use 1000 services , cloud provider will charge you for all 1000 of them). 



#### Interview question :

**Q.  what is the difference between Load balancer type service and kubernets ingress ?**


