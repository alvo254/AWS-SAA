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