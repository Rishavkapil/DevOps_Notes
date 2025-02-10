

S3 Bucket in AWS, is a container used for storing objects, such as files, images, videos etc, in the cloud.

Amazon Simple Storage Service (S3) is a massively scalable storage service based on [object storage](https://cloudian.com/blog/object-storage-care/) technology.



##### Key Features 

**Buckets:**  data is stored in buckets. Each bucket can store an unlimited amount of *unstructured data*.
Unstructured data means it does not have any predefined model . it stores data in the form of objects.

- **Elastic scalability**—S3 has no storage limit. Individual objects can be up to 5TB in size.
- **Flexible data structure**—each object is identified using a unique key, and you can use metadata to flexibly organize data.
- **Downloading data—** easily share data with anyone inside or outside your organization and enable them to download data over the Internet.


## How Does S3 Storage Work?

Amazon S3 data is stored as objects. Objects can be placed on a variety of physical disk drives distributed throughout the data centres.

Amazon provides redundancy and version control using block storage methods. Data is automatically stored in multiple locations, distributed across multiple disks, and in some cases, multiple availability zones or regions.

### Buckets

Buckets are logical containers in which data is stored. S3 provides unlimited scalability, and there is no official limit on the amount of data and number of objects you can store in an S3 bucket. The size limit for objects stored in a bucket is 5 TB.

An S3 bucket name must be unique across all S3 users, because the bucket namespace is shared across all AWS accounts.


### Keys

When you upload an object to a bucket, the object gets a unique key. The key is a string that mimics a directory hierarchy. Once you know the key, you can access the object in the bucket.


The bucket name, key, and version ID uniquely identify every object in S3. S3 provides two URL structures you can use to directly access an object:

`{BUCKET-NAME}.s3.amazonaws.com/{OBJECT-KEY}`

`s3.amazon.aws.com/{BUCKET-NAME}/{OBJECT-KEY`}


## Amazon S3 Storage Classes

S3 provides storage tiers, also called storage classes, which can be applied at the bucket or object level.
S3 also provides lifecycle policies you can use to automatically move objects between tiers, based on rules or thresholds you define.

The main storage classes are:

- **Standard**—for frequently accessed data
- **Standard-IA**—standard infrequent access
- **One Zone-IA**—one-zone infrequent access
- **Intelligent-Tiering**—automatically moves data to the most appropriate tier
- **S3 Express One Zone** (`EXPRESS_ONEZONE`) – Amazon S3 Express One Zone is a high-performance, single-zone Amazon S3 storage class


**Archived data** refers to data that is no longer actively used or frequently accessed but is stored for long-term retention due to legal, regulatory, compliance, or historical reasons.


### S3 Storage Archive

S3 provides Glacier and Deep Archive, storage classes intended for archived data that is accessed very infrequently.
- **S3 Glacier**—data must be stored for at least 90 days and can be restored within 1-5 minutes, with expedited retrieval.
- **S3 Glacier Deep Archive**—data must be stored for at least 180 days, and can be retrieved within 12 hours. There is a discount on bulk data retrieval, which takes up to 48 hours.



##### Types of Buckets in AWS

1. **General purpose Bucket**: 
			General purpose buckets in AWS S3 are the standard type of buckets used for storing objects and can contain objects across various storage classes except for S3 Express One Zone. They are recommended for most use cases and access patterns.

2. **Directory Bucket :** 
			Directory buckets are specialized for low-latency use cases and are designed to store data in a **single Availability Zone**, supporting only the S3 Express One Zone storage class.
			Directory buckets organize data hierarchically into directories, unlike the flat structure of general purpose buckets, and can scale horizontally with no prefix limits.




#### Uploading folders in S3 bucket

We can upload folders in s3 bucket, but Amazon S3 does not actually store folders. Instead it uses the key to stimulate folder structure.
en you upload a folder, S3 assigns a key name that includes the folder path. For example, if you upload a folder called `/images` containing `sample1.jpg` and `sample2.jpg`, S3 will upload the files and assign key names such as `images/sample1.jpg` and `images/sample2.jpg`.




### S3 Bucket Lifecycle policies

Lifecycle policies are the set of rules that define the actions to be taken on objects over time, allowing for automated management of data within the bucket.

These policies allow you to automate the transition of objects between different storage classes (such as moving data from standard storage to infrequent access storage) or even delete objects after a specified retention period.



#### Bucket Versioning in S3

Versioning is a means of keeping multiple variants of an object in the same bucket.

You can use the S3 Versioning feature to preserve, retrieve, and restore every version of every object stored in your buckets. Versioning-enabled buckets can help you recover objects from accidental deletion or overwrite.


An s3 bucket can be in three states :

	1. Unversioned state (by default)  
	2. Version-enabled state 
	3. Version-suspended state

When a user creates a s3 bucket ,by default the bucket will have the unversioned state.

Once a user enables the versioning of a bucket , it can't go back to the unversioned state.

But one can suspend the versioning of a bucket after it has been enabled.

