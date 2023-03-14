Elastic compute cloud is a highly configurable server.
EC2 is resizable compute capacity.

## Instance Types

### General purpose A1 T3 T3a T2 M5 M5a M4
Balance of compute, memory and networking resources 
**Use-case** web servers and code repositories 

### Compute optimized C5 C5n C4
Ideal fo compute bound applications that benefit from hisgh perfomance processor
**Use-case** scientific modeling, dedicated gaming servers and as server engines

### Memory Optimized R5 R5a X1e High Memory z1d
Fast perfomance for workloads that process large data sets in memory.
**Use-case** in-memory caches, in-memory database, real time big data analysis

### Accelerated optimized P3 P2 G3 F1
Hardware accelators, or co-processors
**Use-case** Machine learning, computational finance, seismic analysis, speech recognirion.

### Storage optimized I3 I3en D2 H1
High sequential and write access to very low data sets on local storage
**Use-case** NsSQL, in-memory or transactional database, data warehousing.

## Instance Profile
Instead of embedding your AWS credentials (Access Key and Secret) in your code so your instance has permissions to access certain service you can attach a role to an instance via an *Instance profile*
An *instance profile* holds a reference to a role. 
When you select an IAM role when launching an EC2 instance, AWS will automatically create the instance profile for you.

## Placement Groups
Placement group lets you choose the logical placement of you instance to optimize for communication, perfomance or durability. 
Placement groups are free.

### Cluster
- Packs the intances close together in an AZ
- low-latancy netowrk performance for tightly-coupled node-to-node communication
- Well suited for high performance computing (HPC) application
- Cluster cannot be multi-AZ

### parition
- Spread instance accross logical partitions 
- each partition do not share the underlying hardware with each other (rack per partition)
- Well suited for large distributed and replicated workloads (Hadoop, Cassandra, Kafka)

### Spread 
- Each instance is placed on different rack
- When critical instances should be keept separate from each other
- You can speacd a max of 7 instaces. Spread can be multi-AZ

## UserData
You can provide an EC2 with UserData which is a script that will automatically run when launching an EC2 instance. You could install packages, apply updates or anything you like.

## MetaData
From within you EC2 instance you can access information about the EC2 via a special urk endpoint

## Pricing model
### On-Demand
- low cost and flexible 
- only pay per hour
- short-term, spiky, unpredictable workloads
- for first time apps

### Reserved upto *75%* off
- steady state or predicatable usave
- commit to EC2 over a 1 or 3 year term
- can resell unused reserved instances.

## Spot upto *90%* 
- request spare computing capacity
- flexible start and end times
- can handle interruptions (server randomly stopping and starting)
- for non-critical background jobs

## Dedicated
- dedicated servers
- can be on-demand or reserved 
- when you need a guarantee of isolated hardware(enterprise requirments)
