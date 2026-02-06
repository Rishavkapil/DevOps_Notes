- Sometimes you want to control over the EC2 placement strategy. 


When you create a placement group , you specify one of the following strategies for the group : 

- **Cluster**: Clusters instances into a low-latency group in a single availability zone. 

- **Spread**: spreads instances across underlying hardware(max 7 instances per group per AZ)

- **Partition**: Spreads instances across many partitions (which rely on different set of racks ) within an AZ. 