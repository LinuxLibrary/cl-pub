# Working with Securities in AWS

- Security Groups
	- This is a firewall which can be applied at the resource level
	- Through the SGs we can control the Ingress and Egress traffic
	- It is stateful which allows the return traffic

- Network Access Control Lists (NACLs)
	- This is a firewall which can be applied at the subnet level
	- We need to have separate Inbound and Outbound traffic rules
	- It is stateless as we need to specify each and every rule as per our choice and it doesn't allow the return traffic
