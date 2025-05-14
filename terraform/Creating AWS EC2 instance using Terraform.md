

let's create a file with the name provider.tf (you can change the name of the file as per your requirement.) with the below content.



			provider "aws" {
			  region     = "us-east-1"
			  access_key = "YOUR_ACCESS_KEY_HERE"
			  secret_key = "YOUR_SECRET_KEY_HERE"
			}

put your access key and secret key that you get from aws.

now we are going to create an instance on AWS so let's create one more file in the same directory named as instance.tf with the below content


		
		resource "aws_instance" "web" {
		  ami                    = "ami-0b0ea68c435eb488d"
		  instance_type          = "t2.micro"
		  tags = {
		    Name = "first-tf-instance"
		  }
		}


