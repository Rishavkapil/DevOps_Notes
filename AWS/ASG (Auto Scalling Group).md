
Suppose we have created a Load Balancer to distribute traffic over multiple servers. 

How do we create these servers automatically in the backend , for this we use auto scaling group. 

* In real life , load on your website can change over time 


**The goal of auto scaling group is to :** 
* Scale out (add ec2 instaces) to match an increase load.
* Scale in (remove ec2 instances) to match a decrease load.
* Ensure we have a minimum and maximum number of machines running.
* Automatically register new instances to a load balancer.
* Replace unhealthy instances


* **Cost Saving :**  Only run at optimal capacity

![[Pasted image 20250220124126.png]]




### Hands on of ASG 

First we need to create a ASG (Auto Scaling group )

Then we need to create a launch template( if not created ) and this template is used to tell ASG , how to create ec2 instances within it.
