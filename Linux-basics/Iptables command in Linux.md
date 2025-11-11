
The iptables/ip6tables  command in linux is a powerful tool that is used for managing the firewall rules and network traffic. It facilitates allowing the administrator to configure rules that help how packets are filtered, translated or forwarded. 

* administrator tool for ipv4/ipv6 packet filtering and NAT.


iptables is used to setup , maintain , and inspect the tables of ipv4 packet filter rules in the linux Kernel. Several different tables may be defined. Each table contains built-in chains and may also contain user-defined chains. 

Each chain is a list of rules which can match set of packets. Each rule specifies what to do with the packet that matches. This is a target which may be a jump to user-defined chain in the same table. 

A firewall rule specifies criteria for a packet and target. If the packet does not match the next rule in the chain is examined, If it does match, the next rule is specified by the value of the target, which can be name of user defined chain. 


Accept means let packet through , DROP means drop the packet on the floor, RETURN means stop traversing this chain and resume at the next rule in the previous chain


### What is firewall ?

To cover the fundamentals, firewalling is the idea of deciding which packets are allowed to go in and out of the system. 

The packets in the internet (or any other network) are transferred using ports. We have system reserved ports for services like NGINX or Apache (80/443)

We also have ports that are used by user itself. For example, when you have written a web application that runs on PORT 8000. 


#### Why use iptables ?

now you'll be thinking why not using `ufw` or `firewalld` , but they only allow you to accept or reject a packet. But iptables allows you lot more like NAT, logging , forwarding etc. 

## iptables architecture

iptables consist of different components which are discussed below : 

* **Chains:** There are 5 chains in iptables each responsible for specific task. These chains are : prerouting, input, forward, output and postrouting. As the name suggest, they are responsible for packets either as soon as they arrive, if they are destined for local socket or just before routing to outside world. 

*  **Tables:** Again different table are responsible for different tasks. The list contains filter, mangal, raw & security. The first two are the most used. Filter is responsible for filtering and restricting the packets to/from our computer. NAT is responsible for network address translation. 

* **Targets :** Targets specify where packets should go. This is decided using either iptables  own targets : ACCEPT, DROP or RETURN or its extensions eg. DNAT, LOG, MASQUERADE, REJECT, SNAT, TRACE, TTL. Targets are divided into terminating and non-terminating. 



#### iptables chains : 


As mentioned above, each chain is responsible for specific task . 

* **Prerouting :** this chain decides what happens to the packet as soon as it arrives at the network interface. We have different options such as altering the packet , dropping a packet, or doing nothing at all and letting it slip and be handled elsewhere along the way. 

* **Input:** This is one of the popular chains as it almost always contains strict rules to avoid some evil doers on the internet harming our computer. If you want to open a port a port/block a port, this is where you'd do it. 

* **Forward:** This chain is responsible for packet forwarding . Which is what the name suggests. We may want to treat a computer as a router and this is where some rules might apply to do the job. 

* **Output:**  This chain is responsible for all your web browsing among many others. You can't send a single packet without. You have a lot of options whether you want to allow a port to communicate or not. 

* **Postrouting :**  This chain is where packets leave their trace last , before leaving our computer. 


#### iptables tables  


* **Filter:** This is the table most used on daily basis. Which is why it is the default table. In this table, you would decide whether a packet is allowed in/out your computer. If you want to block a port to stop receiving, this is the stop. 

* **NAT:** This table is the second most popular table and is responsible for creating new connections. 

* **Mangle :** For specialized packets only. This table is for changing something inside the packet either before coming in or leaving out. 

* **RAW :** 