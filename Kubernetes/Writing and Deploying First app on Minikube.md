

## Prerequisites 

 * Docker should be installed 
 * MiniKube should be installed 

## Step 1 : Should have file that you want to run on browser and should have docker file of that also

## Step 2 : Building Docker image



# Deploying app on minikube 

### Step 1 : Copying local docker image into minikube image 

The image we build previously was in local docker image. To use it in the minikube we have to load the image to minikube image list using the following command : 

		$ minikube image load hello-world-php

The above command might take some time to finish , once done run the following command to check the image : 

		$ minikube image ls

You should find the list shown and having your image


### Step 2 : Creating Deployment

A deployment is a resemble to a project or application. Because our image is local , to create the development we have to edit a bit of yaml file . But don't worry we don't have to create the yaml file  manually , rather we will have the kubectl create for us . Type the following command to generate the deployment yaml script to the current working directory. 


		$ kubectl create deployment hello-world-php --image=hello-world-php --dry-run=client -o yaml > deploy-hello-world-php.yaml


==*kubectl create deployment hello-world-php*== 
this tells kubernetes to create a deployment named hello-world-php

==--image=hello-world-php==  

This specify the container image that the deployment should use. 
==hello-world-php== is the image name , which should be available in container registry(like dockerHub ) or locally . 


==--dry-run=client==
 This means that the client won't actually create the deployment in the cluster. Instead, it will stimulate the command and generate the expected output . 


==-o yaml== 

This outputs the generated deployment configuration in YAML format instead of applying it directly.


> ==deploy-hello-world-php.yaml==

This redirects the output (YAML configuration) to a file named `deploy-hello-world-php.yaml`.




Open the generated yaml file using vim or any text editor and then find the container : -image  and add line` imagePullPolicy : Never` after image `name ` . See the following example : 



			apiVersion: apps/v1  
			kind: Deployment  
			metadata:  
				creationTimestamp: null  
				labels:  
					app: hello-world-php  
				name: hello-world-php  
			spec:  
				replicas: 1  
				selector:  
					matchLabels:  
						app: hello-world-php  
				strategy: {}  
				template:  
					metadata:  
						creationTimestamp: null  
						labels:  
							app: hello-world-php  
					spec:  
						containers:  
						- image: hello-world-php  
						name: hello-world-php  
						imagePullPolicy: Never # this is addition  
						resources: {}  
			status: {}



The` imagePullPolicy : Never ` is a trick to tell the kubernetes to use local image only and not trying to pull online image from DockerHub. Once finished, save the file . 

Now to create the deployment run the following command : 

		$ kubectl apply -f deploy-hello-world-php.yaml


Verify the deployment using the following command : 


		$ kubectl get deployments



The deployment automatically created one pod , check using the following command : 

			$ kubectl get pods


A pod can mean a single container or a simple virtual machine which runs the application . We can not see what the application output looks like yet , because the pod is running internally inside the kubernetes cluster and has not been "exposed " to the host machine . Now to expose it we will have to create a "service" . The following step is how to expose application as a service. 


### Step 3 : Exposing application / Creating service


Use the following command to expose the application/create service 


	$ kubectl expose deployment/hello-world-php --type="NodePort" --port 80


**Explanation of the above command :** 
	==kubectl expose deployment/hello-world-php :==  This creates a service in kubernetes that exposes the hello-world-php deployment. 


==--type="NodePort"== : this specifies the type of kubernetes service. NodePort exposes the service on port that can be accessed from the outside of the cluster. 

==--port 80== This defines the port on which the service will receive traffic inside the cluster. 
Your application should be listening to port 80 inside the container. 





To check the service , run the following command : 

		$ kubeclt get services 

you should see something like this 

![[Pasted image 20250401183038.png]]


