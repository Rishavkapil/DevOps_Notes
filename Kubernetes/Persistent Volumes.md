	In kubernetes , a persistent volume(PV) is the piece of storage in the cluster that has been provisioned by an administrator using Storage classes. 

![[Pasted image 20250410152542.png]]


Persistent volume is like a hard drive in your cluster .

It is the storage space that lives outside the pod. 



### Why persistent volumes

Normally , when a pod is deleted or recreated, any data stored in its container file system is lost. A persistent volume allows data to outlive the  lifecycle of individual pods. 

### Key Concepts 

1. **Persistent Volume :** A cluster resource that represent actual storage(like a physical disk or cloud volume)

2. **Persistent Volume Claim(PVC) :** 
	* A request for storage by user. 
	* Specifies the size , access mode etc. 
	* kubernetes binds PVC to a suitable PV. 
	* 
3. **Storage Class :** 
	* Describes different stages of storage. 


### Access Modes

* **ReadWriteOnce(RWO)** - Only one node can mount the volume for read/write. 
* **ReadOnlyMany(ROX):** multiple nodes can read from the volume 
* **ReadWriteMany(RWX) :** multiple nodes can read/write. 



### How it works

* Admin sets up the PV or defines a storage class 
* User creates a PVC
* Kubernetes matches the PVC to a suitable PV. 
* The pod mounts the volume via the PVC. 




### Persistent volume claim

A request by your pod saying ; 

"Hey ! I need 1 gb of storage"

kubenetes say 
"Okay , here's a hard drive (PV) that matches your request"