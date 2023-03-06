Highly available and scalable cloud domain name system (DNS).
Register and manage domains, create DNS routing rule eg, failovers

You can: 
 - Register and manage domains
 - Create various records set on a domain
 - Implement complex traffic flows eg. Blue/green deploy failovers
 - Continously monitor revord via health checks
 - Resolve VPS outside of AWS

## Use Case
You can use it to get you custom domain to point to you AWS resources
![[route53.png]]

## Record Sets
We create record sets which allow us to point out naked domain and subdomains via Domain records.

AWS has their own special Alias record which extends DNS functionality. It will route trafic to specific AWS resources.
Alias record are smart where they can detect the change of an IP address and continously keep that endpoint to the correct resources.
In most case you want to use alias when routing traffic.

## Routing policies
They are different types of routing policies. 
### Simple routing 
Default routing policy, multiple address result in random selection
- You have one record and provide multiple UP
- When multiple values are specified for a record, Route53 will return all values back to the user in random order.
For example if you had a record for "www.example.com" with 3 different Ip address values, users would be directed randomly to of them when visiting the domain.

### Weighted routing
Route traaffic based on weighted values to split the traffic
- This allows you to send a certain percentage of overall traffic to one server, and have any other traffic apart from that directed to a completely different server.
For example if you had an ALB running experimental features you could test against a small amount of traffic at random to minimize the impact of affect.

### Latency-based routing
- Route traffic to region resources with lowest latency
- Requires a latency resource record to be set for the Ec2 or ELB that hosts you application in each region.
For example you have 2 copies of your web-app backed by ALB. One in California, US and another from Montreal, Canada. A request comes in from Toronto, it will be routed to Montreal since it will have lower latancy.

### Failover routing
Route traffic if primary endpoint is unhealthy to secondary endpoint
- Route53 automatically monitors health-checks from your primary site to determine the health of end-points. If and end-point is determined to be in a failed state, all traffic is automatically directed to the secondary location.
For example, we have a primary and secondary web-app baked by ALB. Route53 determines our primary is unhealthy and fails voer to secondary ALB.


### Geolocation routing
- Route traffic bases on the locations of you users
For example this would let you route all traffic coming from north america to servers located in North American regions, where queries from other regions could be directed to servers hosted in that region.



### Geo-proximity routing
Route traffic based on the location of your resources and, optionally, shift traffic from resources in one location to resource in one location to another location. 
You can route more or less traffic to a specific resource by specifying a 'Bias' value

Bias value extends or shrink the size of the geographic region from which the traffic is routed to.
**You must use Route53 Traffic flow** in order to use geoproximity routing policies.



### Multi-value Answers Routing
Respond to DNS queries with up to eight healthy records selected at random.
Multiple values can be specified for almost any record. Route53 automatically perfoms health-checks on resources and only returns values of ones deemed healthy.

Similar to simple routing, however with and added health chekc for you record set resources.

## Health checks

A health check every 30s by default. Can be reduced to every 10s
A health check can **initial a failover** if status returned is unhealthy
A cloudWatch alarm can be created to alert you status of unhealthy
A health check can monitor other health checks to create a chain of reactions.

## Route Resolver
Formally known as .2 resolver
A regional service that lets you route DNS queries between your VPC and you network.
