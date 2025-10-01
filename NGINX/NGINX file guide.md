
Nginx has one master and several worker processes. The main purpose of master process is to read and evaluate configuration, and maintain worker processes. Worker processes do actual processing of requests. NGINX employs event-based model and OS-dependent mechanisms to efficiently distribute requests among worker processes. 

The number of worker processes is defined in the configuration file and may be fixed for a given configuration or automatically adjusted to the number of available CPU cores.

The way nginx and its modules work is determined in the configuration file. By default configuration file is named `nginx.conf`  and placed in the directory /usr/local/nginx/conf, or /etc/nginx or /usr/local/etc/nginx


### Starting , Stopping and Reloading configuration

To start nginx, run the executable file. Once nginx is started , it can be controlled by invoking the executable with -s parameter. Use the following syntax : 

```
nginx -s "signal"
```
where signal may be one of the following : 

* stop - fast shutdown 
* quit - graceful shutdown 
* reload - reloading the configuration file 
* reopen - reopening the log files 

Changes made in the configuration file will not be applied until the command to reload the configuration is sent to nginx or it is restarted. To reload Configuration , execute : 

```
nginx -s reload
```

Once the master process receives the signal to reload configuration, it checks the syntax validity of the new configuration file and tries to apply the configuration provided in it. If this is a success , the master process starts new worker processes  and sends message to the old worker process requesting them to shutdown. Otherwise the master process  rolls back the changes and continues to work with the old configurations 

A signal may also be sent to the nginx processes with the help of UNIX tools such as the kill utility. In this case, the signal is sent directly to a process with given process ID. The process ID of the NGINX master process . The process ID of the nginx master process is written, by default to the `nginx.pid` in the directory /usr/local/nginx/logs or /var/run . For example , if the master process ID is 1628 , to send the QUIT signal resulting in graceful shutdown 

```
kill -s QUIT 1628
```

For getting the list of all running nginx processes, the `ps` utility may be used, for example, in the following way:

```
ps -ax | grep nginx
```


### Directives in NIGNX 

In NGINX, directives are instructions that are used to configure the web server. They are typically specified in the nginx.conf configuration file, located in the /etc/nginx directory. 

Directives are typically organized into blocks. For example, a server block is used to specify settings for a specific server, and a location block is used to specify setting for a specific URL path. 
## Configuration file's structure 

NGINX consist of modules which are controlled by directives specified in the configuration file. 
Directives are divided into simple directives and block directives. 

A Simple directive consist of name and paramtres seperated by spaces and ends with a semicolon(;) .

A block directive has the same structure

