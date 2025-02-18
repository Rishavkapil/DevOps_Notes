
### Step 1: Add Official Repository

			sudo apt install wget ca-certificates



			wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -



			`sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt/ $(lsb_release -cs)-pgdg main" >> /etc/apt/sources.list.d/pgdg.list'`





###   Step 2: Install PostgreSQL



				sudo apt update



				sudo apt install postgresql postgresql-contrib




### Step 3: Check PostgreSQL status



				sudo systemctl status postgres




### Step 4: Start Using PostgreSQL Command Line Tool




				sudo -u postgres psql




