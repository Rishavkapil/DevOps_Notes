- Provides a dedicated private connection from remote network to your VPC. 

- Dedicated connection must be setup between your DC and AWS direct connect locations.

- You also need to setup a Virtual Private Gateway on your VPC. 

- Access public and private resources using the same connection


**USE CASES :** 
- Increase bandwidth throughput - working with large datasets , lower costs. 
- More consistent network experience - applications using real-time data feeds. 



# Direct Connect Gateway

If you want to setup direct connect to one or more VPC in many different regions (same account ), you must use a direct connect gateway. 


### Direct Connect - Connection types 

- Dedicated Connections : 1GBPS, 10 gbps, 100 gbps capacity
		- Physical ethernet port dedicated to a customer. 
		- Request made to AWS first, then completed by AWS direct connect partners.
- Hosted Connections : 50Mbps, 500 MBps, to 10GBps.
	- Connection requests are made via AWS direct connect partners
	- Capacity can be added or removed on demand. 
	- 1,2,5,10 GBps available at select AWS Direct Connect Partners. 

