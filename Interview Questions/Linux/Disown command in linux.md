The disown command is used to remove jobs from current shell. Like cd and pwd , it is shell built-command and it doesn't require root privileges. 

### Syntax of disown command 

The basic syntax for the disown command is : 

```
	disown [options] jobID1 jobID2 ... jobIDN
```

Using the disown command in linux , 
The disown command in linux is used to remove jobs from the job table. You can also you it to keep a longer and more complex job running in the background even after you logout of the server. 

### Review Ongoing Jobs 
In order to user the disown command , you first need to have jobs running on your Linux System. 

```
cat /dev/random > /dev/null &
ping google.com > /dev/null &
```
Use the jobs command to list all current jobs : 


/dev/random generates random numbers. 

/dev/null is a special virtual device file , often referred to as a null device, bit bucket, or black hole. It functions as a sink that discards any data written to it immediately, while reporting that the write operation was successful. 


The `Ping` command is denoted by '+' , which means it's a currently active job.

The cat command is denoted by '-' , which means it will become active job if the ping command is terminated. 

### Remove All Jobs 

To remove all jobs from job table , use the following command : 

```
disown -a
```

### Remove specific jobs 

If you want to remove a specif job from the job table, use disown command with the appropriate jobID, THe job ID is listed in brackets on the job table; 

for example , if you want to remove the ping command , we need to use the disown command on job 2 

```
disown %2
```
Using the disown command without any options or job IDs removes the last job on the job table. 

### Remove currently running jobs 

To remove only the jobs currently running, use the following command : 

```
disown -r
```

### Keeps the job running after you log out

Once you exit your system's terminal , all currently running jobs are automatically terminated. To prevent this, use the disown command with the -h option 


```
disown -h jobID
```

In our case, we want the cat command to running in background  . To prevent it from being terminated on exit, use the following command : 

```
disown -h %1
```

BUT when i create the new terminal that job is not present there. 