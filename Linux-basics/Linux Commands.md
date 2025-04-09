
**df**  **(Disk free):** Shows the amount of disk space used and available on **file systems**.

Displays space usage at the file system level (i.e., how much space is used and free on each mounted file system).

`df` is useful for understanding how much space is left on the entire file system or partition

**du (disk usage):**

Shows the **disk space used by files and directories**.


Displays space usage at the **directory level**. It tells you how much space individual files or directories are using.

 `du` is useful for understanding the disk usage of specific files or directories.




**useradd :**  It requires you to explicitly provide options for user attributes (e.g., home directory, shell, group, etc.), or it will apply the system defaults.

- **No interactive prompts**: By default, `useradd` does not prompt you for additional details when creating the user account. You need to specify everything explicitly via options or rely on default settings.

**adduser :**  `adduser` is a more user-friendly, interactive script for creating new users. It's often available on distributions like Debian, Ubuntu, and derivatives.
**Interactive**: `adduser` prompts you for all required information (like password, home directory, full name, etc.), making it easier to create a new user.



#### To delete data inside the file but not the actual file
	rm -rf <file_name>/* 



## Grep command 

used to search for text patterns within files 

		syntax : grep [options] pattern [file ...]


Common Examples : 

1. Search for a word in a file 

		grep "Hello" file.txt

2. Case Insensitive search 

		grep -i "hello" file.txt



## What is Pipeline in linux 

A pipeline in linux connects the output of command to the input of other using the | (pipe) symbol.


		command1 | command2 


Grep using code Pipelines : 


Eg. Find a running process

	ps aux | grep "nginx"


ps aux : List all the running processes 
grep "nginx" filters the output to only show lines containing NGINX. 