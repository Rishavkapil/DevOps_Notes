Lamp stands for Linux , Apache , Mysql and php , which are open-source software components used together to create  web development enviroment.
 Here, Linux is used as an operating system , Apache is used as a web server , Mysql is used as  database and php/python is used for scripting.
 


![[Pasted image 20250129114532.png]]



#### How does Lamp Stack Work

The four stack components allow developers to host, serve, and manage web-based content. The process looks like this:
1. A user enters a URL in their [browser](https://phoenixnap.com/glossary/web-browser-definition) to request a webpage.

2. The request reaches the Apache web server on the Linux server.

3. Apache serves static content files directly to the browser.

4. If the user's browser requests dynamic content, Apache passes the request to PHP.

5. PHP executes the necessary scripts and fetches or updates data in the MySQL database.
6. PHP sends the generated HTML to Apache.

7. Apache delivers HTML content to the user's browser. The browser renders the HTML and displays the content to the user
![[Pasted image 20250129114815.png]]





In Lamp stack , we just need to automate all the tasks that we have done in previous like installing apache2 , mysql , phpmyadmin etc.

First, we need to make a script file 
			like myscript.sh
			then we have to write script in it and then we have to make that file executable by  `sudo chmod +x myscript.sh`
		After that now we need to execute the script 
		by  `./myscript.sh`

A script always start with 
				`#!/bin/bash`
		