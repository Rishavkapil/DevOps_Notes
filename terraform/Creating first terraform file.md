
Steps to create a Terraform file : 

1. Go to the Directory in which you want to create the terraform  file 
2. Create a file with .tf extension 


In this file , we will just simply add the code for hello

		
		output hello1{
			value = "Hello World"
		}



after saving this file run , `terraform plan` , this will show what will happen if we hit `terraform apply`



We can also write terraform files in json format 

to do that 

{
	"output" : {
			"hello1" : 
			{
			"value" : "Hello "
			}
		}
}


Now save this file with the `.tf.json` extension 


