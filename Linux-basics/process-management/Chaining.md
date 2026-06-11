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

then its parent process will be zsh, but then if i run 

ps -ef | grep sleep

then there are multiple things happening, first the parent process is zsh with process ID 4014, it has two different child processes, one is sleep (4254) and other two are siblings


```
zsh (4014) ----------+
  |                  / \
  |                 /   \
  |                /     \
  |               /       \
sleep (4254)    ps (4378)  grep (4379)
```