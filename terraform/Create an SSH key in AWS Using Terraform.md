
Lets create an ssh keypair on our local system using the ssh-keygen command
			
			ssh-keygen -t rsa 
		
		Generating public/private rsa key pair.
		Enter file in which to save the key (/home/kali/.ssh/id_rsa): ./id_rsa
		Enter passphrase (empty for no passphrase):
		Enter same passphrase again:
		Your identification has been saved in ./id_rsa
		Your public key has been saved in ./id_rsa.pub
		The key fingerprint is:
		SHA256:8CdVo44oVuPiN4AdAKt2sLTiYWpTqCzyF1s5YBcOvWo gaurav@learning-ocean
		The key's randomart image is:
		+---[RSA 3072]----+
		|...  .      o    |
		| . .. o    o .   |
		|.o  .o+o  o      |
		|o =oo++= +       |
		|oB.+*+o.S o      |
		|O +oE++  o       |
		|== ..+o.         |
		|+.. o. .         |
		|  ..             |
		+----[SHA256]-----+




now we can see that id_rsa and id_rsa.pub files were created.

now let's create a file aws-kp.tf with the below content.



			# creating ssh-key.
			resource "aws_key_pair" "key-tf" {
			  key_name   = "key-tf"
			  public_key = file("${path.module}/id_rsa.pub")
			}


now let's run terraform plan and apply the command we can see that the new key pair create on aws.

				terraform plan
				terraform apply

	