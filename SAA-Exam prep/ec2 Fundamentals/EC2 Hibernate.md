
We know we can stop, terminate instances: 

- Stop: The data on the disk(EBS) is intact in the next start. 
- Terminate: any EBS volume(root) also setup to be destroyed is lost 


By using EC2 Hibernate, 

- The in-memory (RAM) state is preserved. 

- The instance boot is much faster. 

- Under the hood, the RAM state is written to a file in the root EBS volume 

- The root EBS volume must be encrypted.