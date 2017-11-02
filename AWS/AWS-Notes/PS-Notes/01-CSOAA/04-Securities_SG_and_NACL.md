# Working with Securities in AWS

- Security Groups
	- This is a firewall which can be applied at the resource level
	- Through the SGs we can control the Ingress and Egress traffic
	- It is stateful which allows the return traffic
	- We can have 100 SGs per VPC
	- A SG can have 50 rules
	- We can have a max of 5 SGs per instance
	- Default SG allows communication from other instances in the same SG 
	- Denies all inbound traffic until allow
	- Able to configure Allow rules only
	- Allow all outbound until allow

	> NOTE: Instances can't communicate unless allowed

	> Destination port filtering only (no source port filtering)

- Network Access Control Lists (NACLs)
	- This is a firewall which can be applied at the subnet level
	- We need to have separate Inbound and Outbound traffic rules
	- It is stateless as we need to specify each and every rule as per our choice and it doesn't allow the return traffic
	- Default rule is Deny All
	- Through NACLs we can write permit and deny rules
	- We can attach 1 NACL per a subnet
	- Lower numbers are processed first and stop on first match
	- Leave gaps while configuring rules (ex. don't give the rule number immediate next keep some 50 or 100 or else some difference)
