
Site-to-site VPN requires two things, 
1. Virtual Private Gateway(VGW)
	- VPN concentrator on the aws side of the VPN connection. 
	- VGW is created and attached to the VPC from which you want to create the site-to-site VPN connection.  


2. Customer Gateway: 
	- Software application or physical device on customer side of the VPN connection. 


## How to do a site-to-site VPN connection

- **Customer gateway device(on-premises)**
	- What IP address to use ? 
		- If customer gateway is public , then there is public internet-gateway IP address for your customer gateway device.
		- If Customer gateway is private, then it will be behind NAT device that has NAT-T enabled , and then use the public IP of NAT device. 

Even though this is setup , the site-to-site vpn will not work until you enable route propagation for Virtual Private gateway in the route table that is associated with your subnets. 



## AWS VPN CloudHub

IF you have a Virtual Private Gateway and have multiple customer-gateway 

- Provides secure communication between  multiple sites, if you have multiple VPN connections 
- 