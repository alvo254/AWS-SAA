
Provision a logically isolated section of the AWS Cloud where you can launch AWS resources in a virtual network that you can define.
You can also have something called dedicated tenancy which gives co-operataions higher control over the vpc.

## Key features
- VPCs are regional specific they don't span regions
- You can create 5 VPCs per region
- Every region comes with default VPC
- You can have 200 subnets per VPC
- Cost nothing: VPCs, Route tables, Nacls, Internet gateways, security groups and sbunets, VPC peering.
- Some cost money: Nat gatways, VPC endpoints, VPN gateway, Customer gateway
- You can use IPv4 and IPv6 CIDR(s)

# Componets of a VPC
## Subnet 
A range of IP addresses in your VPC.

## Route Table
contains existing routes with targets other than a network interface, Gateway Load Balancer endpoint, or the default local route. The route table contains existing routes to CIDR blocks outside of the ranges in your VPC.
A subnet can only be associated with one route table at a time, but you can associate multiple subnets with the same route table.

## Router
 The process of path selection in any network. A computer network is made of many machines, called nodes, and paths or links that connect those nodes. Communication between two nodes in an interconnected network can take place through many different paths.

## Elastic IP
This is a static public IP address associated with your AWS account in a specific Region. Unlike an auto-assigned public IP address, an Elastic IP address is preserved after you stop and start your instance in a virtual private cloud (VPC)

## Elastic Network Interface
This is basically a virtual network card.
Is a logical networking component in a VPC that represents a virtual network card.

## Internet Gateway
Enables resources in your public subnets (such as _EC2_ instances) to connect to the internet
Does 2 things:
  - Provides a target in your VPC route tables for internet routable traffic
  - Perform network address translation (NAT) for instances that have been assigned public IPv4 addresses/

## Customer Gateway 
Router in your prem
A device is a physical or software appliance that you own or manage in your on-premises network


## VPN 
Is a fully-managed remote access VPN solution used by your remote workforce to securely access resources within both AWS and your on-premises network.

## Virtual private gateway


## VPC Peering
Allows you to connect one VPC to another over a direct network route using private IP address.
- Instances on peered VPC behave just like they are on the same network
- Connect VPCs across same or different AWS accounts and regions
- Peering uses a start configuration: 1 Central VPC - 4 other VPCs
- No transitive peering 
- No overlaping CIDR blocks
If you have more than one AWS account, you can peer the VPCs across those accounts to create a file sharing network. You can also use a VPC peering connection to allow other VPCs to access resources you have in one of your VPCs.



## VPC Endpoints
This are basically connections that allow you to communicate privately with certain AWS services.
Without going out to the internet.
- Eliminates the need for an IG or DX
- Instances in the VPC dont require a public IP address to communicate with servcie resources.
- Traffic between your VPC and other services doesn't leave the AWS network
- Horizontal scaled, redundant and highly available 
- Allow secure communications between instances and service - without adding availability risk or bandwidth constraints on you traffic.
There are 2 types of VPC endpoints:
   - Interface Endpoint - are elastic network interface (ENI) with a private IP address
   - Gateway Endpoint - is a gateway that is a target for a specific route in your route table, used for traffic destined for supported AWS services.
	   - To create a gateway you must specify the VPC in which you want to create the endpoint, and the service to which you want to establish the connection.
	   - Only support DynamoDB and S3 


## NAT Gateway
This enables instances in a private subnet to connect to the internet or other service, but prevent internet from initiating a connection to those instances.

## Bastion/ jumpbox
Bastion are EC2 instances which are a security harden. They are designed to help you gain access to your EC2 instance via SSH or RCP that are in a private subnet.
They are also know as jumpbox because you are jumping from one box to access another.
System manager's **sessions manager** replaces the need for bastions


## Direct connect
Is an AWS solution for establishing **dedicated network** connections from on-prem to AWS

## VPC Flow logs
Allow you to capture IP traffic information in-and-out of network interfaces within your VPC.
Flow logs can be created for: 
  - VPC
  - Subnets
  - Network interfaces
All data is stored using AWS CloudWatch Logs
- VPC flow logs monitor in-and-out traffic of your network interface within your VPC
- they cannot be tagged like other AWS resources
- You cannot change configuration of a flow log after it's created.
- You cannot enable flow logs for a VPC which are peered within your VPC unless it is in the same account.
- Can be deliverd to an s3 or cloudwatch logs
- The contain source and destination IP address

## Network Access Control List (NACLs)
An optional layer of security that acts as a firewall for controlling traffic in and out of subnet(s).
Protect the subnet.
Default allow rule.
Can write allow and deny rules.
Are stateless. - Doesn't keep traffic connections
Rules with IPs.
Each NACL contains a set of rules that allow or deny traffic into (inbound) and out of (outbound) subents.
Rule determines the order of evaluation from lowest to highest.


## Security groups
Protect the EC2 instance
can write allow rules
Default outbound allow rules
Are stateful - Keeps track of connections
Rules with IPs or security group IDS
They are no "Deny" rules all traffic is blocked by default
