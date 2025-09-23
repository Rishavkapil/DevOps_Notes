
## Soft Limit 
The soft limit is the maximum resource limit that a user or process can use at a given time. It can be modified by the user upto the value of the hard limit. 

It allows users to have a degree of flexibility in resource usage while still enforcing a maximum that can be adjusted for their current needs. 

Example : A user may have a soft limit of 1GB for memory usage, which they can increase to the hard limit if needed. 


## Hard Limit 
The hard limit is the maximum resource limit that cannot be exceeded. Only root users(or users with appropriate permissions) can increase the hard limit. 

It serves as a safeguard to prevent users or processes from consuming excessive resources, which could affect system stability and performance. 

Example: If the hard limit for a file size is set to 2 GB , no user can create a file larger than this size unless the hard limit is raised by the administrator. 


## Setting limits 

You can view and set these limits using the ulimit command in the shell. 

* To view the current soft limit for the maximum file size. 
		`ulimit -f`

*  To set the new soft limit for the maximum file size (eg. 1GB).

		`ulimit -f 1024`
* To view the current hard limit 

		ulimit -H -f 

* To set the new hard limit . 

		ulimit -H -f 2048

SUMMARY : 

* Soft Limit :  user-adjustable limit, can be increased upto hard limit. 
* Hard Limit : Fixed limit, can only be changed by administrator. 