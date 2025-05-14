


A map value is a lookup table from string keys to string values . This is useful for selecting a value based on some other provided value. 

This is useful for selecting a value based on some other provided value. 

A common use of map is to create table of machine images per region , as follows : 


		variable "images" {
		  type    = "map"
		  default = {
		    "us-east-1" = "image-1234"
		    "us-west-2" = "image-4567"
		  }
		}


Lets take a simple example of terraform map , 

Create a file with .tf extension


			variable "usersage" {
			    type = map
			    default = {
			        gaurav = 20
			        saurav = 19
			    }
			}
			output "userage" {
			    value = "my name is gaurav and my age is ${lookup(var.usersage, "gaurav")}"
			}




### Difference between terraform map and terraform obejct


In terraform map, we can only store key-value pairs of same type






## How to read dynamic values from map variable 

lets create a file 

			variable "usersage" {
			    type = map
			    default = {
			        gaurav = 20
			        saurav = 19
			    }
			}
			
			variable "username" {
			  type = string
			}
			
			output "userage" {
			    value = "my name is ${var.username} and my age is ${lookup(var.usersage, "${var.username}")}"
			}


**How to pass map variable from command line**
		
		terraform plan -var username="gaurav" -var usersage="{"gaurav"=22,"saurav"=23}" 



