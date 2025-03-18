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
* **Magnetic(HDD) :** In simple terms , magnetic storage is HDD, . Amazon claims that Magnetic storage is for **backward compatibility.** 

**Backward Compatibility**  is an ability of the newer version of the product working well with the older version of the product. 



#### Amazon VPC 

The db instances need to run on a VPC . 

#### Creating RDS Instance

Lets create MySQL instance . 


![[Pasted image 20250307131949.png]]


for more refer to this blog post on medium : 
https://medium.com/@veerababu.narni232/aws-rds-relational-database-service-718916fe9692




#### AWS regions and Availability Zones


As the name suggests, regions are the geographical areas in which  Amazon's hardware(storage devices in this case) placed.The availability zones are the geographical areas of the hardware placed in the each region. 

**AWS Regions** is a cluster of data centers in a specific geographic area, Northeastern United states , Western Europe etc. 


**Availability Zones** are highly available data centers within Each AWS region. 

Each **AWS Regions**  consist of multiple AZ's . However, each AZ is restricted to a specific AWS region. 


![[Pasted image 20250317155620.png]]





#### Read Replica 

We can enable read replica on our DB cluster. Read replica is the copy of your primary(source) database instance that allows us to offload read-only queries and distribute read traffic across multiple database instances. 

It is the read-only copy of DB instance . 

You can reduce the load on your primary database instance by routing queries from your applications to the read replica. 

In this way, you can elastically scale out beyond the capacity constraints of a single DB instance for read-heavy(heavy read operations compared to write operations) database workloads. 


***Read replicas are asynchronously replicated from the source database, which means they might lag behind the primary database by few milliseconds to seconds , depending on the replication latency .*** 



#### Proxies 

AWS RDS proxy is a fully-managed database proxy for amazon RDS. RDS proxy works by pooling and sharing DB connections and thus makes applications more scalable as well as resilient to database failures . 


**Connection pooling and sharing in RDS proxy**  refers to the process 






#### Multi-AZ deployments 

In Multi-AZ deployments with Amazon RDS, your primary database is automatically replicated to a standby instance in another Availability zone within the same AWS region. 

The primary instance handles read/write access while the standby instance stays in sync for disaster recovery. 

If the primary instance or its AZ fails RDS automatically switches to the standby instance ensuring minimal downtime. 

![[Pasted image 20250318102604.png]]


In **Multi-AZ DB cluster deployment**, there is one writer DB instance and two reader DB instance spread across three separate availability zones within the same AWS region. 



![[Pasted image 20250318103358.png]]



#### Amazon Dynamo DB

Dynamo DB allows users to create databases capable of storing and retrieving any amount of data and comes in handy while serving any amount of traffic. 

It is a fully managed NOSQL database service. 


#### Amazon RedShift

It is a data warehouse that is based on the cloud . It handles large scale of data and is known for its scalability. 


#### DB Parameter Group 

A DB Parameter Group in AWS RDS is the collection of database configurations settings that can be applied to a DB instance. 

These settings specify how the database is configured , such as amount of resources, like memory , to allocate to a database. 

***NOTE :*** If you create a DB instance without specifying the DB parameter group , a default DB parameter group is created. This means that default parameter group can't be modified. 