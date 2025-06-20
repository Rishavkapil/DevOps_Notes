
Kubernetes networking is a fundamental concept that enables communication between different parts of a kubernetes cluster, including containers, pods, services, nodes and external clients. 


### Key Concepts of Kubernetes Networking 

1. **Kubernetes Networking Model :**
		Each Pod in Kubernets cluster gets its own unique cluster-wide IP address, enabling direct communication between pods without the need for Network address Translation(NAT) or port mapping. This means pods can communicate with each other using their IP addresses regardless of which node they are on. 

	container within the same pod share the same network namespace, which allows them to communicate over localhost easily without additional networking setup.



2. **Types of Communication in Kubernetes Networking :** 

* **Container to Container Communication :** Containers within the same pod communicates over localhost because they share the same network namespace. 