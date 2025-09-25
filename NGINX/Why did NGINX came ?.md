
The most common reason is to solve C10K problem . 
NOw ,

### What is C10K problem ?

It's time for web servers to handle ten thousands clients simultaneously. 

You can buy a 1000MHz machine with 2 gigabytes of RAM and 1000Mbit/sec Ethernet card for 1200$ or so . Lets seee - at 20000 clients , thats 50KHZ , 100k bytes, and 50kbits/sec per client. 

In simple terms, there was apache before NGINX, and it was not able to handle multple users at the same time eg. 10K users. 

So this problem is named after this , Concurrency 10K problem.

So NGINX came to solve this problem, 