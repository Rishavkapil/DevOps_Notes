
For Edge locations 

### BP1 - Cloudfront

- Web application delivery at the edge. 
- Protect from DDoS common attacks (SYN floods , UDP reflection etc .)

### BP1 - Global Accelerator

- Access your application from the edge. 
- Integration with Shield for DDoS protection. 


### BP3 - Route 53

- Domain Name Resolution at the edge
- DDoS protection mechanism. 



## Infrastructure Layer Defence(BP1, BP3, BP6)

- Protect EC2 Instances against high traffic. 

## Amazon EC2 with Auto scaling 

- Helps scale in case of sudden traffic surges including a flash crowd or a DDoS attack. 


## Elastic Load Balancing

- Elastic Load Balancing scales with the traffic increase and will distribute traffic to many EC2 instances. 

## Detect and filter malicious web requests 

- CloudFront cache static content and serve it from edge locations, protecting backend. 

- AWS WAF is used on top of CloudFront  and Application Load Balancer to filter and block requests based on request signatures. 