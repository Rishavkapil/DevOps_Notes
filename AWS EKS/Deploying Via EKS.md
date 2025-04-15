
![[Pasted image 20250415110033.png]]



when you want to deploy the website using EKS , 

the pod is deployed inside the worker node. 
and there is ingress resource which runs the pod
user can not directly access the pod , So there is ingress for it

Now user still can't access the worker node , so there is need for ingress controller.

Ingress controller will watch for the ingress resource and it will create the ALB for you . 

