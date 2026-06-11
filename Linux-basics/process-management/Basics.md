
## What is a process ?

A process is just a program in a running state.

Anything we do like opening browser, starting application , playing video, etc. we are creating a process. 


A lot of process belong to system services that run in background. 

The first process that starts is PID 1 

- Depending on which linux distro you're running, the name of this process is either "systemd" or "init" (in mac - Launchd is the first command)
- This process is either daddy or granddaddy of every other process that is running on the system
- So yes, Processes can spawn other processes. 

when we run normal ps command , it provides a quick snapshot of the processes associated with your current terminal session. 


	 macbookpro@Macbooks-MacBook-Pro ~ % ps

	  PID TTY           TIME CMD

	68421 ttys000    0:00.07 -zsh

	macbookpro@Macbooks-MacBook-Pro ~ %

PID : The unique process ID
TTY: Controlling the terminal for the process.
STAT: The current status of the process
TIME: The total CPU time the process has used
CMD: The command that started the process

## ps with options
#### ps aux
Here's what these options mean:

a : displays all the process for all users.
u: provides a detailed user-oriented format.
x: includes processes not attached to any terminal. These often include system daemons that start at boot and show ? in TTY






