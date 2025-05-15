

Terraform searches the environment of its own process for environment variables named TF_VAR _ followed by the name of a declared variable 


This can be useful when running terraform in automation or when running a sequence of Terraform commands in succession with the same variables . 

On operating systems where environment variable names are case-sensitive, Terraform matches the variable name exactly as given in configuration, and so the required environment variable name will usually have a mix of upper and lower case letters.


For example : 

		variable "username" {
		  type = string
		}
		
		output printname {
		        value = "Hello, ${var.username}"
		}


now set the value of username variable in the environment using the below command


```sh
export TF_VAR_username=Rishav
```




To save the environment variables permanently , you need to store them in 
`~/.bashrc file `




for example 
		
		export $TF_VAR_ACCESS_KEY="your-access-key"


