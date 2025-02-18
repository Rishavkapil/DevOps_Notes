


The **Docker stop command issues SIGTERM**   singal where as **Docker KILL command sends SIGKILL signal**  


**The SIGTERM gracefully terminates a process rather than killing it immediately .** 

**SIGKILL kills the process immediately**  . 


It is possible to handle , ignore or block a SIGTERM signal , but a SIGKILL signal cannot be blocked or handled. 


