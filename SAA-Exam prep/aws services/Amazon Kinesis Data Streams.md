Collect and Store streaming data in Real-time.

- We have producers that send data to kinesis data streams.

- Stream: A stream is made up of shard. 

shard = unit of capacity

- Consumers: 
	-  who reads data
		- Lambda 
		- EC2 apps
		- Kinesis data Analytics
		- Kinesis Firehouse
		- Custom apps

**Capacity Modes:** 

1. **Provisioned Mode:** 
	- Choose Number of shards
	- Each shard gets 1MB/s
	- Scale manually to increase or decrease the number of shards.

2. **On-Demand mode:**
	- No need to provision and manage. 
	- Can scale automatically. 

