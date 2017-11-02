# Network Access Control Lists (NACL)

A NACL is an optional layer of security for your VPC that acts as a firewall for controlling traffic in and out of one or more subnets.

> Default VPC already have a NACL associated with the default subnets. This default NACL will allows all in-bound and out-bound traffic by default.

Within the default NACL in the the InBound and OutBound we can see 2 same statements out of which one allows and one denies. We can configure simillar type of rules. For example say I have 2 rules for SSH

- Rule-#1 allows all traffic from 10.0.0.0/16
- Rule-#2 denies all traffic from 10.0.0.0/16

In this case we can access our instances through SSH as ***always NACL rules will be considered based on the rule number from lower to higher***. So our Rule-#1 allows the traffic so we can access our instances.

> If we create a new NACL then by default it will not have the ALLOW rule and will only have the DENY rule. Also we need to add the subnet associations.
