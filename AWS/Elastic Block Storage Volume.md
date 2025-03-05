Elastic Block Storage volume is a virtual storage provided by aws which is very similar to hard disk storage. 
		These are the storage volume that you can attach to ec2 instances. After you attach a volume, you can use it as you simply use your local storage.




##### What is an EBS volume ?


An EBS volume is a network drive you can attach to your instance while they run. 

It allows your instances to persist data, even after termination.

They can only be mounted to one instance at a time. 



### EBS Snapshots



Make a backup(snapshot) of your EBS volume at a point in time. 
Not necessary to detach volume to do snapshot, but recommended. 


##### **EBS snapshot Features :** 


**EBS snapshot Archives :**  Move a snapshot to an "archive tier " that is 75% cheaper. 

**Recycle Bin For EBS snapshots :**  Setup rules to retain deleted snapshots so you can recover them after an accidental deletion. 


![[Pasted image 20250221122241.png]]



