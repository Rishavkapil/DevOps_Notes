
Container network refers to the ability for containers to connect to and communicate with each other. 
Containers have networking enabled by default , and they can make outgoing connections. A container has no information about what kind of network it is attached to , or whether their peers are also docker workloads or not . 

A container only sees interface with an IP address, a gateway , a routing table , DNS service and other networking details. 

#### User defined networks 

You can create custom , user define networks and connect multiple containers to the same network. Once connected to a user defined network , containers can communicate with each other using container IP addresses or container names. 

The following example creates a network using bridge network driver and running a container in the created Network . 

		
		docker network create -d bridge my-net
		docker run --network=my-net -itd  --name=container1 busybox



##### Drivers 
The following network drivers are available by default and provide core network functionality. 

| Driver    | Description                                                              |
| --------- | ------------------------------------------------------------------------ |
| `bridge`  | The default network driver.                                              |
| `host`    | Remove network isolation between the container and the Docker host.      |
| `none`    | Completely isolate a container from the host and other containers.       |
| `overlay` | Overlay networks connect multiple Docker daemons together.               |
| `ipvlan`  | IPvlan networks provide full control over both IPv4 and IPv6 addressing. |
| `macvlan` | Assign a MAC address to a container.                                     |



#### Connecting to multiple networks 

A container can be connected to multiple networks. 

For example, a frontend container may be connected to a bridge network for external access, and --internal network to communicate with containers running backend services that do need external network access. 

A container may be connected to different type of network . For example , ipvlan network to provide internal access, and bridge network for access to local services. 

