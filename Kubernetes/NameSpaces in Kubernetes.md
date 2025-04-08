

# What is a Namespace ?

In kubernetes , we organize resources in namespaces. 

It is like a virtual cluster inside a cluster. 

Namespaces provide a mechanism for isolating resources within a single cluster. 

Names of the resources need to be unique within a single namespace , 


###### When to use multiple namespaces. 

Namespaces are intended to use in environments with many users spread across multiple teams , or projects. 



## Initial Namespaces

Kubernetes start with four initial namespaces : 



### **default** 

kubernetes includes this namespace so that you can start using your new cluster without first creating a namespace . 

### **kube-node-lease**

this namespace holds ==lease objects== associated with each node. Node leases allow the kubelet to send ==heartbeats== so that the control plane can detect node failure. 



**Lease Objects :** Lease objects are special type of resources used for ==Leader Election== and node heartbeat management. 

==lease object== is a resource defined under the coordination.k8s.io/v1 API group . 


###### **Key uses of Lease objects** 

1. ==**Leader Election**== : 
		In high-availability systems , multiple components of a component may run , but only one should be active at a time. 
		The lease object is used to record which  pod is the leader and for how long . 
- ==**Node heartbeats**== : 
		- Kubernetes nodes use lease objects to send heartbeats to the control plane instead of updating the Node.status object frequently . 
		- This reduces the load on etcd database. 
	Node heartbeats in kubernetes are the regular signals sent by a node to the control plane(specialy the kube-apiserver ) to let it know : 


		"Hey! I'm alive and working fine"



### **kube-public**

This namespace is readable by all users (even those who are not authenticated ) by default 
Its main characteristics  : public read access , even to unauthenticated users. 


Why do we need this ? 
	- To share public information about the cluster 
	- Most commonly used to store a ConfigMap called cluster-info (created by kubeadm ). 
This helps new nodes or clients discover cluster information without needing full authentication. 


