
![[Pasted image 20250318160753.png]]

**RDS Proxy** is a fully managed database that serves as a proxy layer between the application and the database. 

* Client/application is pointed to RDS proxy endpoint , RDS proxy sits between the database and RDS to manage the DB connection. 
* RDS proxy works by pooling and sharing DB connections and thus makes applications more scalable as well as resilient to database failures.
* If you are running applications with unpredictable workloads, which require frequently open and closed database connections and you want to maintain high availability 





#### How does  it Work ?

![[Pasted image 20250318162652.png]]


* RDS proxy works by pooling and sharing DB connections that enable applications to share and re-use database connections thus reducing the load on the database and improve application performance. 


##### Connection Pooling and sharing RDS proxy

Connection pooling and sharing in RDS proxy refers to the process where the proxy manages the pool of database connections that can be re-used by different application requests. 

This reduces the overhead of opening and closing new connections, which includes CPU and memory costs such as TLS/SSL handshaking  , authentication etc. 


By pooling and sharing these connections , RDS proxy improves application performance and scalability , allowing applications to handle more traffic without overloading the database server. 


