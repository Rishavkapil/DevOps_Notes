

Terraform is an open-source infrastructure as a code tool developed by hashicorp . It lets you define, provision and manage infrastructure across various cloud providers(like AWS , Azure etc. ) using a declarative configuration language. 
Terraform allows you manage and automate your infrastructure and your platform and services that run on that platform. 



## Why terraform was needed ?

Before tools like Terraform : 
* Infrastructure setup was done manually via GUIs or scripts (Bash, python etc. )
* It was prone to human error , hard to scale and difficult to reproduce across environments(dev, test , prod. )
* Tracking infrastructure changes was messy. 

**With Terraform:**
* Infrastructure becomes code that can be version controlled , peer reviewed and reused . 
* You get automation , repeatability 



## Terraform Architecture

			+--------------------------+
			|      Terraform CLI       |
			+-----------+--------------+
			            |
			            v
			+--------------------------+
			|    Terraform Core        |  <- Think of this as the "engine"
			|                          |
			|  - Dependency Graph      |
			|  - Plan/Apply Execution  |
			|  - State Management      |
			+-----------+--------------+
			            |
			            v
			+--------------------------+
			|     Providers (Plugins)  |  <- Speak to APIs (AWS, Azure, etc.)
			|   AWS, GCP, Azure, etc.  |
			+--------------------------+


#### Components explained 

**1. Terraform CLI :** The command line interface that you use(terraform init , plan , apply etc. )

**2. Terraform Core :** The brain that reads your configuration files , builds dependency graph , generates an execution path and applies it. 

**3. Providers :** Plugins that allow terraform to communicate with cloud providers or services like AWS , Azure , kubernetes , GitHub etc. 

**4. State file :**  Terraform stores the current state of your infrastructure in a file called `terraform.tfstate` . This helps it track what exists and what needs to change. 
## How does terraform work 


Lets say you want to create  an EC2 instance on AWS : 

1. **Write configuration :** 
	You write `.tf` files using HCL(HashiCorp configuration Language) :
			
			provider "aws" {
			  region = "us-west-2"
			}
			
			resource "aws_instance" "example" {
			  ami           = "ami-0c55b159cbfafe1f0"
			  instance_type = "t2.micro"
			}


2. **Initialize** : 


				terraform init

Downloads the necessary provider plugins . 

3. **Plan :** 

				terraform plan 
Shows what terraform will do - without making changes . Think of it as a dry run. 


4. **Apply :**  

				terraform apply 

Terraform executes the plan , creates modifies the infrastructure , updates the state file 


##### What is the difference between terraform and ansible 

Terraform is used when we need to create infrastructure and Ansible  is used when our infrastructure is ready or already created and to configure that we use ansible. 