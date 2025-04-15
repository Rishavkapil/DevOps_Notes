Environment variables  are used to store app secrets and configuration data, which are retrieved by running app when needed. 


Environment variables add dynamicity to your static code base


![[Pasted image 20250213113907.png]]




we don't want to change url again and again as it makes the entire process very complex. 
So we replace the url with environment variable 
like here we used

		process.env.MONGO_URI





![[Pasted image 20250213114206.png]]



So now to run this docker file using environment variable we have to do 


		docker run -p 3000:3000 -e MONGO_URI=url_of_your_db <img_tag>





Now **why this is usefull ?**


all our secrets should not be hard coded 