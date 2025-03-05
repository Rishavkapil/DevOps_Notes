*  **Elastic container service**
* Launch Docker containers on AWS
* You must provision and maintain the infrastructure(the EC2 instance)
* AWS takes care of starting / stopping Containers
* Has integrations with Application Load balancers. 



![[Pasted image 20250225155342.png]]



### Fargate 

* Launch docker containers on AWS .
* You do not provision the infrastructure (no instances to manage)
* AWS just runs the containers based on the CPU / RAM you need. 



### ECR (Elastic Container Registry)

Private Docker registry on AWS.
This is where you store docker images so that they can be run by ECS or Fargate. 




### ECS Terms

*  **Cluster:**  Group of tasks and services , hosts all the resources and infrastructure.
* **Service :** Handles scalability and load balancing of container. 
* **Task :**  Represent the running container of your AWS 