
#### EFS(Elastic File system) : 

Managed NFS(Network File System) that can be mounted on 100s of EC2

EFS works with Linux EC2 instance in multi-AZ.



![[Pasted image 20250219155953.png]]



###### **EFS Infrequent Access (EFS-IA)** : 

Storage class that is cost-optimized for files not accessed every day. 

Upto 92% lower cost compared to EFS Standard. 

EFS will automatically move your files to EFS-IA based on last time they were accessed. 

   


