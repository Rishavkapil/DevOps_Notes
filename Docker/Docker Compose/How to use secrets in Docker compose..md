

A secret is any piece of data , such as password, certificate or API Key, that shouldn't be transmitted over a network or stored in a unencrypted Dockerfile 

Docker compose provides a way to use secrets without having to use environment variables to store information. 

Environment variables are often available to all processes , and it can be difficult to track access. They can also be printed in logs when debugging errors without your knowledge. 


Secrets are mounted as a file in `/run/secrets/<secret_name>` inside the container.


