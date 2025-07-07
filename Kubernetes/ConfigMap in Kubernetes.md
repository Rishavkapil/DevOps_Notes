

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

### CreateContainerError, CreateContainerConfigError in K8s

`CreateContainerConfigError` indicates an issue when transitioning a container from a pending state to running state, typically due to incorrect or incomplete yaml files. This error frequently arises from missing or misconfigured essentials like ConfigMaps or Secrets. Additionally, factors such as improper image specifications or insufficient resources can also lead to this error. 


**Causes and Resolution of above errors :** 

**Diagnosis :** 

Like CreateContainerConfigError, CreateContainerError occurs when container is transitioning from pending to running state. You can identify it by running the `kubectl get pods` command and looking at the pod status . 

*Common Causes :* 

The following table summarizes the main causes of the errors and how to resolve them. Most of them are related to yaml configuration errors. 


| Cause                                                                                   | Resolution                                                                                           |
| --------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| ConfigMap is missing                                                                    | Identify the missing configmap and create it in the namespace, or mount another, existing configMap. |
| Secret is missing - a secret is used to store sensitive information such as credentials | Identify the missing secrets and create it in the namespace, or mount another, existing Secret.      |


**Resolution:** 
* You need to understand whether a ConfigMap or Secret is missing . Run the `kubectl describe` and look for a message indicating one of these conditions, such as 

```
kubectl describe pod pod-missing-config
Warning  Failed   34s (x6 over 1m45s)    
kubelet   Error: configmap "configmap-3" not found
```

*  If the command returns null, the ConfigMap or Secret is indeed missing, Follow thee instructions to create the missing object mounted by the failed container.  Create ConfigMap or Create Secret. 

* Run the `get configMap or get Secret` command to again verify that the object now exists. Once the object exists, the failed container should be successfully started within a few minutes. 
* Once you verify that the ConfigMap exists, run `kubectl get pods` to again verify that the pod status is `running`


### CreateContainerError (incorrect image specification or runtime error) 




| Causes                                                                                                             | Resolution                                                           |
| ------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------- |
| Incorrect Image specification- both image and pod specification do not have a valid command to start the container | Add a valid command to start the container                           |
| Runtime Error : Container experienced an error while starting                                                      | Identify the error and modify the image specification to resolve it. |
| Insufficient Resources - Container Runtime did not clean the previous containers.                                  | Retrieve kubelet logs and resolve or reinstall the node.             |


### Diagnosis and Resolution

Follow these steps to diagnose the cause of the `CreateContainerError` and resolve it.


**Step 1 : Gather Information**

Run `kubectl describe pod <name>` and save the content to a text file for future reference. 


```
kubectl describe pod [name] /tmp/troubleshooting_describe_pod.txt
```

**Step 2 : Examine Pod Events output**

Check the event section of the describe pod text file, and look for one of the following messages : 


- `no command specified `
- `starting container process caused`
- `container name[. . . ] is already in use by container`
- `is waiting to start`

**Step 3 : Troubleshoot**

If the error is `no command specified`: 

- This means that both image configuration and pod configuration did not specify which command to run the container. 
- Edit the image and pod configuration and add a valid command to start the container. 


If the Error is `starting container process caused` : 

- Look at the words following the container process caused message - this shows the error that occurred on the container when it was started. 
- Identify the error and modify the image or the container start command to resolve it. 

For example, if the error on the container was executable not found, identify where that executable file is called in the image specification, and ensure that file exists in the image and  is called using the correct path and name

If the Error is `container name[. . . ] is already in use by container` : 

- This means the container runtime did not clean up an older container under the same name. 
- Sign in with the root access on the node and open the kubelet log - usually located at `/var/log/kubelet.log .`

- Identify the issue in the kubelet log and resolve it - often this will involve reinstalling the container runtime or the kubelet, and re-registering the node with the cluster. 



If the `Error is waiting to start` 

- This means that an object mounted by the container is missing. Assuming you already checked for a  missing ConfigMap or Secret, there could be a storage volume or object required by the container. 

- Review the pod manifest and check all the objects mounted by the pod or the container, and verify that they are available in the same namespace. If not, create them, or change the manifest to point to an available object. 


