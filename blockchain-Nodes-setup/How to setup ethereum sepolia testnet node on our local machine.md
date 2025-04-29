

## Step 1 : Install the execution client (Geth - GoEthereum)

In this , i'll be installing **geth** as the execution client 

To install geth , go to https://geth.ethereum.org/docs/getting-started/installing-geth this url and download geth for your machine . 


## Step 2 : IF you are running this is first time its recommended to try this in development mode first (OPTIONAL)


To run geth in the development mode : 
First go to the directory in which you downloaded the geth ,(i'll recommend to create another directory for this project)

**We first need to create an account**

		geth --datadir <path_to_directory> account new
		
then we need to create a file for secrets in which we will store the password of our account that we just created using above command . 


Now to run this in development mode , 


	geth --datadir <path_to_directory> --dev --password <path_to_secrets_file>


So to interact with this geth node 

		geth attach <url_given_in_the_logs_of_node>

now you will be in the console of the geth node 

Now to check for user accounts 

in console run `eth.accounts`
to check balance `eth.getBalance`




## Step 3 : Connecting geth node to sepolia network



	geth ---datadir <path_to_directory_(new)> --sepolia  --http -http.api eth,net,web,admin 



When you run this you will be connected with your sepolia network 


## Step 4 : Connect with Consesus client 


Now we need to connect this with the consesus client for that we first need to download the consensus client for the sepolia network 

