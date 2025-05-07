

First you need to login as the default user (ubuntu)

#### Step 2 : Switch to root user 

		sudo -i 


#### Step 3 : Create .ssh directory for root (if it doesn't exist)

		mkdir -p /root/.ssh



#### Step 4 : Copy the ubuntu user's public key into root's authorized keys



		cp /home/ubuntu/.shh/authorized_keys /root/.ssh/


#### Step 5 : Secure the .ssh directory and key file 


	chmod 700 /root/.ssh
	chmod 600 /root/.ssh/authorized_keys




#### Step 6 : Edit the ssh configuration to allow root login 


			nano /etc/ssh/sshd_config


Fix or add the following lines : 


				PermitRootLogin yes
				PasswordAuthentication no



Now you should be  able to login directly as the root user :)