A docker image behaves like a template from which consistent containers can be created . If Docker was traditional virtual machine, the image could be like iso file used to install VM. 


Container is when you run that image locally i.e executing it locally 


`docker build ` command is used to create image of any particular file 


and that image file which is created is given to any user that wants to test our code

and then we run that file using 


		docker run <img_id>

when we run that specific image using the above command then it is called container



This image is what that we send to docker hub using 

				docker push <img_id> dockerhub.com/user_name


Once that image is there we give that img to our friend or pull that image to our AWS 
this is done  using 

				docker pull <img_id>






Docker file Example : 


		Base image				`FROM node:20 

Working directory 						`WORKDIR /usr/src/app`

copy everything from this file to working directory    `COPY . .`


			RUN npm install

exposing the specific port 			`EXPOSE 3000`

All of the above will run while creating the image


			CMD ["node", "index.js"]`

The above file runs when we are running the image


Anything inside `.dockerignore` file will be ignored while copying 




The difference between **`RUN`** and **`CMD`** is that 
RUN will do its when the file is creating 
and CMD will be used to run the container or start the container




###### The next step is how to create an image from this docker file 

`docker build . -t test_app`

-t is for giving a tag to the image
. means the folder in which the source code and docker file is 

	docker run -p 3000:3000 <img_id>


this maps the port of host machine to the port of container

first 3000 is of host machine and 2nd 3000 is of container


