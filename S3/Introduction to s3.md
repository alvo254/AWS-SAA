### What is Object Storage(Object-based storage)?

Data storage architecture that manages data as objects as opposed to other storage architecture:

-   File systems: which means data as a file and fire hierarchy and
    
-   block storage which manages data as blocks within sectors and tracks
    

## S3 Object

Object contains your data. They are like files. Object may consist of:

-   Key this is the name of the object.
    
-   Value the data itself made up of a sequence of bytes
    
-   Version ID when versioning enabled, the version of the object
    
-   Metadata additional information attached to the object
    
-   You can store data from 0 bytes to 5 Terabytes in size
    

## S3 Bucket

Bucket holds objects. Buckets can also have folders which in turn hold objects. S3 is a universal namespace so bucket names must be unique.

## Storage Classes

-   Standard (default) - Fast! 99.99% Availability. Replicated across at least 3 AZs
    
-   Intelligent Tiering - Use ML to analyze your object usage and determine the appropriate storage class. Data is moved to the most cost-effective access tier, without any performance impact or added overhead.
    
-   Standard infrequently Accessed(IA) - Still fast! cheaper if you access files less than once a month. An additional retrieval fee is applied. 50% less than standard.
    
-   One Zone IA - Still Fast! Objects only exist in one AZ. Availability is (95.5%). But cheaper than standard IA by 20% less
    
-   Glacier - For long-term cold storage. Retrieval of data can take minutes to hours.
    
-   Glacier Deep Archive - The lowest cost storage class. Data retrieval time 12 hours.
    

## S3 security

All new buckets are private when created by default. Access control is configured using **Bucket Policies** and **Access Control List (ACL)** This is legacy but not deprecated.

## S3 Encryption

Traffic between your local host and s3 is achieved via SSL/TLS

#### Server Side Encryption (SSE) -Encryption At Rest

Amazon helps you encrypt the object data S3 Managed keys - AWS manages all keys SSE-AES s3 handles the key, uses AES-256 algorithm SSE-KMS Envelope encryption, AWS KMS and you manage the keys SSE-C Customer provided key managed by you

Client-side Encryption you encrypt your own files before uploading them to the s3

## Data Consistency

#### New Object (PUTS)

Read After Write Consistency When you upload a new s3 object you are able to read immediately after writing

#### Overwrite (PUTS) or Delete Object (DELETES)

Eventual Consistency When you overwrite or delete an object it takes time for s3 to replicate versions to AZs If you were to read immediately, S3 may return you an old copy. Generally, you need to wait for a few seconds before reading.

## Cross Region Replication (CRR)

When enabled, any object that is uploaded will be automatically replicated to another region(s). Provides higher durability and potential disaster recovery for objects. You must have versioning turned on both the source and destination buckets. You can have the CRR replicated to another AWS account.

## S3 Versioning

-   Store all versions of an object in S3
    
-   Once enabled it cannot be disabled, only suspended on the bucket.
    
-   Fully integrates with S3 lifecycle rules
    
-   MFA Delete feature provides extra protection against deletion of your data
    

## S3 Lifecycle Management

Automate the process of moving objects to different storage classes or deleting objects altogether. Can be used together with versioning and can be applied to both current and previous versions.

## Transfer Acceleration

Fast and secure files over long distances between your end users and s3 buckets. utilizes **CloudFronts** distributed **Edge Locations**. Instead of uploading to your bucket, users use a **distinct URL** for an edge location. As data arrives at the edge location it is automatically routed to S3 over a specially optimized network path (AWS backbone network)

## S3 Presigne URLs

Generate a URL that provides you temporary access to an object to either upload or download object data. Presigned Urls are commonly used to provide access to **private objects**. You can use AWS CLI or AWS SDK to generate pre-signed URLs.

## MFA Delete

Ensures users cannot delete objects from a bucket unless they provide their MFA code. MFA Delete can only be enabled under these conditions.

-   The AWS CLI must be used to turn on MFA
    
-   The bucket must have the versioning turned on
    

`aws s3api put-bucket-versioning --bucket <bucketname> --versioning-configuration status=Enabled, MFADelete=Enabled --mfa <your-mfa-serial-number mfa-code>`

Only the bcuket owner logged in as root user can delete objects from the bucket.