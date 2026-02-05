
- AMI in source account is encrypted with **kms** key from source account.

- Must modify the image attribute to add a launch permission which corrosponds to specified target aws account. 

- Must share the KMS keys used to encrypt the snapshot the AMI references with target account/iam role.

- Then in account B, Create IAM role/User & must have the permission to describeKey Re-encrypt , create, grant and decrypt. 