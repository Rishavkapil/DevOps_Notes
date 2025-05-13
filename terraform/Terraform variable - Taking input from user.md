
We will use terraform variable if we want to take input from the user , 

like if we hit `terraform plan` , it should ask for username , when i type , lets say rishav 
it should print something like Hello Rishav 


To do this , first we need to make a variable inside the terraform file , 

Sample Terraform file 

`sample.tf`


	variable username{}
	output printname {
		value = "Hello ${var.username}"
	}

Now we will also destructure it 


Create a seperate file name `variable.tf` inside which we will store all the variables 


	variable username{}


and in other terraform file , all would be same like

	output printname{
		value = "Hello ${var.username}"
		}


We can also pass this in Command line like

			terraform plan -var "username=Rishav"



If we want to setup the default value for our variable we can also do that

		variable username {
			default = "World"
		}

In this case, it won't prompt for input , it will just simply print the World , if want to pass our own variable , we can do it by passing it via command line 
like 

			terraform plan -var "username=Rishav"


**NOTE : Terraform will only prompt for input if its not set**



### Multiple Variables 




