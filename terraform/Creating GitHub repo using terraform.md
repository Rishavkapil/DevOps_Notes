

create a file in a folder with .tf extension with the below contents



			provider "github" {
			  token="ghp_lEvJ2GJxXgBnyZlVfQXXXXXXXXXjMUK"
			}
			
			resource "github_repository" "terraform-first-repo" {
			  name       = "first-repo-from-terraform"
			  description = "My First resource for my youtube viewers."
			  visibility = "public"
			  auto_init  = true
			}


Now lets run the terraform provider command to see the output 


	terraform providers


The terraform providers command shows information about the provider requirements of the configuration in the current working directory 


**Terraform init** 

This command performs several different initialization steps in order to prepare the current working directory for use with Terraform.

This command is always safe to run multiple times, to bring the working directory up to date with changes in the configuration.

In order to prepare the working directory for use with Terraform, the terraform init command performs the following steps:

- Backend Initialization
- Child Module Installation
- Plugin Installation

**Terraform plan**

This command looks in the current working directory for the root module configuration. The terraform plan command creates an execution plan, which lets you preview the changes that Terraform plans to make to your infrastructure. 


**Terraform apply**

By default, apply scans the current directory for the configuration and applies the changes appropriately. However, a path to another configuration or an execution plan can be provided.

Terraform apply command is used to create orintroduce changes to real infrastructure.

By default, apply scans the current working directory for the configuration and applies the changes appropriately.

However, you'll optionally give the path to a saved plan file that was previously created with terraform plan.

