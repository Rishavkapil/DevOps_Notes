
* Unencrypted objects and objects encrypted with SSE-S3 are replicated by default. 

For objects encrypted with SSE-KMS , you need to enable the option

* Specify which KMS key to encrypt the objects within the target bucket.
* Adapt the KMS key policy for the target. 
* You might get KMS throttling errors, in which case you can ask for service quota increase. 

**You can use multi-region KMS keys , but they are currently treated as independent keys by Amazon S3( the object will still be decrypted and then encrypted).**

