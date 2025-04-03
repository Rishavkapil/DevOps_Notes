

## Step 1 : User Requests a deployment 

You write a kubernetes deployment yaml file to define how your app deployment should run.


## Step 2 : Apply the Deployment 

Run the following command to apply the deployment : 

	kubectl apply -f <deployment_file_name.yaml>

- This request is sent to the API server (kube-apiserver)
- The api server validates the request and stores the deployment details in etcd. 



## Step 3 : Scheduler selects the node for pods

The scheduler picks worker nodes to run the replicas of pods. 

## Step 4 : Kubelet creates the pods on worker nodes

kubelet asks the container runtime to pull the container image and Container runtime starts the container. 

Now the pod is in the running state. 

**Check the pod status**

			kubectl get pods 

This request also goes to the API server first and then it will validate the request and then it will fetch the pods from the etcd store. 




## Step 5 :  Kube-proxy configures networking


- kube-proxy sets up networking so that pods can communicate. 
- Each pod gets an internal IP (but it's not yet accessible externally)



## Step 6 : Exposing the application 

To access the application from outside, we need to expose it as a **service**. 
create a service file like **node-app-service.yml**


Apply the Service. 

			kubectl apply -f node-app-service.yml

Now users can access the application via a public IP . 


## Step 7 : Controller Monitors and maintain the pods 

If a pod crashes , the replica set controller automatically creates a new one . 

If a node fails , the scheduler assigns a new node for the pod. 