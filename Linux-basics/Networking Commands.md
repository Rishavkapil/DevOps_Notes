1.  **SSH :** Secure shell - It is used to establish a secure connection between client and       server or between two devices. 
		Command : ssh "username"@"hostname or host ip address "
		Example : ssh "ubuntu"@127.0.0.1
2. **Public-Private keys** : For generating [public-private keys](https://www.geeksforgeeks.org/difference-between-private-key-and-public-key/) use the command:
		Command : ssh-keygen
3. **Top :** It is used to monitor system activity. It is used to show all the linux running processes.
		Command : top 
		![[Pasted image 20250121145401.png]] 
		Uptime : How long system has been running since last boot.
		
4. **ifconfig :** Interface configuration (ifconfig) is used to configure our ip address 
				Command : ifconfig 
				![[Pasted image 20250121145814.png]]  
				 **Finding my Public IP Addresses in Linux:** 
				 Command : curl ifconfig.me
					**Finding my private IP Address in Linux :** 
						 - Private IP addresses are used within a private network and are not directly accessible from the internet. 
						- The commonly used private IP address ranges are:						 
							- 10.0.0.0 to 10.255.255.255 (10.0.0.0/8)
							- 172.16.0.0 to 172.31.255.255 (172.16.0.0/12)
							- 192.168.0.0 to 192.168.255.255 (192.168.0.0/16)

**Netmask** : A netmask, short for network mask, is a 32-bit value used in computer networking to divide an internet protocol (IP) address into a network address and a host address.
By applying the netmask to an IP address, you can determine which part represents the network and which part represents the host.
A netmask consists of consecutive 1s followed by consecutive 0s. The 1s represent the network bits, while the 0s represent the host bits.
A netmask is commonly represented using dotted-decimal notation, where each number represents 8 bits of the netmask. For example, the netmask 255.255.255.0 is equivalent to 11111111.11111111.11111111.00000000 in binary.

**Ping** :      The ping command allows users to check their internet connection. 
		This command takes as input the [IP address](https://www.geeksforgeeks.org/what-is-an-ip-address/) or the URL and sends a data packet to the specified address with the message “PING” and gets a response from the server/host this time is recorded which is called latency.

		Synatx : ping [options] host_or_IP_address
		Eg. ping www.google.com

		**Request timed out in Ping command**  : Indicates that target is not 
			responding to ping requests.
			**Destination Host unreachable**  : indicates that there's issue in 
				in reaching the destination.

**Secure Copy (scp) :** It is used to copy files between server in a secure way.
				   The scp command or secure copy allows the secure transferring of files between the local host and the remote host or between two remote hosts.
						Syntax : scp  user@host1:source file or directory ... user@host2:destination

**wget :**  wget is the non-interactive downloader which is used to download files from the 
		server.
		Syntax : wget [option] [url] [url]

**curl :**   curl  is a command-line tool and library for transferring data with URLs.
		It supports a wide range of protocols, making it an invaluable tool for fetching, uploading, and managing data over the Internet.
			Syntax : curl [option] [ url] [ url ]
			**Handling HTTP Requests using curl command :** 
				The curl allows you to send custom http requests with various methods such as Get , Post , Put , etc. 
				eg:  curl -X GET https://api.example.com/resource
			**Downloading files using curl command :** 
				Syntax : curl -o [file_name] [ url ] [ url ]
			**Uploading files using curl command :** 
				Syntax : curl  -T file_name [ url ]

**Netstat :**   (Network statistics) It understand and check things about how your computer connects to the internet.
It can tell you about the connections your computer is making, the paths it uses to send information, and even some technical details like how many packets of data are being sent or received.
Syntax : netstat -[ options ]