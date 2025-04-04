

# What are Workload resources ?



Workload resources in kubernetes define how applications (pods) should run . These resources are higher-level controllers that manage pods and ensure that they run in the desired state. 


###### **Why are Workload resources needed ?**


* Pod management : Workload automatically create , update and scale pods . 
* Fault Tolerance : If pod fails the workload ensures that new pod is created 
* Scaling : Supports auto scaling to handle traffic spikes. 
* Statefull 



## Stateless applications 

A **Stateless application** does not store any data inside the pod . 
Each request is handled independently and any pod can process any request. 


## Stateful applications


A statefull application stores data and each pod has unique identity. 

- IF a pod dies, new pod must keeps the same data. 
- for this we attach volumes to the pod 


# Deployments (For stateless apps)

A deployment is a container that manages a set of stateless pods .

### Why deployment ?

- Stateless apps like web servers , API's don't need persistent storage . 
- Ensure automatic healing (if pod crashes , new pod is automatically created )

### Example deploying a webpage with 3 replicas 
					
					
					
					apiVersion: apps/v1
					kind: Deployment
					metadata:
					  name: web-deployment
					spec:
					  replicas: 3
					  selector:
					    matchLabels:
					      app: web
					  template:
					    metadata:
					      labels:
					        app: web
					    spec:
					      containers:
					      - name: nginx
					        image: nginx:latest
					        ports:
					        - containerPort: 80


##### **What happens in the background**

- Deployment controller creates a replica
- replica sets ensure that 3 pods are running 
- Scheduler assigns each pod to a node.
- If a pod crashes , replica set replaces it immediately . 
- Service routes traffic to healthy pods 


# StatefulSet (for stateful apps)

A StateFulSet is like a deployment but for stateful applications (e.g Databases). It ensures : 

- Each pod has a unique and stable identity 
- Pods are created sequentially  , not all at once. 
- Persistent storage is maintained across restarts. 

### Example : MongoDB StateFulSet


					apiVersion: apps/v1
					kind: StatefulSet
					metadata:
					  name: mongo
					spec:
					  serviceName: "mongo"
					  replicas: 3
					  selector:
					    matchLabels:
					      app: mongo
					  template:
					    metadata:
					      labels:
					        app: mongo
					    spec:
					      containers:
					      - name: mongo
					        image: mongo
					        ports:
					        - containerPort: 27017
					        volumeMounts:
					        - name: mongo-storage
					          mountPath: /data/db
					  volumeClaimTemplates:
					  - metadata:
					      name: mongo-storage
					    spec:
					      accessModes: ["ReadWriteOnce"]
					      resources:
					        requests:
					          storage: 1Gi


##### **What happens in the background ?**

- StatefulSet controller creates pods (mongo-0, mongo-1 etc. )
- Each pod gets a persistent volume (pv-mongo-0, pv-mongo-1 etc. )
- Pod start in order (like mongo-0 first, mongo-1 second). 
- Service allows communication between database nodes. 


# DaemonSet(Running one pod per node)


#### What is daemonSet ?


- It ensures that one pod runs on every node in the cluster .
- It is mainly used for system level services that must be present on all nodes, such as , logging agents , Monitoring agents , Security tools etc. 


###### **Why use a daemonSet**

* **Ensures every node gets the pod** , Even if the new node joins , kubernetes automatically runs a new instance of the daemonSet pod. 
* **Resource Efficiency :** It avoids unnecessary replicas by ensuring that only one pod per node runs.
* **Node-specific tasks :**  Some workloads run on specific nodes. 
* **Resilient to node failures :** If a node fails , the daemonSet ensures that Pod runs on any newly added Nodes. 



### How daemonSets Work behind the scenes 



####  1. User Creates a DaemonSet 


When a user applies daemonSet YAML , the DaemonSet Controller (part of the kubernetes control plane) takes over. 



#### 2. API Server stores it in etcd

The request is sent to kubernetes API server (kube-apiserver)
Then the details are stored in etcd database. 

#### 3. DaemonSet Controller watches the node


The daemonSet controller continuously monitors Nodes. When the new node is added, the controller schedules the daemonset pod onto that Node. 


#### 4. Kubelet runs the pod on each node


The kubelet on each node receives instructions to run the pod. and the pod is automatically started without needing the scheduler . 


#### 5. Continuous Monitoring 

If a node fails , the kubernetes will reschedule the Daemonset Pod to the new Node when it becomes available . 





# Jobs and Cronjobs (For onetime or Scheduled tasks)

In kubernetes , Jobs and Cronjobs are used to run tasks that execute once or on a schedule. These are different from Deployments or DaemonSets because they do not run continuously. Instead they run a task , complete it and terminate. 



## Jobs : One time task Execution 

A **job** in kubernetes is a workload resource that runs a task until it completes successfully . 

Jobs are useful for : 

Batch Processing , Database migrations , Backup and restore tasks , Machine learning Training jobs etc. 


### How jobs work 

- The user creates a job . 
- The request is sent to the API server. 
- The job controller creates one or more pod . 
- Each pod runs until it completes successfully 
- If the pod fails the kubernetes retries it , based on the restart policy. 
- Once the job reaches the desired completion count , it stops creating new pods . 



#### Controlling job execution 
There are three types of job execution patterns : 

1. **Single Job** (Default behavior) : 
	Runs one pod to completion 


2. Parallel Jobs : 