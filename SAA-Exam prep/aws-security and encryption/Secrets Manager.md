
- Newer service, meant for storing secrets.
- Capability to force rotation of secrets every x days.
- Automate generation of secrets on rotation(uses Lambda)
- Integrated with Amazon RDS (MySQL, PostgreSQL, Aurora)
- Can be encrypted with KMS


### Multi Region Secrets

-  Replicate secrets across multiple AWS regions
- SM keep read replicas in sync with the primary secret. 


Use Cases:  multi-region apps, disaster recovery.

