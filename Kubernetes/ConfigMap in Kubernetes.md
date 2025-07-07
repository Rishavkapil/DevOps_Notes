

A ConfigMap is an api object used to store non-confidential data in key-value pairs. Pods can consume configMaps as environment variables, command-line arguments, or as configuration files in a volume. 

A ConfigMap allows you to decouple environment-specific configuration from your container images, so that your applications are easily portable. 


NOTE : ConfigMap does not provide secrecy or encryption. If the data you want to store in confidential , then use a Secret rather than configMap



### ConfigMap Object 

A ConfigMap is an api object that lets you store configuration for other objects to use. Unlike most kubernetes objects that have a spec, a 



There are two ways by which we can create the config map, 

1. Imperative way 
2. Declarative way 


**Imperative way :** We pass the keys and values line by line not in a file ,


```
kubectl create cm --from-literal=<key>=<value>
```



**Declerative way :** 

In this way, we create a seperate kubernetes object of configMap and then pass it to the pod or deployment. 

eg. 

```
apiVersion: v1
data:
  firstname: rishav
  lastname: kapil
kind: ConfigMap
metadata:
  creationTimestamp: null
  name: app-cm
  namespace: rishav-ns

```

Now to include this in pod , we need to add the following inside the configuration: 


```
apiVersion: v1
kind: Pod
metadata:
  name: mypod
  namespace: rishav-ns
spec:
  containers:
  - name: mycontainer
    image: nginx
    ports:
    - containerPort: 80
    envFrom:
    - configMapRef:
        name: app-cm

```



we add `envFrom` inside the container specification , this will include all the variables that are inside the `app-cm` configMap. 
