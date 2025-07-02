

When you create a pod , you can set environment variables for containers that run in the Pod. To Set environment variables, include the env and envFrom field in the configuration file. 

The env and envFrom fields have different effects. 

**env :** 

allows you to set environment variables for a container, specifying a value  directly for each variable you name.


**envFrom:** 

allows you to set environment variables for a container by referencing either a configMap or secret . When you use envFrom , all the key-value pairs that are stored in the configMap or Secret are set as environment variables for container. You can also specifiy a common prefix string. 

**Example :** 


***pod.yaml***

```
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec: 
  containers:
  - name: my-container
    image: ubuntu
    ports:
    - containerPort: 80
    env:
    - name: DEMO
      value: "This is the value of DEMO environment variable"
```


