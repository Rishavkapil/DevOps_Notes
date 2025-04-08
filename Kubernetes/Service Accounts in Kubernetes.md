
# What are Service Accounts ?


A Service Account in Kubernetes is a identity that pods use to interact with the kubernetes API. 

Unlike human users (who use regular user accounts ) , **Service accounts are for applications, pods and controllers** that need to talk to the kubernetes cluster .



## why do we need service accounts ?


Let's say you have a pod that : 

* wants to list other pods
* Reads secrets
* Updates config maps
* Talks to the API server. 
	It needs identity and permission to do those things . That's where service accounts comes in. 


This identity is useful in various situations including authentication to the api server 
Service Accounts exists as ServiceAccount Objects in the API server. 

Service account has following properties : 

* **namespaced :** Each service account is bound to a kubernetes namespace. Every namespace gets default Service Account on creation. 



In simple terms , when we apply a deployment file and we have defined the amount of resources that deployment can get ,We attach the service account with that deployment. 


