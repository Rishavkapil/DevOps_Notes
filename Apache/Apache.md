Apache 2 is a widely used open-source web server software. 

Apache is one of the component that is needed in a web application stack to deliver web content. 

#### Features of Apache web servers :
- Handling Static files
- Loadable dynamic modules
- Auto-Indexing
- Supports HTTP
- FTP connections
- Load Balancing  
- Session Tracking 


###### HTTPD
HTTP deamon is a software/program that runs in the background of a web server and waits for the incoming server requests. 
The deamon answers the requests automatically and serves the hypertext and multimedia documents over the internet using HTTP.



#### What is the difference between Apache and NGINX
- **APACHE** uses process driven model , means it creates a new process or thread for each request, while **NGINX** uses an event-driven, asynchronous architecture which is more efficient in handling high concurrency.

- **NGINX** is better suited for static content and high trafic websites while **APACHE** is ideal for environments requiring extensive customization and dynamic content handling. 

- While **NGINX** handles static content and act as reverse proxy , while **APACHE** handles dynamic content. 




**Methods to host a website on apache 2 sever : )**


First we need to install apache2 on the host machine
	it is done using `` sudo install apache2 -y

run the apache server if not running or running nginx file again even it is closed then it may be due to the path or file which is same as in the nginx default file 

	then we have to create new directory in /var/www/html/
		sudo mkdir apache-server
then we again need to create index.html file for this directory for using apache server

	then we need to add content in this index.html file

then we have to change the path in ``/etc/apache2/sites-enabled/default 
nd have to do 

	```<VirtualHost *:8080>
	ServerAdmin webmaster@localhost
	DocumentRoot /var/www/html/apache-server (this is the path to the file which we want to run)
			ErrorLog ${APACHE_LOG_DIR}/error.log
			CustomLog ${APACHE_LOG_DIR}/access.log combined
		</VirtualHost>


By doing this , a simple index.html should be running by now. 
To check , go to browser and hit ``localhost:8080 
you should be able to see the content written in index.html file

To run other website follow same steps as done in NGINX  server.


