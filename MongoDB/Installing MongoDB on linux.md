

***GPG KEY in MONGODB***

A GPG (GNU privacy guard) key in mongodb is used to verify the authenticity and integrity of mongodb packages.



### Step 1: Add MongoDB Repository


import the [public key to the Ubuntu server](https://phoenixnap.com/kb/generate-setup-ssh-key-ubuntu):

	curl -fsSL https://www.mongodb.org/static/pgp/server-7.0.asc | \
	   sudo gpg -o /usr/share/keyrings/mongodb-server-7.0.gpg \
	   --dearmor

 Create a list file and add the MongoDB repository to the system's sources list.

``
		`echo "deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-server-7.0.gpg ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/7.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-7.0.list`


				sudo apt update
### Install MongoDB


			sudo apt install mongodb-org
	

			mongod --version


### Start MongoDB


Start the MongoDB service with the following **`systemctl`** command:


	sudo systemctl start mongod


To enable launching the service at system startup, enter:

		sudo systemctl enable mongod

Start **mongosh** (the MongoDB shell) by typing:


			mongosh
Exit the mongodb shell by entering the following command: 
				`quit()`

		