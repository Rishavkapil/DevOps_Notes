

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
		Accessible externally using <NodeIP>:<NodePort> but within the EKS or minikube only not on internet . 

3.    Load Balancer : 

		Works with a cloud provider to create an external load balancer. 
		Exposes the service to internet via public IP. 


4. External Name 
		Maps a service to a DNS name . 



YML file for cluster IP type : 

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



