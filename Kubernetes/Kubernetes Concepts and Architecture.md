
Generally , Kubernetes has two different nodes running the application. 



![[Pasted image 20250331155540.png]]

1. **Master Node :** The master node is responsible for managing the complete cluster. 
	It has four components : **ETDC  , API Server , Scheduler  , and Controller manager.**

	* Users can access the master using the CLI through the API server. 
	* The master node monitors all nodes in the cluster and take action accrodingly. 
	* Kubernetes can have more than one master node for high availability .


**API Server :** 
The master can communicate with all the clusters through API server. It is the main access point to the control plane. 

* The **API Server** directly interacts with the user. Ex-users are directly able to apply YML or JSON files directly to the API server through CLI . 
* API server has capability to auto scale as per load. 
* The API server is the frontend of the control plane. 


**ETCD :**

ETCD  is used to store data as key-value pairs , which are used by Kubernetes to manage the clusters. 
It also stores the metadata and status of the cluster. 

It is also responsible for maintaining the **lock mechanism** to reduce conflicts between masters. 

**Lock mechanism :** It is used to ensure that only one replica of an application can execute a critical section of code or a scheduled task at any given time , preventing duplicate work and potential inconsistencies. 

When there are multiple masters and nodes , ETCD stores all the data in the distributed manner . 


**Scheduler :**  

The scheduler is responsible for distributing the work across multiple different available nodes. 

It always looks at the newly created containers and assigns the node . 

handles pod creation and management. 

When the user makes request for the creation and management of pods , the scheduler will take action on that request smoothly . 


**Control Manager :** 

Controllers are the main thing behind orchestration . 

Controllers continuously look at and watch the health of node , whether it is responding or not , and take action according to it. 

	Following are the Components present in the Control manager : 


* *Route Controller :* Responsible for managing the networking.
* *Node Controller :*  Responsible for detecting the node if it is not responding. 
* *Service Controller :* Responsible for load balancing to manage the load. 
* *Volume Controller :* Responsible for mounting and creating volume storage. 


**Worker Node  :**


* **Kubelet :** 
	Kubernetes worker node has kubelet to communicate with the master node and provide all the information continuously to the master node related to the health of the Nodes. 
	It is also responsible for carrying out actions taken by the master node. 

	listens to the kubernetes master 

	It also sends access reports for the node to the master. 

* **Kube Proxy :** 
	Kube proxy is responsible for managing the network traffic properly as per the rule defined in the controller manager. 

	**It also assigns IP to each Pod .** 

	kube-proxy runs on each node and has the ability to check that a unique IP address is assigned to each pod. 


* **Pods :** 
	It runs as the single instance of the application . 
	It may have many resources like IP addresses, containers and storage . 
	Pods have one or more containers that are deployed on the same host. 

	In Kubernetes, the control unit is pod not the container. 

	Pods run on the worker node which is controlled by the master. 



* **Container Engine :** 
	The container engine is responsible for running containerized applications . 




#### High Level Kubernetes Objects

1. **Replica Set :** A replica sets contains a group of instances and a number of identical running pods.
(Replica sets ensure that specified number of pod replicas are running at a given time.)

2. **Deployment :** Deployment maintains the desired state and versioning . 

3. **Volume :** Kubernetes provide stable storage services in the form of volumes that persist data for the whole lifetime of the pod. 

4. **Service :** Inside the Pods , multiple pods are in running mode under the selector , so in that case , the Service manages DNS addresses for them. 






