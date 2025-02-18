



#### What is Docker Compose 

Docker compose is a tool for defining and running multi-container Docker applications.
It automates the process of managing several docker containers


with compose you use a YAML file to configure  your application's services. Then with a single command, you create and start all the services from your configurations. 

![[Pasted image 20250213153625.png]]

To run the docker compose file 
we do 

			docker compose up



All containers are already connected via network and can be referenced by their name. 




![[Pasted image 20250213155045.png]]


if i would have to run this container manually i would have to do 

	docker run -p 27017:27017 -v mongodb-data:/data/db mongo
