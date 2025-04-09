
## What is subnetting ?

Subnetting is a method in networking to ==divide the large IP network into smaller , more manageable sub-networks (subnets)==. It helps improve network performance , security and efficient IP address management. 



### Why do we need subnetting ?

Let's say you are given a network like **192.168.1.0/24** which has **256 Ip addresses** , but you only need : 
30 for sales , 20 for HR , 50 for IT . 

If you use /24 for each department , you waste IPs. 

Subnetting solution : 

You divide the /24 network into smaller parts : 
* Assign /27 to sales 
* Assign /27 to IT, 
* Assign /28 to HR. 



### Key concepts in subnetting 

##### IP address 
eg. 192.168.1.10
It consist of : 
* networking part : identifies the network
* Host part : identifies a device in a network 


##### Subnet mask 

Defines which part of the IP is the network and which part is the host. 
eg. **255.255.255.0 (or /24) , here first 24 bits are network bits.** 

IPV4 is 32 bit long

In CIDR block , there are 4 blocks each of 8 bits size. 

##### Private IP ranges : 

10.0.0.0 - 10.255.255.255 
172.16.0.0 - 172.31.255.255
192.168.0.0 - 192.168.255.255 

How many ip address can we create from the following ip with subnet mask 

		10.0.0.1/8


THIS MEANS  the first block of this ip is fixed and remaining we can change. 

