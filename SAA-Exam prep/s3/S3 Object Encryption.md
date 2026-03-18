You can encrypt objects in Amazon s3-managed keys 

- Server Side Encryption (SSE)
	- Server side encryption with KMS keys stored in AWS KMS
	- Server side encryption with Amazon S3-managed keys
	- Server side encryption with customer-provided keys
- Client Side encryption

### SSE-KMS

- Encryption using keys handled & managed by AWS KMS

- KMS advantages: user control + audit key using cloudtrail 



#### CORS(Cross-Origin Resource Sharing)

In simple words, CORS tells the browser which websites or origins are allowed to access your S3 bucket directly from frontend code. 

**What CORS Control in S3?**

- Allowed Origins
- Allowed methods(Get, PUT, POST etc. )
- Allowed Headers. 