

![[Pasted image 20250403182816.png]]



this is my deployment file of the disaster relief app


##### **Explanation of this deployment file** 

This deployment file consist of two parts : 

1. Deployment(frontend)
2. Service(frontend-service)


## Deployment 

A deployment ensures that the desired number of pods are running in this cluster. 

		apiVersion: apps/v1
		kind: Deployment
		metadata:
			  name: frontend


*  apiVersion : apps/v1 ->Specifies the kubernetes api version for deployments
* kind : Deployment  -> Declares that this is a deployment source.
* metadata : -> Contains information about the deploymetn 
	* name : frontend -> The name of the deployment 


## Replica settings 

				spec:
					  replicas: 1

* replica : 1 -> this ensures that only one pod runs. 
* If the pod crashes , kubernetes will restart it . 


## Pod Selection

				  selector:
				    matchLabels:
					      app: frontend

* Selector -> helps kubernetes to find pods managed by this deployment 
* app : frontend -> It looks for pod with app : frontend

## Pod Template 


	  template:
	    metadata:
	      labels:
	        app: frontend


The template section defines the blueprint for the pods. 
Every pod created will have label app : frontend 


## Container Specification 


    spec:
      containers:
        - name: frontend
          image: lets-go:latest



* containers -> defines the container inside the pod
* name : frontend -> container's name inside the pod 
* image : lets-go:latest -> The docker image to use 


## Image Pull Policy 

          imagePullPolicy: Never
* Never means kubernetes won't pull image from DockerHub. 
* its usefull if you are using local Docker image. 


## Port exposed by the Container 

          ports:
            - containerPort: 80


* containerPort : 80 -> The container inside the pod listens on port 80 






## Service (Front-end service)


A service allows other users' to access the frontend. 

		apiVersion: v1
		kind: Service
		metadata:
		  name: frontend-service



* apiVersion : v1 -> Kubernetes API Version for services. 
* kind : services -> Defines this as a service resource. 
* metadata -> Containes the name of the service. 



## Pod Selection 

			spec:
			  selector:
			    app: frontend



This service targets pods labelled as app: frontend (from the deployment )


## Port Mapping 

			  ports:
			    - protocol: TCP
			      port: 80
			      targetPort: 80



*  port : 80 -> The port exposed by the service
* targetPort : 80 -> Port of the Container


## Service type 

		  type: NodePort


* NodePort -> Exposes the service externally on a port in the range of 30000-32767
* 

