
Manages all the firewall rules in all accounts of an AWS Organization. 

- We can set security policy in this 
	- security policy = common set of rules.
		- WAF rules(ALB, API Gateway , Cloudfront)
		- AWS Shield advanced(ALB,CLB,NLB, Elastic IP, Cloudfront)
		- Security groups for EC2
		- AWS Network firewall (VPC level)
		- Amazon route53 Resolver DNS firewall. 


- **Rules are applied to new resources as they are created across all and future accounts in your organization.** 



