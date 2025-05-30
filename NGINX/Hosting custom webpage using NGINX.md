

1. Install the Nginx if not present using 

			sudo apt install nginx

2. Create the custom file in whatever directory you want and then give permissions to that file . 
like this 


		chmod o+x /home /home/user /home/user/work-per /home/user/work-per/nginx-server-down-page
  sudo chmod o+x /home /home/user /home/user/work-per /home/user/work-per/nginx-server-down-page


3. Then add it to the config file of nginx . eg. you can add it in 

		/etc/nginx/nginx.conf


```sh
events{}
http{
	server{
		listen 80;
		root <path_to_your_file>
		index index.html
	}
}
```


then check for errors using

	nginx -t

then reload the nginx service

	nginx -s reload


then visit localhost on your browse or try to curl localhost



###  How to navitage to differne page whenever 404 comes



To do that , you need to create separate file in the same directory in which index.html is placed ,
then in config file of nginx add


	error_page 404 /<error_file_name>


Now when you try to hit the wrong path in localhost , it will serve the content of error's page 


