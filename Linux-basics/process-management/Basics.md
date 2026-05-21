
## What is a process ?

A process is just a program in a running state.

Anything we do like opening browser, starting application , playing video, etc. we are creating a process. 


A lot of process belong to system services that run in background. 

The first process that starts is PID 1 

- Depending on which linux distro you're running, the name of this process is either "systemd" or "init" (in mac - Launchd is the first command)
- This process is either daddy or granddaddy of every other process that is running on the system
- So yes, Processes can spawn other processes. 


