

### Your Docker image is over 1GB of size, and builds are slow. How would you reduce the image size ?

* Use smaller base image (eg. alpine instead of ubuntu)
* Multi-Stage builds
* Clean up unnecessary files 
* Avoid copying unnecessary files 



### A Container in Production keeps restarting every few seconds . How do you troubleshoot it ?


* Check logs : `docker logs container-id`
* Inspect the container health : `docker inspect`
* Check restart policy : maybe it's `restart=always`
* Try running the Container with an interactive shell to debug : 
		`docker run -it <image> /bin/sh`


### You updated your Dockerfile and built a new image . How do you update your service with zero downtime ?

* Use Rolling update strategies if your are using Docker swarm or kubernetes 
* With Docker Compose : 
			
			docker-compose pull
			docker-compose up -d --no-deps --build <service-name>



### How to pass database password to a container securely ?

* Use docker secrets if you are using swarm 
* Use environment variables 
* Use external secret management tools (AWS Secrets Manager ). 
* Mounts secrets as volumes and read from files . 


### Port Binding Issue : 

#### Your containerized app says it's running on port 80 , but you can't access it from the host 

- Ensure port is established : `docker run -p 8080:80`
- Confirm the app is listening on` 0.0.0.0`, not `127.0.0.1` inside container 
- User Docker inspect to check network settings 
- Test with curl `localhost:8080`


### Image Caching Problem 

#### You changed a single line in the Dockerfile , but the build still takes too long . Why ?

* Docker uses layer cache: Changing early layer invalidates later caches. 


### Persistent Data 

#### You stop and remove a container , but all uploaded user data is lost . What went wrong ?


* Data was stored in the container's ephemeral layer. 
* Solution : Use volumes : 

			docker run -v /host/path:/container/path ...


### Debugging a Hanging Container 

#### A Container runs but seems to hang and produce no output.

* Use `docker inspect -it <container> bash` to inspect it .
* Check entrypoints of CMD in Dockerfile. 




### Dockerfile not working in CI/CD

#### Your build works locally but fails in CI/CD pipeline. The error mentions "missing dependencies " or "file not found"


* Ensure all necessary files are included in the build context. 
* Check .dockerignore - it might be excluding required files. 
* Absolute vs Relative paths : CI might run in a different working directory. 


### Inter Container Communication

#### Your app container can't reach the database container by hostname. Both are in docker compose. 


* Make sure both containers are on the same user-defined network(Docker compose does this automatically. )
* Use the docker compose from `docker-compose.yml` as the hostname. 
* Check the port mismatches and container health status. 



### Volume not persisting Data

#### You are using a volume to persist data , but everytime the container restarts ,the data disappears. 

* Make sure you are using matched volumes , not anonymous ones: 
		
			docker run -v myvolume:/data ...


### Continues Deployment with Docker 



* Setup CI/CD pipeline : 
	* Build docker image (docker build )
	* Push to registry (docker push )
	* Deploy via docker-compose pull && up -d  or via kubernetes 
* Tag images properly 
* Use webhooks or Github Actions/GitLab CI. 



### Preventing root access

You security team requires container to not run as root . How do you comply ?

In Dockerfile : 

RUN adduser --disabled-password myuser
USER myuser

Avoid USER root


### Cleaning up disk space

##### The disk is full due to Docker usage. How do you clean it ?

*  Remove unused images : 

			docker system prune -a 

* Remove unused volumes:

			docker volume prune
		



### How to check resource usage of running containers in Docker


`docker stats ` command is used to monitor the resource usage of running Docker Containers in real-time. 


