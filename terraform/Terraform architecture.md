

The main components of the terraform includes **Core** and **Plugins** 

![[Pasted image 20250430152000.png]]

Terraform core manages the life cycle of infrastructure, evaluating the current state against the desired configuration and proposing a plan for adding or removing infrastructure components. 


![[Pasted image 20250430152645.png]]


Terraform plugins include providers and provisioners , which allow teraform core to communicate with the infrastructure hosts or SaaS providers via remote procedure calls(RPC). 

Terraform core doesn't know how to talk to AWS, Azure , Google cloud or other services , To solve that terraform uses plugins 

There are two main types of plugins  : 

- **Providers :** These help terraform to talk to cloud services like AWS, Azure, Google cloud etc. 
- **Provisioners :** These help terraform run scripts or commands on a server after it's been created. 


