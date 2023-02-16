Amazon Elastic Block Store (Amazon EBS) is an easy-to-use, high-performance, block storage service designed for use with Amazon Elastic Compute Cloud (Amazon EC2) for both throughput and transaction intensive workloads at any scale. A broad range of workloads is widely deployed on Amazon EBS, such as relational and nonrelational databases, enterprise applications, containerized applications, big data analytics engines, file systems, and media workflows.

## 

**Primary data storage types**

Whether on premises or in a cloud environment, you have three primary types of storage: block, file, and object. Different storage hardware manufacturers and cloud service providers implement these storage types differently. However, the fundamentals for each storage type are basically the same, regardless of where the storage type is located, who manufactures the hardware, or who provides the service. The specific features and functionality differ based on how the manufacturer or service provider implements the storage.

### Block storage overview
_Block storage_ is raw storage in which the hardware storage device or drive is presented, as either disk or volume, to be formatted and attached to the compute system for use. The storage is formatted into predefined continuous segments on the storage device. These segments are called blocks, which is where this storage type gets its name. The blocks are the basic fixed storage units used to store data on the device.

  

Storage devices can be hard disk drives (HDDs), solid state drives (SSDs), or newer types of storage devices, such as Non-Volatile Memory Express (NVMe). In addition to individual storage devices, block storage can be deployed on storage area network (SAN) systems.

The storage device is presented to be used by the operating system or an application that has the capabilities to directly manage block storage. In cases where the application manages the block storage, the application often shares management with an operating system.

Following this overview section on the primary storage types, you learn more about the details of block storage.

### File storage overview
_File storage_ is built on top of block storage, typically serving as a file share or file server. File storage is created using an operating system that formats and manages the reading and writing of data to the block storage devices. The name file storage comes from the primary use of storing data as files typically in a directory tree hierarchy.

The two most common storage protocols for file storage are Server Message Block (SMB) and Network File System (NFS), which are network protocols that enable users to communicate with remote computers and servers. The protocols enable users to use the servers' resources or share, open, and edit files.

The operating system manages the storage protocol and the operation of the file system. The file system can be Windows Server, Linux, or a specialized operating system used on network attached storage (NAS) devices or clustered NAS systems.

### Object storage overview
_Object storage_ is also built on top of block storage. Object storage is created using an operating system that formats and manages the reading and writing of data to the block storage devices. The name object storage comes from the primary use of storing the data within a binary object. Unlike file storage, object storage does not differentiate between types of data. The type of data or the file type becomes part of the data's metadata.

An object is made up of a larger sets of blocks organized using a predetermined size. For example, one object storage system uses binary object sizes of 128 megabytes (MB). Smaller files or data are stored at a binary level within the object. Larger data files are stored by spreading the data across multiple objects.

Object storage is recognized for its inherent availability of the file objects. Some systems support file versioning, file tracking, and file retention.

##

**Block storage architecture**

The basic block storage architecture consists of three components: the block storage, the compute system, and the operating system running on the compute system. The block storage is either physically or logically attached to the compute system. The operating system, which runs on the the compute system, then recognizes the block storage as available. The operating system formats or makes the block storage ready for use. In some situations, an application running on the compute system can act as the managing entity rather than the operating system. However, for most use cases, the operating system running on the computer system manages the block storage.

### Block Storage Management 
The operating system or application manages the block storage. Some of the aspects that the operating system manages are configuring the block size; creating and managing metadata; managing read, modify, and write activity; and managing file-level and block-level locking.

### Block size
The operating system must first format the block storage. When you format the block storage, you select the block size that best meets your use case. For some applications, small block sizes are more appropriate, and larger block sizes better serve other applications. Block size flexibility is a fundamental differentiator for block storage. You have the ability to format the storage to best service your application requirements.

### Metadata management
When data is stored, the operating system creates metadata. Metadata is data about the data. The metadata information helps to manage a data resource, such as resource type, permissions, and the time and way it was created. The metadata includes the information that the operating system and users need to identify and track the data.

-   Metadata includes timestamp tracking for the data such as:
    -   The creation or birth time (ctime), which is when the data was first created.
    -   The modification time (mtime), which is when the data or metadata was last changed or modified.
    -   The access time (atime), which is when the data was last accessed.
-   Metadata tracks where the data is stored on the storage system. It tracks which blocks on the drives were used to store the data.
-   Metadata also contains information about the data owner and access permissions: who owns the data and who can read or modify the data.


### Read-write activity
The operating system determines what controls, if any, are in place to manage access to the data. 

-   Often the operating system uses metadata permissions to control who can access, modify, or delete the data. The operating system can also reference external sources such as Microsoft Active Directory or Lightweight Directory Access Protocol (LDAP) to determine these permissions.
-   The operating system also manages how client access is managed when reading data and modifying data. The operating system determines how clients or applications are notified when another client or application is accessing data.
-   The operating system manages where and when data is written to the block storage. It determines how writes are cached and staged before writing the blocks and which blocks to write to.
-   The operating system also manages the caching or read activity: how are reads cached, what order reads are performed, and how are multiple read requests are managed.

### Locking control
The operating system also manages data integrity when data is being modified or deleted. The operating system can prevent other clients from modifying the data by applying a lock on the entire data file or on specific portions or blocks being modified. These are called file-level locking and block-level locking, respectively. Some operating systems can also place locks on certain block ranges.