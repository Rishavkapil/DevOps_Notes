Fully managed highly available with replication across multi-az.

- NoSQL database - with transaction support 

- Scales to massive workloads, distributed databases. 
- No maintenance, always available.
- In Dynamo DB, you can rapidly evolve schemas. 


### **Dynamo DB Read/Write Capacity Modes**: 

- Control How you manage your table's capacity(read/write throughput)


#### Provisioned Mode

- You specify the number of read/write per second. 
- You need to plan the capacity beforehand.
- This is useful, if load is predictable

#### On-Demand Mode

- Read/Writes automatically scales up or down with your workload
- No capacity planning needed. 
- Great for unpredictable workload. 


## DynamoDB Accelerator(DAX)

- Fully managed, highly available, seamless in-memory cache for **DynamoDB**
- Help solve Read Congestion by caching

- Microsecond latency for cached data.
- Doesn't require application logic modification. 

#### DynamoDB Stream Processing

Use Case - 
- React to changes in real-time
- Real time usage analytics


