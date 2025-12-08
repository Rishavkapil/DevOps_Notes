
Namespaces are linux kernel feature that Docker uses to create and manage containers. 

Namespace is a linux kernel feature that isolates a set of system resources , so processes in one namespace cannot see or affect resources in another namespace. 

| Namespace | Isolates           | Example                                   |
| --------- | ------------------ | ----------------------------------------- |
| PID       | Process IDs        | Container sees PID 1 as first process     |
| NET       | Network Interfaces | Each Container gets its own network stack |
|           |                    |                                           |
## How do namespaces work in Docker?

When you run : 

```
docker run nignx
```
Docker : 
* Creates a new process(using clone()) system call.
* The new process is placed into new namespace: 
	* new PID namespace
	* new Network namespace
	* new Mount namespace
* Inside the container, processes see : 
	* only their own process
	* their own filesystem
	* their own hostname

***NOTE : A container is just a process with isolation applied via namespace.*** 

