
- Every service is publicly exposed (Public URL)
- VPC Endpoints (powered by AWS Private link) allows you to connect to AWS services using a private Network instead of public internet. 


IN case of issues: 

- Check the DNS settings in your VPC 
- Check the Route Tables. 


## Types of VPC Endpoints 


#### Interface Endpoints(powered by private link) 

- Provisions an ENI(private IP address) as an entry point (must attach a security group )
- supports most AWS services. 

#### Gateway Endpoints

- Provisions a gateway and must be used as a target in the route table.
- Supports both S3 and DynamoDB. 

**Gateway endpoint is most likely going to be preferred all the time at the exam.** 

Interface endpoint is preferred access is required from on-premise (site-to-site VPN or Direct Connect), a different VPC or different region. 





