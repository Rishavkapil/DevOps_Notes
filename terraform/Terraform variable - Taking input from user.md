
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