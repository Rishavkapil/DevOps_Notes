

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
