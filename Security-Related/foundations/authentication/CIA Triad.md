
The CIA Triad is a model designed to guide security policies for organizations. 
It consists of three fundamental principles: 

- **Confidentiality :** Ensuring that information is accessible only to authorized individuals. 

- **Integrity:** Maintaining the accuracy and completeness of the data. 

- **Availability:** Guaranteeing that authorized users have reliable access to the resources and information when needed. 

### Confidentiality

- Certain information should only be know to certain people
- Prevent unauthorized information disclosure. 
- Encryption should be there, 
- Access Controls : selectively restrict access to resources. 
- Two-Factor authentication

### Integrity

- Data is stored and transferred as intended. 
	- Any modification to the data would be identified. 
- One way to providing integrity is by **HASHING** 
	- Map data of an arbitrary length to data of a fixed length. 
	- The person sending the data will create a hash of the data and send you both data and hash at the same time. 
	- When you receive the data , you'll perform the same hashing function , and then if your hash matches the sender hash, then you'll know that the data you've received is correct. 
- We an enhance integrity by including **DIGITAL SIGNATURES**
	- Mathematical scheme to verify the integrity of data. 

- Certificates
	- Combine with digital Signatures to verify individual 


### Availability 

- Information is accessible to authorized users

- One to provide AVAILABILITY is to design the system that are always been running. 

- Redundancy
	- Build Service that will always be available. 

- Fault Tolerant
	- Systems will continue to run, even when a failure occurs. 
