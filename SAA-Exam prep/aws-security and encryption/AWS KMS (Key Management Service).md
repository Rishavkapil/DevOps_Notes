
* Anytime you hear encryption for an aws service , its most likely KMS.
* AWS manages encryption for us. 
* Fully integrated with IAM for authorization.
* Easy way to control access to your data. 
* Able to audit KMS key usage using cloudtrail.

### KMS Key Types

* KMS keys is the new name of KMS customer master keys.
* **Symmetric Key(AES-256 keys)**
	* Single key is used for both encryption and decryption
	* AWS services that integrated with KMS use symmetric key
* **Asymmetric Key(RSA & ECC key pairs)** :
	* Public key(Encrypt) & private Key(decrypt)
	* Use Case : encryption outside of aws by users who can't call the KMS API.

#### Types of KMS keys:

1. **AWS Owned Keys(free)** : SSE-S3, SSE-SQS, SSE-DDB
2. **AWS Managed Keys(free)** : aws/servicename
3. **Customer Managed Keys created in KMS**: 1$ per month


#### Automatic Key rotation

* AWS-managed KMS Key: automatic every 1 year
* Customer-managed KMS key: automatic & on-demand
* Imported KMS key: only manual using alias.
