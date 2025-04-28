

## Step 1 : Install the execution client (Geth - GoEthereum)

In this , i'll be installing **geth** as the execution client 

To install geth , go to https://geth.ethereum.org/docs/getting-started/installing-geth this url and download geth for your machine . 


## Step 2 : IF you are running this is first time its recommended to try this in development mode first (OPTIONAL)


To run geth in the development mode : 
First go to the directory in which you downloaded the geth ,(i'll recommend to create another directory for this project)

**We first need to create an account**

		geth --datadir <path_to_directory> account new
		
then we need to create a file for secrets in which we will store the password of our account that we just created using above command . 



