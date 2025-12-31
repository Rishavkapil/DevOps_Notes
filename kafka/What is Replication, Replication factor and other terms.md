
Kafka has two independent ideas: 

* Partitioning : splits data
* Replication: copies data


Let's take an example of amazon, 

lets say we have a topic for orders . 

This topic receives events like : 

* Order placed 
* Order cancelled 
* Order shipped

Step 2 : Partitioning (data distribution)

Amazon wants scalability, so they create partitions : 

```
orders (Topic)
 ├── orders-0  (region = North)
 ├── orders-1  (region = South)
 ├── orders-2  (region = West)

```

