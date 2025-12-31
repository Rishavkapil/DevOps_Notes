
Kafka has two independent ideas: 

* Partitioning : splits data
* Replication: copies data

## Topics
Let's take an example of amazon, 

lets say we have a topic for orders . 

This topic receives events like : 

* Order placed 
* Order cancelled 
* Order shipped

## Partitioning (data distribution)

Amazon wants scalability, so they create partitions : 

```
orders (Topic)
 ├── orders-0  (region = North)
 ├── orders-1  (region = South)
 ├── orders-2  (region = West)

```

* Each partition contains different data.
* No overlap
* Partitioning = Sharding


## Replication (data safety)

Now amazon wants fault tolerance.

They set : `replication.factor = 3` 

This means ***Each Partition will be copied to 3 brokers*** 


## Write and Read Flow

When producer sends an order: 

* Produces hashes key( order ID or region)
* kafka chooses one partition
* Data goes to Leader of that partition only.
* Followers copy data from leader. 
* and **Consumers will read data only from leaders.** 





## So who is the leader like broker or partition ??


A broker never stores only replicas. 

Each broker stores : 
* Some Partitions as leaders
* Some partitions as followers (replicas)



```
Broker-1:
  orders-0 → Leader
  orders-1 → Follower
  payments-2 → Leader

Broker-2:
  orders-1 → Leader
  orders-0 → Follower
  shipping-0 → Leader

```


