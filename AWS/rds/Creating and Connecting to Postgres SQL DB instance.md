
1st you need to create an ec2 instance 
then you need to create a RDS postgres instance 
then SSH to ur ec2 instance
and then install postgres on EC2 instance
	it is done using command 
			`sudo apt install postgresql-16`


then connect to RDS instance using 


	psql --host=<endpoint> --port=5432 --username=postgres
then you will be prompted for password which you have created while creating RDS

	