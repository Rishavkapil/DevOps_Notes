## Benefits of AWS Lambda

- Easy pricing
	- Pay per use & compute time 

- Free tier of 10,00,000 AWS Lambda requests & 400,000 GBs of compute time. 

#### Lambda Snapstart

- Improves your lambda function performance upto 10x at No extra cost for java, python and .net


## Lambda with RDS Proxy

- If Lambda function directly access your DB, they may open too many connections under high load. 

- **RDS Proxy :** 
	- Improves scalability by pooling & sharing DB connections

- Lambda function must be deployed in VPC, because the RDS proxy is never publically accessible. 

- To invoke lambda function from RDS and Aurora
- You must allow outbound traffic to your lambda function
- DB instance must have required permissions to invoke lambda function. 