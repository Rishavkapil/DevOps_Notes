

Kubernetes volumes provide a way for containers in a pod to access and share data via the filesystem.

----------------------------------------------

Why volumes are important ?

* Data Persistence : On-disk files in a container are ephemeral, which presents some problems for non-trival applications when running in containers. One problem occurs when a container crashes or is stopped , the container state is not saved so all of the files that were created or modified during the lifetime of the container are lost. After a crash kubelet restarts the container with a clean state. 

* Shared Storage : Another problem occurs when multiple containers are running in a pod and need to share files. It can be challenging to setup and access a shared file system across all of the containers.


-----------------------------------------------

How volumes work ??

Kubernetes support many types of volumes . A Pod can use any number of volumes simuntaniously . 

Ephemeral volume types have a lifetime linked to a specific pod, but persistent volumes exist beyond the lifetime of any individual pod, When a pod ceases to exist, kubernetes destroys epheremal  volumes , However kubernetes does not destroy persistent volumes. For any kind of volume in a given pod, data is preserved across container restarts. 

At its core, volume is a directory, possibly with some data in it. which is accessible to the container in a pod. How that directory  comes to be, the medium that backs it and the contents of it are determined by the particular volume type used. 

To use a volume, specifies the volume to provide for the pod in .spec.volumes and declare where to mount those volumes into container in .spec.containers[*].volumeMounts. 


When a pod is launched, a process in the container sees a file system view composed from the initial contents of the container image. 

Volumes are mounted at specified paths within the container file system. For each container file system defined 



--------------------------------------------------------------------------------------

Below is the simple non persistent pod creating file with attached volume, but that volume is non-persistent or its  lifetime is limited to Pod's lifetime, if the pod is crashed or deleted , the volume and data will also be vanished. However, Container's lifecycle will not affect the volume, but pod's lifecycle will. 


apiVersion: v1
kind: Pod
metadata: 
  name: redis-pod
  namespace: rishav-ns
spec:
  containers:
  - name: redis-container
    image: redis
    ports:
    - containerPort: 6379
    volumeMounts:
    - name: redis-storage
      mountPath: /data/redis
  volumes:
  - name: redis-storage
    emptyDir: {}          	# this is for non-persistent volumes
    
    
    
===============================================================================================
  
Persistent Volumes (PV) : 

Persistent volumes are storage resources provisined in a kubernetes cluster. managed by cluster administrator. They provide an abstraction layer over physical storage devices, allowing users to access storage without needing to know the underlying infrastructure details. 

Available options : 

* Capacity : Specifies the size of the volume. 
* Access Mode : Defines how volumes can be accessed. Below are the available options : 

1. ReadWriteOnce : Can be mounted as read-write by a single node. 
2. ReadOnlyMany : Can be mounted as read-only by multiple nodes. 
3. ReadWriteMany : Can be mounted as read-write by multiple nodes. 


* StorageClassName : Associates the PV wiht the specific storage class. 

* Volume Mode : Determines whether the volume is mounted as a file system or block device. 


* Persistent Volume Reclaim Policy : Determines what happens to the PVs resources when released. 

* Mount Options : Additional options to be passed to the mounted command. 


Example  Manual PV creation : 


apiVersion: v1
kind: PersistentVolume
metadata: 
  name: my-pv
  namespace: rishav-ns
  labels:
    type: local
spec:
  capacity: 
    storage: 1Gi
  storageClassName: standard
  accessModes:
  - ReadWriteOnce
  hostPath:
    path: "/home/ubuntu/testing"
    type: DirectoryOrCreate

===========================================================================

PersistentVolumeClaim(PVC) : 
Persistent Volume Claims are requests for storage made by users or applications running in the cluster. They allow users to consume storage without needing to know the specifics of how it is provisined. 

Available Options : 

* Capacity : Specifies the minimum size of the Volume 
* AccessMOdes : 
  1. ReadWriteOnce : Can be mounted as read-write by a single node. 
  2. ReadOnlyMany : Can be mounted as read-only by multiple nodes. 
  3. ReadWriteMany : Can be mounted as read-write by multiple nodes. 



StorageClassName: Requests a specific Storage Class

* Volume Mode: Determines whether the volume is mounted as a filesystem or block device. File System is the default mode used when volumeMode parameter is omited. 



Example : Dynamic PV provisioning with SC


apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: my-pvc
  namespace: rishav-ns
spec: 
  accessModes: 
  - ReadWriteOnce
  storageClassName: standard
  resources: 
    requests: 
      storage: 1Gi
  volumeName: my-pv




====================================================================

Storage Class(SC): 

Storage class defines the type of storages available in the cluster and how they are provisined. They enable dynamic provisioning of PVs based on predefined templates or policies. 

Available options: 

* Provisioner: Specifies the type of volume plugin used for provisioning . 

* Parametres : Custom parametres for the provisioners. 

* Reclaim Policy : Determines what happens to the PV's resources when released. 



    ========================================================
    
    
    
    User creates a PVC (Persistent Volume claim) , it will be defined with specifications that are required by the user in the volume, If any volume matches that volume, it will be binded with that PV
    
    It will match the PVC with the existing PV, 	
    
    
    
    PV is the total Storage we have , and PVC is what we are requesting. 
    
    ==================================================
    
    
    There are three reclaim policies that we have and those are 
    1. Retain : PV will still exist even if pvc is deleted 
    2. Delete : If the PVC is deleted , then PV will also be deleted. 
    3. Recycle : WHen pv will be deleted , it will be made available to other pods 
   

