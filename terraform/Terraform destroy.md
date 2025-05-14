

The terraform destroy is used to destroy infrastructure governed by terraform. To check the behavior of terraform destroycommand at any time we can use terraform plan -destroy command.

For the deletion of the particular resource and its dependencies **-target**flag can be used

example:


	terraform destroy --target github_repository.terraform-second-repo




	