

### How to set username and password that never expires.

	
				chage -M -1 rishav


### What does /etc/shadow file contain 


The /etc/shadow file in linux contain secure user account information, including encrypted password and account expiration details . 

Each entry in the file corresponds to a user and is separated by colon(:). 

The fields in the each entry include the username , encrypted password , last password change data, minimum password age , maximum password age, etc. 



### What does /etc/passwd file contain 


Contains information for all the user accounts on a Linux system. 
Each line in the file represents a user account and consist of seven colon separated fields : username, password, userID , groupID etc. 


The password field typically contains an 'x' character , indicating that the actual password is stored in the /etc/shadow  file for increased security 



### Why /etc/passwd and /etc/shadow files cannot be merged into one file ?

/etc/passwd is a text file and can be read by any other application , so an attacked could gain access to the information of the file that included hashed password . 

To increase security, the hashed password that used to be in the file was moved to other file called /etc/shadow that is accessible only by the root. 


### To list , all the opened file by its particular PID. 


				lsof -p  PID
Count the number of files and processes 



### We are unable to unmount the file system , what are the reasons behind it 


1. Either you are in the same directory (try to get path by using pwd)


### What could be the reason if server takes more time after reboot ?


file system got corrupted


### How to check kernel routing information 

There are 3 commands to check for kernel routing information. 

		route -n
		netstat -rn 
		ip route 


### What is default gateway in linux

The default gateway in linux is the IP address of a router that your system uses to send traffic to destinations outside its local subnet 



### How to Check which services are currently running in Linux system.

```
sudo systemctl list-units --type=service --state=running
```

### How to set a password that require users to change password every 30 days 


option 1 : Set password policy for specific user 

```
sudo chage -M 30 username
```

option 2 : Set Default password policy for all new users 

```
sudo vim /etc/login.defs

and add the below lines if not already present

PASS_MAX_DAYS 30
PASS_MIN_DAYS 0
PASS_WARN_AGE 7
```


### How to create new user and give sudo previlages to it

```
sudo adduser
sudo usermod -aG sudo username
```


### How to create user with only specific permission like should only run basic commands and docker


Step 1 : Create a new user , you can create it using sudo adduser <user_name>


Step 2 : Create a private bin directory for allowed commands. 

```
sudo mkdir /home/devuser/bin
```
- Instead of copying binaries, we made **symlinks** to the real commands:
    
```
sudo ln -s /bin/ls /home/devuser/bin/ls sudo ln -s /bin/cat /home/devuser/bin/cat sudo ln -s /usr/bin/docker /home/devuser/bin/docker # (and so on for mkdir, rm, cp, mv)
```

Step 4 : Restricted Path

```
echo 'export PATH=$HOME/bin' 

```

