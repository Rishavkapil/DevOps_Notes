



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



## Creating custom network for two docker compose files



	docker network create my-custom-network


then in docker compose file , we need to attach that network to the service 


like if we are creating mysql service , then our compose file will be something like : 

			version: '3.8'
			
			services:
			  mysql_db:
			    container_name: mysql_database_cnt
			    image: mysql:8.0.35
			    ports:
			      - "3306:3306"
			    environment:
			      MYSQL_ROOT_PASSWORD: "root"
			      MYSQL_USER: "rishav"
			      MYSQL_PASSWORD: "rishavuser"
			    restart: always
			    volumes:
			      - ./mysql-data:/var/lib/mysql
			      - ./my.cnf:/etc/my.cnf
			    networks:
			      - my-custom-network
			
			networks:
			  my-custom-network:
			    external: true // this is if we have already created a custom network






