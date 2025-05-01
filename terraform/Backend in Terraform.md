

In Terraform, Backend defines where and how terraform stores its state file, which is snapshot of your infrastructure. 

This file tracks the resources terraform manages so it knows what to create , update or destroy during subsequent operations. 


#### Key Concepts : 

**Terraform Statefile** (terraform.tfstate)

The state file keeps track of : 

What infrastructure terraform has created 
Resouce ID's, settings , metadata etc. 
What needs to be updated , changed or destroyed. 

By default this statefile is saved locally on your system . But with a backend , you can store it remotely in a shared location (like AWS, Azure etc. )

### Why Backend is important 

Imagine you are building infrastructure with a team : 

- If everyone keeps their own statefile locallly , things get messy. 
- You could overwrite some else's changes. 
- Collaboration becomes difficult .
- Remote backends allow for team sharing , locking and safety. 


### What does a backend do ?

Backend handles : 

* Storing state files 
* Locking (So only one person can run changes at a time )
* Versioning (keeping past copies)


**Example**

S3 Backend


		terraform {
		  backend "s3" {
		    bucket         = "my-terraform-state"
		    key            = "env/dev/terraform.tfstate"
		    region         = "us-east-1"
		    dynamodb_table = "terraform-locks"  # optional: for state locking
		    encrypt        = true
		  }
		}
i