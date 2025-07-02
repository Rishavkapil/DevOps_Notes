


## **Taints :**

In Kubernetes, a "Taint" is a key value pair associated with a node that marks the node to repel certain pods. Taints are used to influence the scheduling decisions made by the kubernetes scheduler. When a node is tainted, only pods with matching tolerations can be scheduled onto that node. 

**Key & Lock Formula :** 

Lets use an analogy of key and lock for a house to explain taints and tolerations in Kubernetes. 


Imagine you have a house(which represents a kubernetes node ), and you want to control who an enter and use it.  In this analogy, 

1. **Taints:** Taints act like lock on your house's doors. You can install different types of locks on each door to restrict access. For example, you might have a door that requires a specific key or code to open. Similarly in Kubernetes, taints are applied to nodes to restrict which pods can be scheduled on them. Each taint has a key (the taint itself) that prevent pods without the corresponding toleration from being scheduled on the node. 


2. **Tolerations :** Toleration act like keys that allow certain pods to bypass the locks(taints) and enter the house(node) . When you have a key that matches the lock on the door, you can enter the house without any issues. Similarly, in Kubernetes, pods can specify tolerations that match the taints on nodes. These tolerations act as keys that allow the pods to be scheduled on node despite the taints. 


so in summary, 

* Taints are like locks on the door of your house, restricting access to certain pods(visitors)
* Tolerations are like keys that pods(visitors) can carry to bypass the locks (taints) and be scheduled on nodes. 



**Taint key Concept** 

**Taint Effect :** Determines how the taint affects pod scheduling on the node. 

* **No Schedule:** Pods will not be scheduled onto the tainted node unless they have a matching tolerations. 
* **PreferNoSchedule:** Scheduler tries to avoid scheduling pods onto the tainted node but can do so if necessary. 
* **NoExecute:** Existing pods on the node without matching tolerations are evicted. 


**Taint Syntax :** 

```
kubectl taint nodes <node_name> key1=value1:<taint-effect>
```



A taint is defined with three components : 

* **Key :** The key of the taint to tolerate. 
* **Value :** The value of taint to tolerate. 
* **Effect :** Specifies the effect of the taint to tolerate. 


```
tolerations: 
- key: "key1"
  operator: "Equal"
  value: "value1"
  effect: "NoSchedule"
```


If there is a taint on a node , any pod that comes to it will not be scheduled on that node expect some specific pods.

If you want to schedule a pod on that node , then you need to a toleration with the same value as added in taint.


**NOTE :  Taint hum Node pe lagate hai and Toleration Hum Pod Pe lagate hai.** 


**Toleration Operations :**  
* **Equal:** Requires an exact match for the taint key and value. 
* **Exists:** Requires only presence of taint key, irrespective of its value. 
* **Exists with an effect :** Requires only the presence of taint with a specific effect, irrespective of its key and value. 

**Example**

In this example, the NGINX pod has toleartion that matches the taint with `nginx-node=true` and `NoSchedule` effect, allowing it to be scheduled on nodes with that taint. 

Lets first add a taint to a node using the below command , 

```
kubectl taint nodes <node_name> nginx-node=true:NoSchedule
```


with the above command the node is tainted with `nginx-node=true:NoSchedule`. 
Now lets create nginx pod without any toleration and see if it is scheduled on any node or not. 

**nginx-pod.yaml**

```
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
  - name: nginx
    image: nginx
```


When you try to create this pod in your kubernetes cluster, it won't be placed on the target node and it will be in `pending` state since we have added taint to the worker node. 


```
kubectl apply -f nginx-pod.yaml
```

It won't be scheduled and it will be in pending state, 
Now modify the nginx pod manifest by adding tolerations to it same as below : 


```
apiVersion: v1
kind: Pod
metadata: 
  name: nginx
spec: 
  containers:
  - name: nginx
    image: nignx
  tolerations: 
  - key: "nginx-node"
    operator: "Equal"
    value: "true"
    effect: "NoSchedule"
```



Now lets apply the above manifest file and see if it is scheduled on target node. 


```
 kubectl apply -f nginx-pod.yaml 
```





#### Use Cases and Best Practices

1. **Isolating Critical Workloads :** Taint Critical Nodes and add tolerations to critical pods to ensure they run only on these nodes. 


2. **Dedicated Nodes for specialized Tasks :** Taint Nodes with hardware accelerators or specialized hardware and add tolerations to pods requiring those resources. 

w
1. **Node Maintenance :** Use taints to gracefully evacuate nodes for maintenance by tainting them with "NoExecute" effect and add tolerations to workload pods to allow them to drain safely. 