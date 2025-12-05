
In kubernetes , services are an abstraction that define a stable way to access group of pods. 

##### What service does 

Select pods  using labels 
Exposes those pods to other parts of your cluster 
provides a stable DNS name or IP address for those pods. 

## Types of services in Kubernetes 

1. ==Cluster IP== (Default):
		Exposes the service on an internal IP in cluster. 
		Only accessible within the cluster. 


2. ==NodePort== : 
		Exposes service on each Node's IP at a static Port 
		Accessible externally using ==NodeIP:NodePort== but within the EKS or minikube only not on internet . 

3. ==Load Balancer== : 
		Works with cloud provider to create an external load balancer .
		exposes the service to the internet with a public IP. 



4. ==ExternalName== : 
		Maps a service to a DNS Name. 



**Yml file for all the types :** 

## Cluster IP : 

		apiVersion: v1
		kind: Service
		metadata:
		  name: clusterip-service
		spec:
		  selector:
		    app: my-app             # Selects Pods with label app=my-app
		  ports:
		    - protocol: TCP         # Protocol type
		      port: 80              # Port exposed by the service (inside cluster)
		      targetPort: 8080      # Pod's port to forward traffic to




**Explanation :** 

* apiversion : version of the Kubernetes API 
* Kind : Type of resource , here its a service . 
* metadata.name : Name of the service. 
* spec.selector : matches pod with app:my-app
* spec.ports.port : Port that this service exposes.
* spec.ports.targets.port : Actual port inside the pod the traffic will go to . 
* ClusterIP is default : this service is accessible only within the cluster. 




## NodePort : 

		apiVersion: v1
		kind: Service
		metadata:
		  name: nodeport-service
		spec:
		  type: NodePort
		  selector:
		    app: my-app
		  ports:
		    - protocol: TCP
		      port: 80             # Service port
		      targetPort: 8080     # Pod port
		      nodePort: 30007      # Exposed port on all nodes (range 30000-32767)




**Explanation :** 

**type : NodePort ->** Exposes the service on each pod's IP . 
**nodePort:** The actual port exposed on Node's IP. 




## LoadBalancer 

		apiVersion: v1
		kind: Service
		metadata:
		  name: loadbalancer-service
		spec:
		  type: LoadBalancer
		  selector:
		    app: my-app
		  ports:
		    - protocol: TCP
		      port: 80
		      targetPort: 8080
		


**Explanation :** 

**type:loadBalancer ->**  Cloud provider assigns an external IP to this service. 

Ideal for production when you want to expose service on the internet. 


## ExternalName 



			apiVersion: v1
			kind: Service
			metadata:
			  name: externalname-service
			spec:
			  type: ExternalName
			  externalName: example.com



**Explanation :** 

This service doesn't point to any pod. 
It just resolves to a DNS name like example.com


