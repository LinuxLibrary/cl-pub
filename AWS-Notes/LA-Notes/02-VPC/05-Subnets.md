# Subnets

A subnet is a short form of sub-network or a subsection of a network.

- If we are about to have our instances in multiple availability zones for Fault Tollarance and High Availability then we can have X number of subnets for X number of AZs with in the region.
- Default VPC will have the same scenario of having multiple subnets for the number of AZs
- If we need some of the resources connected to Internet and some should not then we need to have separate Route Tables.
- For example:
	- We have some EC2 instances in 3 subnets which should have Internet connection
	- We also have a DB instance in a subnet which should not be connected to Internet but should have connection to the EC2 instances
	- We should have a RT say RT-#1 associsted with the subnets in which we have the EC2 instances
	- RT-#1 should have the number of Networks we have along with the IGW as the routes
	- Now we should have another RT say RT-#2 associated with the subnet in which we have the DB instance
	- RT-#2 should have the Networks in which we have the EC2 instances as the routes, but should not have the IGW
- In this way we can have specific Subnets have access to the internet and also can some be Denied to have access to the Internet.

> Public subnets are the subnets which can be accessed through the internet.

> Private subnets can not be accessed through the Internet
