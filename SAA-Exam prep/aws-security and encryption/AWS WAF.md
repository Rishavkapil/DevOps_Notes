- Protects your web application from common web exploits(Layer 7)

- Layer 7 is HTTP (& Layer 4 is TCP/UDP)


- Deploy on - 
	- ALB
	- API Gateway
	- Cloudfront
	- AppSync graphql 
	- Cognito user pool

- WAF can't be deployed on NLB
- Define web ACL rules. 

- **Can be used to prevent common attacks like SQL Injection, Cross-Site Scripting(XSS)**
### Fixed IP while using WAF with Application Load Balancer. 

Use Global Accelerator for fixed IP and waf on the ALB. 