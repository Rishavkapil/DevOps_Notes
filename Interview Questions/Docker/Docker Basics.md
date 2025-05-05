

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

* Docker uses layer cache
