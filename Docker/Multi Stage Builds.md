##### **node and nodemon** 

when we run using nodemon , it watches our index.js file 

after we make any change in index.js file it automatically restarts 

## What are multi Stage builds 

Multi staged builds in docker allows developers to split the build process into multiple stages within single docker file.


**what if we want to allow the dev backend to hot reload ? but not the production environment ?**


thats when we need **multi staged builds**



![[Pasted image 20250213123226.png]]



Here we are creating 3 images 
image no.2  and image no. 3 will use image no. 1 as the base image




![[Pasted image 20250213124207.png]]





