
When you run a command , Bash does a bunch of things ,. 

When you run `touch rishav` , Bash  : 

* Splits it into words and treats the first word as a command name. i.e touch 

**Thats why when you mistypes anything , it shows command not found ,** 


* Checks if the command name is an alias , is a function , and/or  has a hashed path , 
* Checks each directory in the PATH environment variable for an executable with that name, 
	* In my case , touch is at /usr/bin/touch . 
* It waits for the command to complete and return its exit status. 

