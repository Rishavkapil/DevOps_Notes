	NGINX is an open-source web server , reverse proxying , load balancing media streaming, HTTP  cache etc. 

## What is reverse Proxy ?
A reverse proxy is used to provide load balancing services .
**Reverse proxy** also hides the identity of server .
**Forward proxy**  hides the identity of client.
In networking and web traffic , proxy is a device or server that acts on behalf of other devices. It sits between two entities and performs a service . 
Same way we user proxy in classes like we ask friends to mark our attandance.

Typically reverse proxy server sits in front of the web servers and forwards clients requests to those web servers.

### Difference between Load Balancer and Reverse Proxy 
A **Load balancer** distributes incomming client requests to a group of servers to ensure statisfactory speed and optimized functioning . Load Balancer and mostly deployed when a site needs multiple servers because the volume request is too large 
A **Reverse Proxy** accepts requests from client and sends it to a server.







## How does NGINX Work 

When we interact with any webpage we don't directly communicate with the servers but we communicate with NGINX server and then that communicates with the servers of web page.

Client send request to NGINX server and then NGINX server decides which particular server to interact with and then that server replies back to client through NGINX server.



NGINX is built to offer low memory usage and high concurrency. Rather than creating a new process for each web request, NGINX uses a asynchronous event-driven approach where requests are handled within single thread.

With nginx one master process can control multiple worker process.


![[Pasted image 20250127112156.png]]



#### Routing Pathways
Routing pathways in linux manage how data packets are directed from one network to another.



**Methods of doing this ->**

We have to first install nginx server in our machine using 

		sudo apt install nginx -y

After installing server, we need to make changes in ``/etc/nginx/sites-enabled/default 

``` server{
		listen 80; // this will make nginx server run on port 80
		listen [::]:80;  // this ensures that server will recieve traffic from both ipv4 and ipv6 
		root /var/www/html/nginx-server/; // this is the path to the file 
		index index.html; //file which you want to run 
		server_name _; // server will run by default on localhost 
		location /{
			try_files $uri $uri/ =404;
		}
}
```

- **`location /`**: This tells Nginx to apply this block for any requests that match the root directory (`/`) of the server. Essentially, it handles requests to the main URL or any subpath.
    
- **`try_files $uri $uri/ =404;`**:
    
    - **`$uri`**: This represents the URI (or path) that the client is requesting.
    - **`$uri/`**: This checks if the request corresponds to a directory (by appending a trailing slash).
    - **`=404`**: If neither `$uri` nor `$uri/` exists, Nginx will return a 404 error (file not found).

### What this does:

- When a request comes in, Nginx will first check if a file or directory exists at the given `$uri` (the requested path).
    - If the requested file exists, Nginx will serve it.
    - If the requested path is a directory (and the request doesn't include a trailing slash), it will try the path with a trailing slash (to redirect to the directory).
    - If neither exists, Nginx will return a `404 Not Found` error.




Then we have to create files that we want to run inside the path that we have specified in the default file

if we want to host a website on nginx server , Then we first need to create that file or directory which we want to run
	for example here we have specified path which is 
		`` /var/www/html/nginx-server
	Lets say we want to make file new file named mainsite 
	then first we need to make a new directory named mainsite.com or mainsite (we have to mention this in nginx config file too)
			`` sudo mkdir mainsite.com
				`` sudo touch index.html
				`` sudo vim index.html 
		then add content in this file
	then we need to make a conf file for this in `` /etc/nginx/sites-enabled/
	we will create file like what i did was `` sudo touch mainsite
		then we need to make the server config. for this file 
		```
```
	server{
			listen 80;
				server_name mainsite.com;
				root /var/www/html/nginx-server/
				index index.html;
				location{
					try_files $uri $uri/ = 404;
				}
	}

```

#### How to do load balancing in nginx 

1.  Run different pages on different ports
2. Add servers in default file
```
				upstream boxes{
        server 127.0.0.1:81;
        server 127.0.0.1:82;
        server 127.0.0.1:80;
}
```

3. In servers of different ports , in location add
			` proxy_pass http://nameofupstream`




