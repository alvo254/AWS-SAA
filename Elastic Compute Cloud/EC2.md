This is a highly configurable server.
Is resizable compute capacity.

## Instance Types

### general purpose
**A1, T3, T3a, T2, M5, M5a, M4**
- Balances of compute, memory and networking resources use-cases web servers and code repositories.

### Compute Optimized
**C5, C5n, C4**
Ideal for compute bound applications that benefit from high performance processor
use-cases scientific modeling, dedicated gaming servers and ad server engines

### Memory Optimized 
**R5, R5a, X1e, X1, High Memory, z1d**
Fast performance for workloads that proccess large data sets in memory.
use-case in-memory caches, in-memory database, real time big data analytics

### Accelerated Optimized
**P3, P2, G3, F1**
Hardware accelerators, or co-processors
Use-case machine learning, computational finance, seismic analysis, speech recognition

### Storage Optimized
**I3, i3en, D2, H1**
High, sequential read and write access to very large data sets on local storage 
use-case NoSQL, in-memory or transactional database, data warehousing.

## Instance Profile
Instead of embedding you AWS credentials (access key and secret) in your code so you instance has permissions to access certain services you can attach a role to an instance via instance profile.

An instance profile holds a reference to a role. The EC2 instacnce is associated with the instance profile. When you select an IAM role when launching an EC2 instance, AWS will automatically create the instance profile for you. Instance profiles are not easliy viewed via the AWS console.


## Placement Groups
This helps you choose the logical placement of your instance to optimize for communication, performance or durability. 
They are free
#### Clusters
- Pack instances close together in an AZ
- Low-latency network perfomance for tightly-coupled node-to-node communication
- Well suited for High performance computing (HPC) applications
- Cluster cannot be a multi-AZ

#### Partition
- Spreads instances acress logical partitions
- Each partition do not share the underlying hardware with each other (rack per partition)
- Well suited for large distributed and replicaed workloads (Hadoop, Cassandra, Kafka)

#### Spread
- Each instance is placed on a different rack
- When critical instances should ekkp separate from each other 
- You can spread a max of 7 instances. Spread can be a multi-AZ

## UserData
You can provide and EC2 with UserData which is a script that will be automatically run when launching an EC2 instance. 

## Metadata
Is additional information about your EC2 which you can get at runtime

## EC2 pricing Model

## On-Demand
When you launch an EC2 instance its by default using On-Demand pricing. This has no up-front payment and no long-term commitment.
You are charged by the hour or by the minute.

## Reserved Instances (RI)
Designed for applications that have a steady-state, predictable usage, or require reserved capacity.
Reduces pricing is based on  **Term x Class  Offering x Payment option**
**Standard** upto 75% reduced pricing compared to on-demand.
- cannot change RI attributes.

**Convertible** up to 54% reduced pricing compared to on-demand.
- Allows you to change RI attributes if greate or equal to value.

**Schedlude** You reserve instances for a specific time period eg. Once
a week for a few hours. savings vary

##### RIs can be shared between multiple accounts within an org
##### Unuses RIs can be soled in the Reserved instance marketplace.
##### This is also the best long-term.

## Spot Instance
Aws has unused compute capacity that they want to maximize the utility of their idle servers.
Its like when a hotel offers discount to fill vacant suites.
- A spot instance provides a discount of 10% compared to On-Demand pricing.
- Spot instance can be terminated if the computing capacity is needed by on-demand customers.
- **AWS batch** is an easy and convenient way to use spot pricing.
##### Termination conditions
- Instance can be terminated by AWS at anytime
- If your instance is terminated by AWS, you dont get charged for a partial hour of usage
- If you terminate an instance you will still be charged for an hour that it ran

##### This offers biggest savings

## Dedicated Host Instances
Designed to meet regulatory requirements. When you have strict server-bound licensing that wount support multi-tenancy or cloud deployments.
*Multi-Tenant* - When multiple customers are running workloads on the same hardware. Virtual isolation is what separates customers.

*Single Tenant* - When a single customer has dedicated hardware physical isolation is what separates customers. 

Offered in both On-demand and Reserved(70% off on-demand pricing

##### Enterprise and large organizations may have security concerns or obligations about sharing the same hardware with other AWS customers.

