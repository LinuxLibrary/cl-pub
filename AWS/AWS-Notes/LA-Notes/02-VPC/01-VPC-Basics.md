# VPC Basics

A VPC or a Virtual Private Cloud is what we create with some AWS components and control them within. For a VPC we can have some EC2 instances for computing, RDS instances for Database and also configure network with IP address range we prefer along with subnets, Route tables, Internet Gateways and Network Access Lists.

On creating an AWS account we can see a default VPC configured with some default subnets, Route tables, NACLs and Internet Gateways. We cannot delete the existing default VPC or sny of its settings. We need to prepare other VPCs as of our choice.

For an ec2 instance within a VPC the traffic will be routed as follows.

```
	Internet Gateway -> Route Tables -> NACLs -> EC2 Instance
```

At first out request goes through the Internet Gatewayand the traffic from the IG will be routed to the instance as per the Route Tables and after the Route Tables our request will be verified at the Network Access Control Lists to check whether our traffic can be forwarded to the instance or not. If our traffic can be routed to the instance as per the NACLs then we can access the EC2 Instance.
