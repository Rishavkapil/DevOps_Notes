

Context are way to define the docker daemon you're interacting with. 

Each context contains all the information required to manage resources on the daemon. The `docker context` command makes it easy to configure these contexts and switch between them. 

syntax : 

		docker context create <context_name>



to switch to other context : 

	docker context use <context_name>


to delete any context , first make sure that you are not in the context that you want to delete

	docker context rm <context_name>





## How do they work 

Each context contains : 

* `DOCKER_HOST` (IP/SSH connection)
* TLS cert details(if remote)
* Orchestrator(eg. swarn or kkubernetes)
* Additional metadata. 

When you switch context, docker cli starts pointing to that engine. 

eg. 


```
docker context use prod-server
```

Now every command you run : 

```
docker ps
docker run 
docker logs
docker build
```

is executed on the remote docker engine, not your laptop. 



## Where are the config files of context

All the Docker context configuration files are present  in :

```
~/.docker/contexts
```

