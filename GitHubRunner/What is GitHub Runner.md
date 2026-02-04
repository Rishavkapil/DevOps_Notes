

A **GitHub runner** is machine that execute jobs in a GitHub Action Workflow. 

It can be virtual machine hosted by GitHub or a self-hosted runner that you deploy and manage. 

GitHub provide runners that are pre-configured with an operating system and a set of tools and packages , including Ubuntu, Windows , macOs runners etc. 


### What is Self-Hosted Runner

A **Self-hosted runner** is a system that you can deploy and manage to execute the jobs from GitHub Actions on GitHub. 

with Self-Hosted Runners, you can create custom hardware configurations that meet your needs with processing power or memory to run larger jobs. 

Self-Hosted runners allow complete control over the environment , dependencies , and hardware. 
These runners can be Virtual Machines, Physical Servers or even personal Computer. 

#### How do self hosted runner work

Self-Hosted runners are machines that run the self-hosted runner script 

When you run the script , you set the self-hosted key you get from your GitHub UI . 

Once the Script runs on the machine , it opens a long poll connection (50 seconds ) with GitHub. 

