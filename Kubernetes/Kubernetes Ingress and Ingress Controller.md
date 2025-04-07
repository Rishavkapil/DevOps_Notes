
Ingress and Ingress Controller are the key components for managing external access to services in a cluster. 
### What is Kubernetes Ingress


While Pods within the kubernetes cluster can easily communicate between themselves , they are not by default accessible to external networks and traffic. 

A **Kubernetes Ingress** is an API object that shows how traffic from internet should ou reach internal kubernetes cluster Services that send request to group of pods. 

The Ingress itself has no power. 
It is a configuration request for ingress controller that allow users to define how external clients are routed to a cluster's internal service . 


**Kubernetes Objects** are persistent entities in your kubernetes system that represent the state of your cluster. 

Ingress acts like a router or reverse proxy that defines rules for routing traffic based on : 

* Hostnames
* Paths 
* Protocols(HTTP/HTTPS)

You define these rules in an Ingress resource  , which tells kubernetes how to handle incomming requests. 


#### Example Use Case : 

You have two apps running inside your cluster : 
* frontend service : frontend-service
* backend service : api-service

Instead of exposing both separately , you ca define this ingress : 


				apiVersion: networking.k8s.io/v1
				kind: Ingress
				metadata:
				  name: my-ingress
				spec:
				  rules:
				    - host: example.com
				      http:
				        paths:
				          - path: /
				            pathType: Prefix
				            backend:
				              service:
				                name: frontend-service
				                port:
				                  number: 80
				          - path: /api
				            pathType: Prefix
				            backend:
				              service:
				                name: api-service
				                port:
				                  number: 80
				

This means : 
* example.com/ goes to frontend-service
* example.com/api goes to api-service





### What is Ingress Controller ?

**Now , the question is who reads ingress file and apply the routing ?**
That's the job of ingress controller . 

The **Ingress Controller** is an actual software that implement the rules you write in your Ingress resources. 


**Popular Ingress Controller :** NGINX , Traefik , HAProxy, AWS ALB Ingress 



### How it all comes together 


					+-----------------+
					|   Internet      |
					+--------+--------+
					         |
					         v
					+----------------------+
					| Ingress Controller   |  <-- e.g., NGINX, Traefik
					| (LoadBalancer/NodePort)
					+--------+-------------+
					         |
					+--------v------------------+
					| Ingress Rules (YAML)      |
					+---------------------------+
					         |
					         v
					+----------------+     +-----------------+
					| frontend-svc   |     | api-svc         |
					+----------------+     +-----------------+




## Lets see how these work with example



### **Goal : You want to setup where users can access :**

* http://myapp.com -> goes to frontend
* http://myapp.com/api -> goes to backend



## Step 1 : You have services inside your cluster

Lets say you have two apps already running : 

1. **Frontend deployment and service** 

				apiVersion: v1
				kind: Service
				metadata:
				  name: frontend-service
				spec:
				  selector:
				    app: frontend
				  ports:
				    - port: 80
				      targetPort: 3000

you have frontend apps running on port 3000 , and its service exposes it on port 80 

2. **Backend deployment and Service** 

				apiVersion: v1
				kind: Service
				metadata:
				  name: backend-service
				spec:
				  selector:
				    app: backend
				  ports:
				    - port: 80
				      targetPort: 5000


you have backend apps running on port 5000 and its service exposes it on port 80 within the cluster. 

These services are cluster-internal , they can't be accessed from outside the cluster yet. 


## Step 2 : Install an Ingress controller 

You need to install an ingress controller . This is a pod that watches your ingress rules and handles external traffic. 

eg. Installing NGINX Ingress Controller (minikube)

			minikube addons enable ingress
	

