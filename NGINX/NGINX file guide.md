
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

Once the master process receives the signal to reload configuration, it checks the syntax validity of the new configuration file and tries to apply the configuration provided in it. If this is a success , the master process starts new worker processes 
