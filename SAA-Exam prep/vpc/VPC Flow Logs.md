
- Capture information about IP traffic going into your interfaces. 
	- VPC Flow logs
	- Subnet flow logs
	- ENI flow logs
- Helps to monitor and troubleshoot connectivity issues. 

- Flow logs data can go to S3 , cloudwatch logs & Kinesis data firehouse. 
- Query logs using Athena on S3 or cloudwatch logs insights. 

### VPC Flow logs - Troubleshoot SG & NACL issues. 


**Incoming requests**

Inbound REJECT => NACL or SG is refusing the request

Inbound ACCEPT , Outbound REJECT => NACL

Because security group is stateful, if inbound is allowed then outbound is automatically allowed. 


**Outgoing requests**

Outbound REJECT => NACL or SG issue

Outbound ACCEPT  , Inbound REJECT => NACL issue