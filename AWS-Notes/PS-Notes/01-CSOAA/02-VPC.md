# Virtual Private Cloud (VPC)

***Creating VPC***

- From the AWS console under the Networking group we have VPC
- Select VPC
- To create your own VPC click on *Your VPCs*
- Click *Create VPC*
- Here you need to provide the Name, CIDR and Tenancy
- Another method of doing this is from the VPC Dashboard
- From the VPC Dashboard click on *Start VPC Wizard*
- Here we can find 4 options
	- VPC with single public subnet
	(This one contains a single subnet which wouldn't be available on the public subnet and we need to configure those)
	- VPC with Public and Private subnets
	(This one contains both Public and Private subnets with some NAT rules applied)
	- VPC with Public and Private subnets and Hardware VPN access
	- VPC with a Private subnet only and Hardware VPN access

	> NOTE: Among the above 3rd and 4th options need a Hardware VPN

- Let us go with the basic one which is a single public subnet
- Let us create a subnet with the following options

```
IP CIDR Block 		: 192.168.0.0/16
VPC Name 		: myFirstVPC
Public Subnet 		: 192.168.1.0/24
Availability Zone	: Select one of your AZs
Subnet Name		: myWebAppsSN
Enable DNS Hostnames	: Yes
Hardware Tenancy	: Default
```
