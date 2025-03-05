
![[Pasted image 20250305145126.png]]


When the user try to hit the url , the request first goes to DNS Server which is in this case ROUTE 53, So as soon as the request lands on route 53 , it tries to resolve the request. 
And once that request is resolved , it is forwarded to particular resource that we are using. 

So this request forwarding is happening with the help of A-Record 




### Hosted Zone in Route 53

Hosted Zone is a container for managing DNS records for a domain that uses ROUTE 53 as its DNS provider. 

It allows you to configure that how traffic should be routed for a specific domain and its sub-domains such as example.com and acme.example.com

There are two types of Hosted Zones : Public Hosted Zones and Private Hosted Zones. 

**Public Hosted zones:**  Contains records for routing traffic on the internet 
**Private Hosted Zones :**  Contains records for routing traffic within Amazon VPC. 




### Creating Hosted Zone
**Lets say we forward request to ec2** 

First we will need to create a hosted zone , 
there we have two options one for public and one for private, 
If we select public then we need to give our Domain which we have to buy
If we select private then we need to create VPC and Create that hosted zone within that VPC. 

Then we need to launch an instance in that VPC  and to check host apache2 webpage on that instance. 

Then we need to create a record in the Hosted Zone which would point to the public IP of our ec2 . 


![[Pasted image 20250305162341.png]]



But the problem with this simple routing is , whenever we are creating this A record , we are putting a static IP here.  So suppose we want to change the ec2 instance and we want to have another IP address, then this record will be useless, because the resource IP has been changed and we are using the same older IP address. 

To Fix this issue , we need to create a Load Balancer.