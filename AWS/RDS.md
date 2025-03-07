### What is amazon RDS 

Amazon RDS is a managed database service provided by AWS. 

It makes it easy to setup and operate a scalable relational database. 


Similar to EC2 , RDS is amazon's service , which provides an easily scalable Hardware to store your data remotely. 

Amazon Highlights the advantages of RDS by comparing it to on-permises server. 


* **On-permises :**  In software programming, "On-permises" means that hardware or software is installed , owned and used by the users themselves. 


Latency : Latency means the time that the requestors(clients in our cases) have to wait for responses from the respondents to arrive. For example, if you took 2 seconds to load a page, 2 seconds are the latency for the response of the page.



##### DB Instances

Just like EC2, RDS manages the database in instances, the instances can be created and modified using AWS CLS, RDS API etc. 

##### DB Engines

Database engine means the relational Database software that runs on your DB instance. 
eg. POSTGRES , MYSQL , ORACLE etc. 

##### DB Instance Classes

The instance class is the computation power and memory capacity  of a database instance. Consider this is no. of CPU's and RAM of your instance. 

**There are 4 types of Classes :** 
	1. **General Purpose :** Well Balanced instance class type. Here "Well Balanced" means the balance between performance and memory. 
	2. **Memory Optimized :**  Memory intensive class type (High memory )
	3. **Brustable-performace :** Focuses on high performance. 
	4. **Optimized Reads :**  Optimized for "read" actions. 



##### DB Instance Storage

RDS uses AWS EBS(Elastic Block Storage) as the volume for database and log storage. You can select one of the following : 

* **General Purpose SSD :**
* **Provisioned IOPS SSD :**  
* **Magnetic(HDD) :** 


#### Amazon VPC 

The db instances need to run on a VPC . 

#### Creating RDS Instance

Lets create MySQL instance . 


![[Pasted image 20250307131949.png]]


for more refer to this blog post on medium : 
https://medium.com/@veerababu.narni232/aws-rds-relational-database-service-718916fe9692


