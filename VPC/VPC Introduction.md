Provision a logically isolated section of the AWS Cloud where you can launch AWS resources in a virtual network that you can define.
You can also have something called dedicated tenancy which gives co-operataions higher control over the vpc.

# Componets of a VPC
## Subnet 
A range of IP addresses in your VPC.

## Route Table
contains existing routes with targets other than a network interface, Gateway Load Balancer endpoint, or the default local route. The route table contains existing routes to CIDR blocks outside of the ranges in your VPC

## Router
 The process of path selection in any network. A computer network is made of many machines, called nodes, and paths or links that connect those nodes. Communication between two nodes in an interconnected network can take place through many different paths.

## Elastic IP
This is a static public IP address associated with your AWS account in a specific Region. Unlike an auto-assigned public IP address, an Elastic IP address is preserved after you stop and start your instance in a virtual private cloud (VPC)

## Elastic Network Interface
This is basically a virtual network card.
Is a logical networking component in a VPC that represents a virtual network card.

## Internet Gateway
Enables resources in your public subnets (such as _EC2_ instances) to connect to the internet

## Customer Gateway 
Router in your prem
A device is a physical or software appliance that you own or manage in your on-premises network


## VPN 
Is a fully-managed remote access VPN solution used by your remote workforce to securely access resources within both AWS and your on-premises network.

## Virtual private gateway


## VPC Peering
if you have more than one AWS account, you can peer the VPCs across those accounts to create a file sharing network. You can also use a VPC peering connection to allow other VPCs to access resources you have in one of your VPCs


## VPC Endpoints

## NAT Gateway