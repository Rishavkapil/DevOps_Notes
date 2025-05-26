
When the docker compose runs a container , it uses two elements , **ENTRYPOINT and COMMAND** , to manage what happens when the container starts or stops. 

However it can sometimes be easier to handle these tasks separately with lifeCycle hooks - command that runs after the container starts or just before it stops. 

Life cycle hooks are particularly useful because they have some special privileges (like running as a root user) 

There are mainly two types of hooks : 

 Post start hooks                  Pre stop hooks

**Post Start Hooks :** 
	These hooks are commands that run after the container is started , but there's no time set for when they will exactly execute. 

eg. 

```yaml
services:
  app:
    image: backend
    user: 1001
    volumes:
      - data:/data    
    post_start:
      - command: chown -R /data 1001:1001
        user: root

volumes:
  data: {} # a Docker volume is created with root ownership
```

**Pre Stop Hooks :**  
	Pre stop hooks are the  commands that run before the container is stopped by a specific command like (docker compose down or stopping it manually ) . These hooks won't run if the container stops by itself or gets killed suddenly. 


```yaml
services:
  app:
    image: backend
    pre_stop:
      - command: ./data_flush.sh
```


