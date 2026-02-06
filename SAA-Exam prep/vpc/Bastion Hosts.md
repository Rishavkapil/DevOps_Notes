The problem is that we don't have direct internet access to instance that are launched in private subnet. 

So the trick here is to use a **bastion hosts** 


Bastion Host is an EC2 instance and it is launched in a public subnet, has its own security group 


Now our, Bastion host EC2 instance has access to the our instance which is launched in private subnet because both are in the same VPC. 

Now to have internet access to our private EC2 instances, first we need to SSH into our bastion host EC2 , then from there again SSH to our EC2 in private subnet. 

