# AWS-SAA
My notes on AWS Certified Solutions Architect
To be broken down better 

I will be adding provisioning with terraform for each category i create.

### Latency is measured as the amount of time between making a request to the storage system and receiving the response. Latency is often referred to as delay. Low-latency performance is a primary benefit for block storage.

### Throughput
Throughput is a statistical storage measurement used to measure the performance associated with reading large sequential data files. Large files, such as video files, must be read from beginning to end. Throughput operations are measured in megabytes per second (MB/s).
HDDs are also referred to as spinning disks. HDDs are best suited for applications that require sustained read throughput. Applications that read and write large sequential files, such as video files, are well suited for HDDs. Random read operations are slower due to the seek times to locate the blocks and read them. Write operations to HDDs are also slower because of the seek time to locate and write to the blocks.

### IOPS

Input/output operations per second (IOPS) is a statistical storage measurement of the number of input/output (I/O) operations that can be performed per second. IOPS is also used to measure the number of operations at a given type of workload and operation size can occur per second. IOPS is typically used to measure random I/O read-write activities. Random means that the information used for the read-write activity is usually very small in size and the different information is not related to each other.
Along with the low latency, block storage can often obtain higher IOPS than other types of storage. SSDs are best suited for applications that require high IOPS. SSDs provide the benefit of low latency and higher read and write performance for random I/O. SSDs do not have the seek times required for HDDs and are able to perform operations much faster.

AWS has a lot of the basic regulatory, legal, and security groundwork covered before you even launch your first service.
AWS has invested significant planning and funds into resources and expertise relating to infrastructure administration. Its heavily protected and secretive datacenters, layers of redun- dancy, and carefully developed best-practice protocols would be difficult or even impossible for a regular enterprise to replicate.
Where applicable, resources on the AWS platform are compliant with dozens of national and international standards, frameworks, and certifications, including ISO 9001, FedRAMP, NIST, and GDPR. (See http://aws.amazon.com/compliance/programs for more information.)