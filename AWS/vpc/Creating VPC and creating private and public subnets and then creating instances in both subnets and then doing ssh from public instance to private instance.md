

## Step 1 : Creating a VPC


Prefer to give 10.0.0.0/16 or something in CIDR block


## Step 2 : Creating Subnets 


Create Subnets with different IP's

like 10.0.1.0/24 , 10.0.0.2/24 etc. 


## Step 3 : Create route tables for both public and private subnets

there will two route tables in this case . 
and then add both public and private subnets in respective route tables. 


## Step 4 : Creating Internet gateway 

## Step 5 :  Creating NAT gateway


We will create a NAT gateway and then we will attach it with **public subnet** . 

## step 6 : Adding routes in both route table


Attach Internet gate for all traffic in public routing table 

Attach nat gateway for all traffic or specific ip in private route table

## Step 7 : Create two instances 

Create 1 instance in public subnet and 1 in private subnet . 
SSH into public instance and then we will have to copy pem key using scp if not present in the public instance , 
then we will ssh into that using the private ip of private instance . 