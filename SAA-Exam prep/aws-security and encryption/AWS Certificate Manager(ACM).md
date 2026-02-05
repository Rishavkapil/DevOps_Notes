
-  Easily provision, manage & deploy TLS certificates.
- Provide in-flight encryption for websites(HTTPS).
- Supports both public & private TLS certificate
- Free of charge for public TLS Certificates. 
- Automatic TLS renewal. 
- Integrations with (load TLS certificates on ):
	- Elastic Load Balancers
	- Cloudfront distributions
	- APIs on API Gateway. 
- **Cannot be used with EC2**



### Requesting a Public Certificates

1. List domain names to be included in the certificate
2. Select validation method : DNS Validation or Email Validation
	- DNS validation is preferred for automation process. 
	- Email validation will send emails to contact addresses in the WHOIS database
	- DNS validation will leverage a CNAME records to DNS config. 
3. It will take few hours to get verified. 
