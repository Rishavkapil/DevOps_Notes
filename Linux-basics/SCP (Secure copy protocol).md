
SCP (Secure copy protocol ) is a command line tool used to securely transfer files between your local and remote server( like ec2 instance) using SSH encryption.

### How to use SCP to transfer files to EC2 instance



	scp -i your-key.pem <file_name> ubuntu@host_name:/<path_to_destinaion>


# What is the difference between scp and cp ?


==**cp**== : used to copy files locally (ie. within the same system )



==**scp**== : Secure copy (remote file copy over SSH). 

used to copy files between systems over a network. 
uses SSH for secure file transfer.  

