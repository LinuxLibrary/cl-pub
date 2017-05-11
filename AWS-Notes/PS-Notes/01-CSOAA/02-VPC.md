# Virtual Private Cloud (VPC)

| About VPC |
-------------
|Amazon Virtual Private Cloud (Amazon VPC) enables you to launch Amazon Web Services (AWS) resources into a virtual network that you've defined. This virtual network closely resembles a traditional network that you'd operate in your own data center, with the benefits of using the scalable infrastructure of AWS.|

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
