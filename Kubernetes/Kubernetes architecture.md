

**There are tow types of mnodes on which kubernetes operates on :** 

1. **Master Node** 
2. **Worker Node**


### Worker Nodes


![[Pasted image 20250403102543.png]]

* Each node has multiple pods on it
* 3 Processes must be installed on every node
* Worker nodes do the actual work
* Every Worker node has container running on it either one or many it depends. 
##### Kubelet
**Kubelet is responsible for ensuring that the pods assigned to a node are running and healthy .** 


**Kubelet communicates** with the kubernetes **API server** to receive instructions for running and monitoring containers and report the node's status back to the control plane. 

It ensures that pods are created created , started and stopped according to the specifications defined by the control plane. 

- it schedules all the process or containers in the Node. 
- kubelet interact with both container and node. 
- kubelet starts a node with a container inside. 
- kubelet also assigns resources like cpu, ram etc.  from node to the container . 


Usually kubernetes cluster is made up of multiple nodes, with each node having **container runtime  and kublet services**  installed on it. 

and these both runs other pods and containers and replicas of the existing pods. 

The way in which communication works in these is via **Services**. 

**Services** are like the load balancers that catches the requests directed to the pods like database for example and forwards it to respective pods. 
and the third process that is responsible for forwarding requests from services to pods is **kubeproxy** . 

**Kubeproxy**  forwards the requests from services to pods in the node. 

![[Pasted image 20250403110657.png]]



For example, if my-app wants to access the database , the request goes to services and instead of forwarding request to any replica , it will forward the request to the replica which is running on the same pod. 

**Replica Sets :** Replica set is the Group of multiple instances of the same pod ensuring that specified number of replicas are running all the times. It maintains the desired state of set of identical pods, 

For kubernetes Worker node to function properly, it must be installed with 3 processes : 

* kubelet
* kubeproxy
* Container runtime




## Component of Worker Node  and How they work

### Kubelet : 
- It is an agent running on each worker node. 
- Kubelet interacts with the **API server** (component of master node) and ensures that pods assigned to each node are running as expected. 
- It communicates with the Container runtime to start and stop the Container
- It reports the health checks of the node 
### Container Runtime : 
Responsible for pulling Container images , starting container and managing container lifecycles . 

### Kube proxy

- It is responsible for networking inside the container. 
- It enables Service discovery and load balancing by forwarding requests to appropriate pods. 

### cAdvisor(Container Advisor)

- cAdvisor collects resource usage stats (like cpu, ram etc. ) of running containers. 
- It helps in monitoring and performance analysis



# How does Worker Node Executes workloads. 


## Step 1 : Receiving a Workload

* The **Scheduler** in the Master node **assigns pod to the Worker node**. 
* **The API Server sends instructions** to the **kubelet** on that Node . 

## Step 2 : Pulling the Container Image 

The kubelet requests the Container runtime to pull the required Container image from registry (such as DockerHub, AWS ECR  or a private registry ).

## Step 3 : Creating and Running the Container

The container runtime starts the container inside the pod 

## Step 4 : Maintaining desired State 

The kubelet continuously monitors the pod and it runs as per the specification defined in the pod YAML file. 
If pod crashes , the kubelet will restart it . 

## Step 4: Handling Networking 

kube-proxy sets up the routing rules to ensure the pod can communicate with the other pods and services. 

If a pod is exposed via kubernetes service , kube-proxy ensures that traffic reaches the correct pod like if any application or container wants to access a database, then kube-proxy will forward request to the one which is running on same pod . 


## Step 5 : Monitoring and Reporting 

The worker node continuously sends the status updates(CPU , memory usage, pod health ) to the control plane. 



# Pod Creation Process

## Step 1 : User or controller requests a pod

* A pod is created when user manually applies a pod or deployment YAML file 
* A controller (like a Deployment , ReplicaSet ) manages and creates pods automatically. 


## Step 2 : API server receives the request

The kubernetes API server receives the request and stores pods definition in ETCD . 

## Step 3 : Scheduler assigns a node

The kubernetes scheduler picks a suitable worker node based on : 
*  Resources availability 
* Node selectors and **affinity rules** (defines on which node should pod run)
* **Taints and toleration** (taints prevents pods running on a node unless they have a matching toleration )

## Step 4 : Kubelet creates a pod 

The kubelet running on the assigned worker node receives instructions from the API server . 
It asks the container runtime (like docker) to : 
		1.  Pull the required image from a container registry 
		2. Create the container inside the pod 
		3. Start the pod. 

## Step 5 :  Kube-proxy Configures Networking 

The kube-proxy ensures the pod is discoverable and can communicate with other pods and services. 

## How do you interact with this cluster ?

**How to**  : 
* Schedule a pod
* if replica pod dies what process will monitor it ?
* and then re-schedule or re-start the pod
* when we add a new server how does it join the node 

**All these managing processes are done by ==Master Node==** 




# Master Node


There are 4 process that run on every master node that controls the cluster and every worker node : 

![[Pasted image 20250403125421.png]]


So when you as a user want to deploy a application in a kubernetes cluster , you interact with the api server using some client (can be UI, kubernetes dashboard , cli like kubelet ) 
### API Server (kube-apiserver)

==Act as an entry point for all kubernetes operation.== 

==When the request comes to api server , it first validates the request and then forwards it to other components== 
so **API server is like the cluster Gateway** which gets the initial requests of any updates into the cluster or even the queries from the cluster and it also act as a gatekeeper for authentication 
![[Pasted image 20250403125815.png]]


for example : when you run 

		kubectl apply -f my-deployment-file.yaml

The api server receives this request , checks if this is valid and sends it to etcd and other componentes. 

### Scheduler 

==Assigns pods to worker nodes based on resource availability and scheduling rules.== 

if user send request to API Server to schedule a new pod , the API server will first validate the request  and then send it to scheduler and then scheduler will the start the application pod on one of the worker nodes. 


**It does not runs the pod itself, but decides where they should run** 

Uses Scheduling Constraints like : 

- **Node Affinity** (Run on a specific node)
- **Pod Affinity** (run close to or away from other pods)
- **Taints and Tolerations** (Restricts pod to a specific nodes). 

### Controller Manager(kube-controller-manager)


==Runs multiple container processes to manage the cluster state .== 

It detects state changes like crashes of pods . so when pods die Controller manager detects that and tries to recover as soon as possible . for that it makes request to scheduler and to re schedule the pods 

##### **Important Controllers :** 

**Replication Controller / ReplicaSet Controller :** Ensures the correct no. of Pod replicas are running . 

**Node Controller :**  Monitors the health of Worker nodes, remove them if they fail . 

**Job Controller :** Manages batch jobs and ensures that they complete. 

**Endpoint Controller :** Manages networking by keeping track of pod IPs. 

### ETCD

- It is a key-value store of a cluster state. 
- Cluster changes are stored in key value store 


![[Pasted image 20250403145723.png]]







# How the master Node works


### Step 1 : User requests a pod or (or Deployment )

A user runs : 

			kubectl apply -f my-app.yml

This request is sent to the API server . 


### Step 2 : API server validates and store the request.

The API server checks if the request is valid or not . 
Then it stores the new pod definition in the etcd .


### Step 3 : Scheduler assigns a node 

The scheduler checks the available worker nodes 
It selects the best node based on CPU , RAM , and affinity rules. 
Assigns the pod to that node. 

### Step 4 : kubelet runs the pod

The kubelet on the selected node receives the instructions. 

It asks the container runtime to pull the image and start the container. 

### Step 5 : Kuber-proxy configures networking 

kube-proxy ensures the pod can communicate with other pods and services. 


### Step 6 : Controller monitors and Maintain the Pod 

If a pod crashes , the replication Controller automatically replaces it . ``