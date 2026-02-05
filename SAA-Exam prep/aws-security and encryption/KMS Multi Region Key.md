
Same Key is replicated across multiple regions , even the Key id will be same .

* Identical KMS keys in different AWS regions that can be used interchangeably. 


Use Cases :  

Global client-side encryption, encryption on Global DynamoDB, Global Aurora


### Dynamo DB Global Tables and KMS multi-region key client-side encryption

* We can encrypt specific attributes client-side in our DynamoDB table using Amazon DynamoDB Encryption Client , so that data is accessible only to specific client, not even to database administrator. 