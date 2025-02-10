
### What is a Virtual Private Cloud?
A virtual Private Cloud is a private cloud located inside the public cloud that enables you to experience the benefits of virtualized network while using public cloud resources.



##### How Does a VPC Differ from a Private Cloud?


A private cloud consists of infrastructure dedicated completely to a single organization.
Usually, an organization will buy the cloud infrastructure, install the software, and hire an IT management team. In this case, the organization owns everything from top to bottom.


![[Pasted image 20250204101014.png]]


Imagine a public cloud as a crowded restaurant, and a virtual private cloud as a reserved table in that crowded restaurant. Even though the restaurant is full of people, a table with a "Reserved" sign on it can only be accessed by the party who made the reservation. Similarly, a public cloud is crowded with various cloud customers accessing computing resources – but a VPC reserves some of those resources for use by only one customer.



The technical term for multiple separate customers accessing the same cloud infrastructure is "multitenancy"

**Subnets:** A [subnet](https://www.cloudflare.com/learning/network-layer/what-is-a-subnet/) is a range of [IP addresses](https://www.cloudflare.com/learning/dns/glossary/what-is-my-ip-address/) within a network that are reserved so that they're not available to everyone within the network, essentially dividing part of the network for private use. In a VPC these are private IP addresses that are not accessible via the public Internet, unlike typical IP addresses, which are publicly visible.


**VLAN:** A [LAN](https://www.cloudflare.com/learning/network-layer/what-is-a-lan/) is a local area network, or a group of computing devices that are all connected to each other without the use of the Internet. A VLAN is a virtual LAN. Like a subnet, a VLAN is a way of partitioning a network, but the partitioning takes place at a different layer within the [OSI model](https://www.cloudflare.com/learning/ddos/glossary/open-systems-interconnection-model-osi/) .

**VPN:** A [virtual private network (VPN)](https://www.cloudflare.com/learning/access-management/what-is-a-vpn/) uses [encryption](https://www.cloudflare.com/learning/ssl/what-is-encryption/) to create a private network over the top of a public network. VPN traffic passes through publicly shared Internet infrastructure – [routers](https://www.cloudflare.com/learning/network-layer/what-is-a-router/), [switches](https://www.cloudflare.com/learning/network-layer/what-is-a-network-switch/), etc. – but the traffic is scrambled and not visible to anyone.

**Network Address Translation (NAT):** This feature matches private IP addresses to a public IP address for connections with the public Internet. With NAT, a public-facing website or application could run in a VPC.





**ACL**: ACL is a security feature in AWS which is used to control traffic in and out of subnets.


A _network access control list (ACL)_ allows or denies specific inbound or outbound traffic at the subnet level. You can use the default network ACL for your VPC, or you can create a custom network ACL for your VPC with rules that are similar to the rules for your security groups in order to add an additional layer of security to your VPC.

There is no additional charge for using network ACLs.

The following diagram shows a VPC with two subnets. Each subnet has a network ACL. When traffic enters the VPC (for example, from a peered VPC, VPN connection, or the internet), the router sends the traffic to its destination. Network ACL A determines which traffic destined for subnet 1 is allowed to enter subnet 1, and which traffic destined for a location outside subnet 1 is allowed to leave subnet 1. Similarly, network ACL B determines which traffic is allowed to enter and leave subnet 2.

	