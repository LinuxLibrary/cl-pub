# Virtual Private Cloud (VPC)

A virtual private cloud (VPC) is a virtual network dedicated to your AWS account. It is logically isolated from other virtual networks in the AWS cloud. You can launch your AWS resources, such as Amazon EC2 instances, into your VPC. You can configure your VPC; you can select its IP address range, create subnets, and configure route tables, network gateways, and security settings.

A subnet is a range of IP addresses in your VPC. You can launch AWS resources into a subnet that you select. Use a public subnet for resources that must be connected to the Internet, and a private subnet for resources that won't be connected to the Internet. For more information about public and private subnets, see VPC and Subnet Basics.

To protect the AWS resources in each subnet, you can use multiple layers of security, including security groups and network access control lists (ACL). For more information, see Security.

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

- With the above options click on Create VPC
- Once its done go to your VPC console and check what it has created by default.

---

***VPC Access Methods***

- Gateway
	- Internet Gateway (IGW): which allows the Ingress and Egress traffic to the VPC
	- Virtual Private Gateway (VPG): which is AWS side secure VPN
	- Customer Gateway (CG): which is customer side secure VPN which can be configured using a Hardware VPN device
- VPN
	- Direct Connect: which is dedicated and isolated, bipases internet and also have HA connectivity supported
	- Hardware Based VPN: which can establish connection from on-premesis to AWS over internet. It supports HA and 3rd party brands

---

***VPC Security***

- Security Groups
	- This is a resource level traffic firewall through which we can control the traffic at instance level say EC2 Instances,ELB, etc.
	- We can control the Ingress and Egress traffic
	- It is stateful as it allows the return traffic
- Access Control Lists (ACL)
	- This is a subnet level traffic firewall which controls the Inbound and Outbound traffic based on the rules set
	- We can filter the traffic based on source and protocols
	- It is stateless as the traffic is filtered strictly. This means the return traffic is not allowed automatically but we need to set rules as needed

---

***VPC Peering***

- It is also called as Inter-VPC routing
- This can be configured for same or different AWS accounts
- Strictly no overlapping of network adresses. Means we should not use the same IP ranges for the VPCs we are trying to connect to
