
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


#### px -ef

This is very popular way of getting full picture of everything running on your system.

this provides full listing of all processes.

-e : selects every process on the system. 
-f : displays a "full format" listing, which includes tails like PID, UID , C(CPU utilization ) and STIME (Start time)


Many prefer ps -ef over ps aux for its clear , heirarchical view and detailed information. When troubleshooting on a linux system , running ps -ef is often one of the first steps to diagnose issues. 


### Real time monitoring with top

while ps gives you a snapshot , the top command provides real time dynamic view of the processes on your system. It is an excellent tool for identifying which processes are consuming the most CPU or memory. By default, top display refreshes every few seconds. 


