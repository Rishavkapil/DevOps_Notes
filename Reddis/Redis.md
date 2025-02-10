**REDIS** (Remote Directory Server) is an open source , in-memory, NO-SQL key/value store that is primarily used as application cache or quick response database. 

Redis stores data in-memory(RAM) rather then on a disk or solid-state drive(SSD) which helps deliver unparalleled speed, reliability, and performance.

When an application relies on external data sources, the latency and throughput of those sources can create a performance bottleneck, especially as traffic increases or the application scales.
One way to improve performance in these cases is to store and manipulate data in-memory, physically closer to the application. Redis is built to this task: It stores all data in-memory—delivering the fastest possible performance when reading or writing data—and offers built-in replication capabilities that let you place data physically closer to the user for the lowest [latency](https://www.ibm.com/topics/latency).

##### Redis cache sessions 
Again, unlike NoSQL databases such as [MongoDB](https://www.ibm.com/topics/mongodb "mongodb") and [PostreSQL](https://www.ibm.com/topics/postgresql "postgresql"), Redis stores data in the server's main memory rather than on hard disks and solid-state drives.
Faster Data access 
High availability and scalability of services. 

### Redis queues
It put tasks in queue that may take longer to process than usual.


#### Redis Datatypes

While technically a key/value store, Redis is an actual data structure server that supports multiple data types and structures, including:

- Unique and unsorted string elements  
      
    
- Binary-safe data  
      
    
- HyperLogLogs  
      
    
- Bit arrays  
      
    
- Hashes  
      
    
- Lists



###### Redis Sentinal

**Redis Sentinel** is a high-availability solution for Redis. It is a distributed system designed to manage and monitor Redis instances, providing automatic failover and ensuring that your Redis setup remains available even in the event of a failure.

Redis Sentinel is a separate process (or set of processes) that runs alongside your Redis instances. Its primary purpose is to:

1. **Monitor Redis instances** (both master and replicas) to ensure they are functioning properly.
    
2. **Detect failures** (e.g., if the master node goes down).
    
3. **Automatically promote a replica to master** in case of a failure (automatic failover).
    
4. **Notify administrators** or other systems about failures and changes in the Redis setup.



###### Redis Cluster

[Redis Cluster](https://redis.io/docs/latest/operate/oss_and_stack/management/scaling/) is a distributed implementation of Redis that automatically splits datasets among multiple nodes.


###### Redis pub/sub
Because Redis supports the use of [publish and subscribe (Pub/Sub) commands](https://redis.io/docs/latest/develop/interact/pubsub/), users can design high-performance chat and messaging services across all their applications and services. This includes the ability to use list data structures to run atomic operations and blocking capabilities.


###### Redis persistence
Redis uses [persistent disk storage](https://redis.io/docs/latest/operate/oss_and_stack/management/persistence/) designed to survive process outages and [network](https://www.ibm.com/topics/networking "networking-a-complete-guide") bottlenecks.

**Persistent disk storage** refers to the ability of a system to save data to a non-volatile storage medium (like a hard drive or SSD) so that the data remains intact even after the system is shut down, restarted, or crashes.



### RedisInsight 

Redis Insight is a powerful tool for visualizing and optimizing data in redis or redis stack , making real time applications more easier. 
It supports both GUI based and CLI based interactions in a fully-featured desktop client. 




### Installation of Redis-Server on Linux


	`sudo apt update`
		1.    sudo apt install redis-server

 Following this, there is one important configuration change to make in the Redis configuration file, which was generated automatically during the installation.
				`sudo nano /etc/redis/redis.conf`

Inside the file, find the `supervised` directive. This directive allows you to declare an init system to manage Redis as a service, providing you with more control over its operation. The `supervised` directive is set to `no` by default. Since you are running Ubuntu, which uses the [systemd](https://en.wikipedia.org/wiki/Systemd) init system, change this to `systemd`:



			
				supervised systemd

After that , 
				`sudo systemctl restart redis.service`

Start by checking that the Redis service is running:

				sudo systemctl status redis.service

To test that Redis is functioning correctly, connect to the server using `redis-cli`, Redis’s command-line client:

			$ redis-cli

In the prompt that follows, test connectivity with the `ping` command:

				ping
				output 
				Pong

This output confirms that the server connection is still alive. Next, check that you’re able to set keys by running:

				set test "It is working "
				output 
				OK
Retrieve the value by typing: 

				get test
				output
				It is working



###### Binding it to localhost

			`sudo nano /etc/redis/redis.conf`

Then, restart the service to ensure that systemd reads your changes:
					`sudo systemctl restart redis`



##### Configuring a redis password

Configuring a Redis password enables one of its two built-in security features — the auth command, which requires clients to authenticate to access the database. The password is configured directly in Redis’s configuration file, /etc/redis/redis.conf, so open that file again with your preferred editor:


			sudo nano /etc/redis/redis.conf


Scroll to the `SECURITY` section and find a commented directive that reads:



						# requirepass foobared

Uncomment it by removing the `#`, and change `foobared` to a secure password.




After setting the password, save and close the file. Then restart Redis:



	sudo systemctl restart redis.service



To test that the password works, open up the Redis client:

				redis-cli

The following shows a sequence of commands used to test whether the Redis password works. The first command tries to set a key to a value before authentication:


					set key1 10

That won’t work because you didn’t authenticate, so Redis returns an error:



The next command authenticates with the password specified in the Redis configuration file:


				auth your_redis_password
		