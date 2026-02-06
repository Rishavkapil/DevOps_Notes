
- Logical network component in a VPC that represents a virtual Network Card.

- You can attach to an EC2 instance in a VPC. It provides Networking capabilities to the instances. 

- When we create an EC2 instance , AWS automatically attaches a primary ENI (eth0) 

Without ENI, 

- If A fails, & B spins up to recover, IP changes. 
So with ENI, we can just attach ENI to B.

