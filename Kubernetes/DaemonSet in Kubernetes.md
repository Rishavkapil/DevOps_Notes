
DaemonSet is just like deployment, but it creates replicas on each of the present node, for example if a new node is added into the cluster , it will create a replica of pod on that node also , and if that node is deleted its replica will also be deleted. 



A daemonSet defines pods that provide node-local facilities. These might be fundamental to the operation of your cluster, such as networking helper tool, or be part of an add-on. 


A daemonSet ensures that all nodes run a copy of Node. As Nodes are added on the cluster, pods are added on them. As Nodes are removed from the cluster , those pods are garbage collected. Deleting a daemonSet will clean up the pods it created. 

Some typical uses of daemonsets are : 
* Running a cluster storage daemon on every node.
* Running a logs collection daemon on every node. 
* Running a node monitoring daemon on every node. 


In a simple case, One DaemonSet, covering all nodes, would be used for each type of daemon. A more complex setup might use multiple daemonsets for a single type of daemon, but with different flags or different memory and cpu requests for different hardware types. 



### Writting daemonSet spec

Create a daemonSet 


You can describe a daemonset in a yaml file .

For example, daemonset.yaml, the file below describes a DaemonSet that runs fluentd-elasticsearch Docker image. 



```
apiVersion: apps/v1
kind: DaemonSet
metadata: 
  name: nginx-deploy
  labels:
    env: demo
spec:
  template: 
    metadata:
      labels:
        env: demo
      name: nginx
    spec: 
      containers:
      
```