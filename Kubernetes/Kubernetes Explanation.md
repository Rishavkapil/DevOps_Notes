	
Kubernetes is a container orchestration tool 

Why it is needed when we already have docker ?

	self healing , autoscaling , management. 


first , we create pod using ==pod.yml== file 

Now the problem with this is that we can't create replicas with this pod.yml file

So we need do define ==deployment== file , which create replica sets and then replica set creates pods . 

Now **when we have replicaSet , then why there was a need for deployment?**

Because deployment is an advanced version of replicaSets, In replicaSets we can't roll back to previous versions, whereas in deployment we can rollback to previous versions as well .This was the main reason. 

**why do we need services** 

If we have two applications running one for backend and one for frontend . 

Frontend app is forwarding request to Backend using its IP. 

Now everytime the backend app restarts , its IP changes ,
So this is the major problem , it becomes very complicated to change the IP of one service again and again . 

So to solve this issue , we have services. 

In these services , we provide label to Ip's of applications. 


We have two nodes , **Master Node** and **Worker Node** 

**Types of Services :** 

**cluster IP :** can access only within the node
**NodePort :** can access only within EKS or minikube
**ALB :** Can access outside the EKS or minikube (i.e via internet )



But still there is problem with ALB , ALB doesn't provide much configurations (like reverse proxy etc. ) for that we need NGINX or other web servers. 

So kubernetes brings up with Ingress , Ingress is just a file that tells which ingress controller to use like 

in ingress file we have defined .nginx or .alb 








