
RDS setup steps:
	1. First choose rds from search menu inside all aws services
	2. Go inside region where we need to setup our rds instance
	3. Create a security group inside same region with name extension, e.x., stage-rds-musicbull-sg. Open only database port and route to vpc cidr block
	4. Now next create a subnet group and click on create db subnet group.
		a.) Add name for security group
		b.) Choose vpc for subnet group
		c.) Add all availability zones for your vpc
		d.) Choose all subnets inside your vpc
		e.) Click on create subnet group
	5. Next click on parameters group and click on create parameters group.e.x., stage-rds-musicbull-pg
		a.) Add name for your parameters group as well as description
		b.) Choose DB engine type.
		c.) Add parameter group family.
		d.) Add Type as DB Parameter Group
		e.) Click on create button to create the parameter group
	6. Modify parameter group entry.select the parameter group and click on edit and add these entries
		interactive_timeout		60
		wait_timeout		60
		log_output		file
		slow_query_log		1
		general_log		1
		log_bin_trust_function_creators 1
		read_only                  0
		long_query_time             5
	7. Now Click on database to create database
		a.) Select the database (MySQL Community)
		b.) Select version for database
		c.) Select the template for database (Environment for database). e.x., Dev/Test
		d.) Select the Availability and Durability for database. Use Single DB instance for Dev/Test
		e.) In DB settings,
			i) First add name for your database.e.x., stage-rds-musicbull
			ii) Add username for database. Use admin for dev/test or staging
			iii) Click on self-managed password
			iv) Either choose Auto-Generated or Custom password as per your's need.
		f.) In instance configuration, choose the db instance type. Use db.t3.micro for Dev/Test environment
		g.) Specify volume for your db instance.
		h.) In connectivity
			i) Choose Don't connect to an ec2 compute resource
			ii) Select your vpc
			iii) Select the same db subnet group which you created in previous stages.
			iv) Select No to public access
			v) Choose your existing security group which created in step3
		i) In Additional Configuration, select your parameter group which we created earlier.
		j) Enable automated backups and setup retention period as per description
		k) Enable Encryption for your data
		l) Select all log exports