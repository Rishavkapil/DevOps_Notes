

In Terraform, Backend defines where and how terraform stores its state file, which is snapshot of your infrastructure. 

This file tracks the resources terraform manages so it knows what to create , update or destroy during subsequent operations. 


#### Key Concepts : 

**Terraform Statefile** (terraform.tfstate)

Contains mapping between terraform configurations and real-world infrastructure. 
Needed for terraform to function correctly. 