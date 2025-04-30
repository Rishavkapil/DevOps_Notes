	

***Docker image se hum containers bnate h :)***



A docker image behaves like a template from which consistent containers can be created . If Docker was traditional virtual machine, the image could be like iso file used to install VM. 


Container is when you run that image locally i.e executing it locally 



Docker file Example : 


		Base image				`FROM node:20 


**Base img is a starting point for building a Docker image. It is a foundational environment upon which you can add your application code , dependencies and configurations.**

	

Working directory 						`WORKDIR /usr/src/app`

copy everything from this file to working directory    `COPY . .`

this **first 'dot' represents the source file on your local machine i.e current directory** 
and **the second 'dot' represents the destination directory**


			RUN npm install

exposing the specific port 			`EXPOSE 3000`

All of the above will run while creating the image


			CMD ["node", "index.js"]`      represents what command to run when the container is running

The above file runs when we are running the image


Anything inside `.dockerignore` file will be ignored while copying 




The difference between **`RUN`** and **`CMD`** is that 
RUN will do its part when the file is creating 
and CMD will be used to run the container or start the container




###### The next step is how to create an image from this docker file 

`docker build . -t test_app`

-t is for giving a tag to the image
**.**  means the folder in which the source code and docker file is 

	docker run -p 3000:3000 <img_id>


this maps the port of host machine to the port of container

first 3000 is of host machine and 2nd 3000 is of container





##### **build vs run**

**docker build lets you create an image**
**docker run lets you create a container**



#### Problem with docker build again command



when we hit docker build again command 

the docker will store the base image that was fetched previously in its cache so that now it should take less time to execute. 

so the problem here is if only index.js file is changed then after the layer 3 i.e COPY . .
not even a single thing will be cached . 

but the next layer which is RUN npm install is very time consuming and in most cases it is same as previous so it needs to be cached. 




**To  do this we need to copy the all the packages files**


COPY package*.json ./
 
RUN npm install



##### To make this docker image smaller in size 

we need to make use of alpine as a base image 
alpine is light-weight variant 

**`eg. FROM node:20-alpine`**






		


