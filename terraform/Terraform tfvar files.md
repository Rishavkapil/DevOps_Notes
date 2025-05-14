

To set lots of variable , it is more convenient to specify their variables in a variable definition file (with filename ending with .tfvars or .tfvars.json) 

Terraform automatically loads a number of variable definitions files if they are present : 

1. Files named exactly terraform.tfvars or terraform.tfvars.json
2. Any file named with ending .auto.tfvars or .auto.tfvars.json


For Example : 

Create file with tf extension

		variable age {
		    type = number
		}
		
		variable "username" {
		  type = string
		}
		
		output printname {
		        value = "Hello, ${var.username}, your age is ${var.age}"
		}


Create a file terraform.tfvars

			
			age=25
			username="Gaurav Sharma"


**We cal also create custom file name of .tfvars file**

But then we need to pass that file in the Command line 
like 

	terraform plan -var-file=development.tfvars