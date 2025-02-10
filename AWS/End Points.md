
In AWS, an endpoint is a URL that serves as an entry point for accessing AWS services.


Allows us to communicate with the AWS services privately without going over the internet

An **endpoint** is a URL or network address that serves as an entry point for accessing AWS services or resources.



Here are the main types of endpoints in AWS:

### 1. **Service Endpoints**

These are the public URL's provided by AWS to access their services over the internet.
Each AWS service has its own endpoint 

syntax : `https://<service>.<region>.amazonaws.com`


Example:

- S3 endpoint: `https://s3.us-east-1.amazonaws.com`
    
- EC2 endpoint: `https://ec2.us-west-2.amazonaws.com`

These endpoints are used when interacting with AWS services via APIs, SDKs, or the AWS Management Console.



### 2. **VPC Endpoints (PrivateLink)**


- VPC endpoints allow you to privately connect your Virtual Private Cloud (VPC) to supported AWS services without using the public internet.


### 3. **API Endpoints**


- AWS services expose APIs that allow programmatic access to their features. These APIs are accessed via specific endpoints.
    
- Example:
    
    - AWS Lambda API endpoint: `https://lambda.<region>.amazonaws.com`
        
- These endpoints are used by developers to integrate AWS services into their applications.




## Creating a connection Endpoint to connect private instances


EC2 Instance Connect Endpoint allows you to connect securely to an instance from the internet, without using a bastion host, or requiring that your virtual private cloud (VPC) has direct internet connectivity.