	
Kubernetes is an open source platform designed to automate deploying, scaling and operating application containers . 

It simplifies the developers tasks of managing containerized applications . 


#### Challenges of Containerized applications

Managing Containerized applications, whether using Docker Containers or some other containers runtime , comes with own set of challenges , such as : 

* **Scalability :** As the number of containers grow , it becomes challenging to scale them effectively 
* **Complexity :** Managing numerous containers , each with its own role in a layer application 


### Kubernetes as a solution 

Now that we have all gone through the challenges of using Containerized applications, let's see how kubernetes handles these challenges .

* Kubernetes step in as a powerful tool to manage these complexities. Its an open source system designed for automating deployment, scaling and operation of application .
* It simplifies container management, allowing applications to run efficiently and consistently . 



### Core Components of Kubernetes

1. **Pods :** The smallest deployable units created and managed by kubernetes . A pod represent a single instance of running process in your cluster and can contain one or more container. 

2. **Nodes:**  Nodes are the worker machine in the kubernetes , which can be either a physical or virtual machine , depending on the cluster. Each node runs pods and is managed by the master. 


3. **Deployments :** They describe the desired state of your application , like which images to use and the number of pod replicas  . Deployments update your application to the desired state at a controlled rate. 


4. **Services :** They are an abstract way to expose an application running on a set of pods as a network service. 

5. **Ingress :** This manages the external access to the services in a cluster, typically HTTP. Ingress can provide load balancing , SSL termination and name-based virtual hosting . 


6. **Namespaces :** Namespaces help split a kubernetes cluster into a sub-cluster, making it possible to divide resources between different projects or teams. 


7. **Labels and Selectors :** They are powerful tools that allow you to organize and select subsets of objects , like pods , based on key-value pairs for more precise resource management. 
![[Pasted image 20250331124141.png]]





### How does kubernetes achieve high availability 

* **Control Plane Components :** The control plane's components , including the kube-apiserver , etcd, kube-scheduler and kube-controller manager work together to manage the cluster state. Ensuring high availability of control plane is crucial for production envionments. 


* **Self Healing mechanisms :** Kubernets constantly checks the health of nodes and containers, restarting those that fail , replacing them and killing those that don't respond to user-defined health checks . 


* Kubernetes doesn't replace docker but complements it by handling the orchestration of containers created by docker. 

* It addresses the challenge of running and connecting containers across multiple hosts, managing the complexity of high availability , and service discovery. 

* Kubernetes is designed to respond to the dynamic nature of modern cloud environments, scaling up or down as needed and rolling out updates without downtime. 



**Like if we are using ==PhonePe== and the organization has updated the UI , it will not affect the user experience because the previous version will stay until the session is not being restored**


