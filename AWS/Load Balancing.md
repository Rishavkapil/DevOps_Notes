
#### What is load balancing

Load Balancers are the servers that forward the internet traffic to multiple server



![[Pasted image 20250220105718.png]]


### Why use a load Balancer 

*  Spreads load across multiple downstream instances. 
* Seamlessly handle failures of downstream instances. 
* Do regular health checks to your instances. 
* Provides SSL termination( HTTPS ) for your websites. 


#### Why use an elastic load balancer

An ELB (Elastic Load Balancer ) is a managed load balancer 
		AWS guarantees that it will be working 

It costs less to setup your own load balancer but it will a lot more effort on your end 



##### 4 types of load balancers offered by AWS
* Application Load Balancer (HTTP /HTTPS  only ) - Layer 7
* Network Load Balancer (ultra-high performace , allows for TCP ) - Layer 4
* Gateway Load balancer  - Layer 3
* Classic Load Balancer -  Layer 4 and 7



![[Pasted image 20250220111814.png]]





**Target Group is the group of instances that we have created .** 


