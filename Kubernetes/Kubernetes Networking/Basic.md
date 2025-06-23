- Kubernetes Networking addresses four concers : 

- Containers within a pod use network to communicate via loopback. 

- Cluster Network provides communication between different pods. 

- The service resource lets you expose an application running in a pod to be reachable from outside you cluster.


- You can also use services to publish services only for consumption inside your cluster. 


- Container to Container communication on the same pod happens through localhost within container.



The contaiumairmd385ner running in any kubernetes cluster does not have its own ip , it uses the Ip of the pod. So if there are multiple containers running on the same pod , they will communicate via localhost and will serve on different ports on same ip 