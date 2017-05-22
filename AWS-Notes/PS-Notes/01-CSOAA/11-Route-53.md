# Amazon Route 53

- ***Characteristics***
	- As we have the DNS running on UDP/TCP port no. 53 we have the name as Route 53
	- Amazon has its DNS servers which are distributed worldwide
	- Route 53 has 100% SLA uptime
	- This can be managed through API calls ass well
	- Through Route 53also we can run Server health checks

- ***DNS Record Types***

	Type | Description
	-----|------------
	A | Address Record
	CNAME | Canonical Record Name
	MX | Mail Exchange
	AAAA | IPv6 Address Record 
	TXT | Text Record
	PTR | Pointer Record
	SRV | Server Locator
	SPF | Sender Policy Framework
	NS | Name Server Record
	SOA | Start of Authority Record

- *** Routing Policies***
	- Single
		- Use a simple routing policy when you have a single resource that performs a given function for your domain, for example, one web server that serves content for the example.com website. In this case, Amazon Route 53 responds to DNS queries based only on the values in the resource record set, for example, the IP address in an A record.
	- Weighted
		- Weighted resource record sets let you associate multiple resources with a single DNS name. This can be useful for a variety of purposes, including load balancing and testing new versions of software. To create a group of weighted resource record sets, you create two or more resource record sets that have the same combination of DNS name and type, and you assign each resource record set a unique identifier and a relative weight.
		- When processing a DNS query, Amazon Route 53 searches for a resource record set or a group of resource record sets that have the specified name and type. For weighted resource record sets, Amazon Route 53 selects one from the group.
	- Latency
		- Use the latency routing policy when you have resources in multiple Amazon EC2 data centers that perform the same function and you want Amazon Route 53 to respond to DNS queries with the resources that provide the best latency. For example, you might have web servers for example.com in the Amazon EC2 data centers in Ireland and in Tokyo. When a user browses to example.com, Amazon Route 53 chooses to respond to the DNS query based on which data center gives your user the lowest latency.
	- Failover
		- Use the failover routing policy when you want to configure active-passive failover, in which one resource takes all traffic when it's available and the other resource takes all traffic when the first resource isn't available.
	- Geolocation
		- Use the geolocation routing policy when you want Amazon Route 53 to respond to DNS queries based on the location of your users.
