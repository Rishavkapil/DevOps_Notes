
VPC peering is a method that allows two virtual private cloud to connect and communicate privately using private ip address for traffic flow between them without the need of public internet.

###### Steps to establish VPC Peering Connection

First, you need to create two vpc's 
then you need to launch instance in those two vpc's 
then you need to establish a peering connection between those two
after creating a peering connection , you need to add a new route in the routing table of both vpc's and thats it :)


**OPTIONAL**:

you can host a apache server on both devices to check for connection
