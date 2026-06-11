when we run command like ps -ef , we'll see columns like PID, PPID

PID --> (Process ID ) a unique identifier of a process

PPID --> (Parent Process ID ) It is the PID of the process which created the current process. 

	PID   PPID
	456   123

means:
- Process 456 was created by Process 123.
- Process 123 is the parent.
- Process 456 is the child.


like we do sleep 

then its parent process will be zsh