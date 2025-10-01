Komodo is a web app to provide structure for managing your servers, builds, deployment,and automated procedures. 

With komodo you can: 

*  Connect all your servers, alert on CPU usage, memory usage and disk usage and connect to shell sessions 
* Create , start , stop , and restart  docker containers on the connected servers , view their status and logs and connect to container shell. 
* Docker compose stacks. The file can be defined in UI, or in a git repo, with auto deploy on git push. 
* Manage repositories on connected servers, which 



## Stack in komodo

Think of stack like a project or application bundle. 

* Its basically a set of services defined together(via Docker compose or komodo config). 
* Example: 
	* A wordpress stack might  have 
		* Wordpress(Container)
		* MYSQL (container)
		* PHPmyadmin(Container)
All these run as one unit (the stack)
So , our apache stack is a single service stack. (just apache)



## Resources 
- Think of this as the inventory of everything running or available. 
- Shows you all containers , images, volumes and networks across servers. 
- Good for quickly checking "What do i have right now"

## Containers 

* A focused view just for running containers . 
* You can see logs, restart, stop or remove containers individually. 

## Servers

- List of all servers(machines/VMs ) you connected to Komodo. 
- Each server runs a Komodo agent  that listens for instructions. 
- You deploy stack/deployments onto these servers.
- You can see metrics like CPU, RAM , disk usage here. 


## Stacks

- A blueprint/project for you app- usually defined with a docker-compose file.
- Can have one service or multiple 
- Its where you paste, define your configurations. 
- Doesn't run by itself you must deploy it to a server .


## Deployments 

- A live running instance of a stack (or Build)
- Example: You have called a stack called apache-stack. 
	- When you deploy it to server-1 , is shows up under deployments 
- This tab is where you monitor/manage active workloads. 


## Builds

- This is where you create custom images. 
- Example : If you have a source code and a Dockerfile, komode can build the image for you.
- Saves built images in its registry or pushes to external repos. 
- Useful when you want to package your own app instead of pulling httpd:latest. 


## Repos 

* A place to link your github repositories. 
* If you connect GitHub, GitLab, you can trigger builds automatically when you push code. 
* This ties into build -> deployment flow(CI/CD sytle)

## Procedures

* Think of  these like scripts or recipes you can automate inside komodo. 
* Example: Restart all Apache Containers, clear logs or run DB migrations. 
* They're reusable and can be run across servers/stacks. 


## Actions

* A history/logs of whats been done in komodo. 
* Example: "Stack developed ", "Build Completed", "Server added".
* Lets you audit changes (good for debugging who did what. )


## Syncs

* Used for syncing files between your git repos and stacks
* Example : If you have a repo with your docker-compose.yaml file , Komodo can keep your Stack in sync with that repo. 
* Ensures your running environment always matches the source code. 