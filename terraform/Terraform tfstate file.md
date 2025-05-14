

When we build infrastructure with terraform configuration, a state file will be created automatically in the local workspace directory named "terraform.tfstate". This tfstate file will have information about the provisioned infrastructure which terraform manage. Whenever we make changes to the configuration file, it will automatically determine which part of your configuration is already created. And, also it will determine which needs to be changed with the help of the state file.


you may have noticed that when you ran the terraform plan or terraform apply commands, Terraform was able to find the resources it created previously and update them accordingly. But how did Terraform know which resources it was supposed to manage? You could have all sorts of infrastructure in your AWS account deployed through a variety of mechanisms (some manually, some via Terraform, some via the CLI), so how does Terraform know which infrastructure it's responsible for?

The answer is that Terraform records information about what infrastructure it created in a Terraform state file. By default, when you run Terraform in the folder, Terraform creates the file terraform.tfstate in that folder. This file contains a custom JSON format that records a mapping from the Terraform resources in your templates to the representation of those resources in the real world.