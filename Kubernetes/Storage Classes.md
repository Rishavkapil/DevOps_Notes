
#### What is Storage class ?

Imagine you are ordering a pizza , and you want a specific type : thin crust , extra cheese, medium size etc. . You don't make the pizza yourself - you just say what kind you want , and someone else makes it for you. 

In kubernetes, When you need storage (like hard drive) , instead of manually creating it and setting it up, you can just say : 

"Hey Kubernetes, I need storage with these settings"

You do that using something called **Storage Class**

#### What does it do ??

A **Storage class** defines : 

*  What type of storage you want (fast, slow , SSD, HDD etc. )
* Who provides it (AWS , Google Cloud , local disk etc. )
* How big it should be and some extra options. 

When you create a persistent Volume Claim (PVC)(like placing your order ), kubernetes looks at the storage class and automatically creates a volume for you  -no manual setup needed. 


##### Difference between Storage classes and PVC

Lets say you want a new chair from a furniture store : 

* **Storage Class** is like a template for what kind of chair you want (wooden , with cushions, etc). 
* **PVC**  is your actual order saying , "Hey, I want a chair using this template, and i need it now "

**The kubernetes uses the Storage class to create the PV based on your PVC .** 