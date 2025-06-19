
### Public IP address 

A public IP address is an ip address assigned by your Internet Service Provider(ISP) that is unique across the entire network. It is used to define your network to the outside world.

**Purpose :** Public Ip enables devices to communicate directly with other devices or servers on the Internet. They are necessary for hosting websites, running servers, or allowing remote access to devices from outside your local network. 

**Security :** Public IP's are exposed to the internet, making them more vulnerable to attacks unless protected by firewalls or other security measures. 

### Private IP Address

A Private IP address is used within a local Area Network(LAN) such as home, office or enterprise network. These addresses are not routable on the public Internet and are assigned by router to each device in the network. 

**Purpose :**  Private Ip's allow devices within the same network to communicate with each other security and efficiently, without needing to connect to internet. 

Private Ip's have local reach only and are not visible outside the network. 

**Security :** Since Private Ip's are not exposed to internet, they provide an additional layer of security, protecting internal devices from external threats. 



##### Now why do we need private Ip addresses ?

* **Conservation of Private IP addresses :** There are limited number of public IPV4 addresses. Private IPs allow multiple devices on a local network to share  a single public IP address through Network Address Translation(NAT), conserving the limited pool of public IP addresses. 
* **Enhanced Security :** Private Ip's are not directly accessible from the internet, reducing exposure to cyber threats such as hacking and malware. 
* **Local Network Communication :** Devices like printers, file servers and computers can communicate within the network without needing an internet connection. 


Now You will be thinking, like how public ips are less and private ip's are more, 

thats because Two devices that are in different network can have same private IP but they can not have same public ip on the internet. 

Private IPs can be reused across different private networks.