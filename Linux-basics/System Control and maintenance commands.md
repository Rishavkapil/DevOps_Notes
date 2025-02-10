**Systemctl :** This command is used to manage systemd services. 
	We can start , stop , enable or disable services using `*systemctl*` command
	Syntax :  sudo systemctl [ action ]  [ service name ]
	Example : sudo systemctl disable mysql
		actions are like start , stop , enable , disable , restart , status etc. 
**Service :** This is also used to manage system services .
	We can only do actions like start , stop , restart , reload etc. It does not allow enable or disable actions .
	It is older than systemctl and provides less tools than systemctl

**What are systemd Services ?**
Systemd services are the processes that run in the background on a linux system , providing various functionalities and services.

**Daemon :** A daemon is a type of computer program that runs in the background, performing various tasks without direct interaction from the user. 
eg. sshd -> Secure shell daemon : Listens to secure shell protocols and processes incomming requests.
**crontab :** This command is used in linux to manage corn table , which is a list of scheduled tasks.
corn is a daemon that runs in the background and execute these tasks at specified times.
It is used in scheduling and automating tasks. 
It facilitates the users to run scripts and linux commands at specified times and intervals.
**Syntax : MIN HOUR DOM MON DOW CMD**
**MIN(minute) :** specifies the minute when command will run . range = 0-59
**HOUR:** denotes the hour of the day when the command is scheduled to execute . range = 0 - 23
**DOM(Day of Month):** Specifies the day of the month for the task . range = 1-31
**MON(month) :** Indicate the month during which the command will execute . range = 1-12.
**DOW(Day of the week):** specifies the day of the week for the task. range = 0-7.
**CMD(command) :** represent the actual command or script that will execute at the scheduled time .  