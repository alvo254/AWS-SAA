### What is Object Storage(Object-based storage)?
Data storage architecture that manages data as objects as oposed to other storage architecture:
- File systems: which means data as file and fire hiearachy and 
- block storage which manages data as blocks within sectors and tracks

## S3 Object 
Object contain your data. They are like files.
Object may consit of:
- Key this is the name of the object.
- Value the data itself made up of a sequence of bytes
- Version ID when versioning enabled, the version of object
- Metadata additional information attached to the object
- You can store data from 0 bytes to 5 Terabytes in size

## S3 Bucket
Bucket hold objects. Buckets can also have folders which in turn hold objects.
S3 is a universal namespace so bucket names must be unique.

## Storage Classes 
- Standard (default) - Fast! 99.99% Availability. Replicated across at least 3 AZs
- Intelligent Tiering - Use ML to analyze your object usage and determine the appropriate storage class. Data is moved to the most cost-effective access tier, without any perfomace impact or added overhead.
- Standard infrequently Accessed(IA) - Still fast! cheaper if you access files less than once a month. Additional retrieval fee is applied. 50% less than standard.
- One Zone IA - Still Fast! Objects only exists in one AZ. Availability is (95.5%). But cheaper than standard IA by 20% less 
- Glacier - For long-term cold storage. Retrial of data can take minuntes to hours.
- Glacier Deep Archive - The lowest cost storage class. Data retrieval time 12 hours.