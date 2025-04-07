

## Kubernetes Controllers. 

A Controller is a **control loop** that continuously watches the state of the kubernetes cluster and attempts to drive the actual state towards the desired state defined by the users in configurations files. 

**Control Loop** : 
A control loop is a programming pattern that continuously monitors a system and takes action to bring the system into desired state if it detects a mismatch . 

Kubernetes uses control loops inside controllers to make sure actual state of the cluster matches the desired state you define in the YML manifests or kubectl. 



#### Key behavior of Controllers : 

*  You define what you want (eg. 3 replicas of running pod)
* The controller checks what's actually running . 
* If the desired state and actual state don't match it takes action to correct it . 


### Why Controllers matter. 

Kubernetes is a self-healing system. Controllers are what give it that power. 

eg. if a pod crashes or a node fails , the deployment controller or replica set controller will create a new pod automatically . 


#### Where do controllers run 

Most of the core controllers run inside the kube-controller-manager , which is the part of the kubernetes control plane. 



## Types of Controllers in Kubernetes 

##### 1. Replication Based Controller : 


* **==ReplicaSet Controller  :==** 
		Ensures that specified number of replica pods are running at anytime. 
		If a pod gets down, it creates a new one . 

* **==Deployment Controller :==** 
		manages replica sets and allows rolling updates , rollbacks and scaling 
		It is the most common controller used in stateless apps  . 

* ==**StatefulSet Controller**== : 
		Similar to deployment for stateFull apps. 
		Provides : 
				Stable network identities 
				persistent storage per pod. 

* ==**DaemonSet Controller :**== 
		Ensures a pod runs on all(or selected) nodes. 
			Use Cases : 
					Monitoring agents 
					Log collectors 
					Network Plugins 



##### 2 .Job Based Controllers 

For batch or scheduled jobs 

*  ==**Job Controller**== : 
		Runs a pod or multiple pods to completion 
		used for onetime tasks like DB migrations or backups 
* ==**CronJob Controller**== : 
		Runs a job on a schedule , like a cron task . 



##### 3. Node and cluster management Controllers. 

==**Node Controller**== : 
		Monitors the health of the nodes. 
		Marks them not ready if they become unresponsive

==**NameSpace Controller**== : 
	Manages the lifecycle of the namespaces. 
	Deletes resouces within the namespace when it is removed. 

