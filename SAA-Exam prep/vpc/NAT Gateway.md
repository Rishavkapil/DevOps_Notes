
NAT = Network Address Translation

- Allows EC2 instances in private subnet to access Internet
- Must be launched in public subnet
- Must have elastic IP attached to it. 
- Route tables must be configured to route traffic from private subnets to the NAT Gateway. 


How the flow works : 

The EC2 instance in the private subnet first sends request to the NAT gateway in the public subnet, 

The NAT gateway will receive request from source IP to destination IP and then forwards the request to the internet/destination with its own IP as the source IP. 



NAT Gateway requires an Internet Gateway(IGW) 

now traffic goes from **private subnet --> NAT Gateway --> IGW**


#### NAT Gateway with High Availability

- NAT Gateway is resilient within a Single Availability Zone. 
- Must Create multiple NAT Gateways in multiple AZs for fault tolerance. 