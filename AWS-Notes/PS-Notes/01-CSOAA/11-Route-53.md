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
	- Single / Simple Routing Policy:
		- Simple routing policy is a simple round robin policy and can be applied when there is a single resource doing the function for the domain for e.g. web server that serves content for the website
		- AWS Route 53 responds to the DNS queries based on the values in the resource record set for e.g. ip address in an A record
	- Weighted
		- Weighted routing policy enables Route 53 to route traffic to different resources in specified proportions (weights) for e.g., 75% one server and 25% to the other during a pilot release
		- Weights can be assigned any number from 0 to 255
		- Weighted routing policy can be applied when there are multiple resources that perform the same function for e.g., webservers serving the same site
		- Weighted resource record sets let you associate multiple resources with a single DNS name
		- Common use cases include
			- load balancing
			- A/B testing and piloting new versions of software
		- To create a group of weighted resource record sets, two or more resource record sets can be created that have the same combination of DNS name and type, and each resource record set is assigned a unique identifier and a relative weight.
		- When processing a DNS query, Route 53 searches for a resource record set or a group of resource record sets that have the specified name and type.
		- Route 53 selects one from the group. Probability of any one resource record set being selected depends on its weight as a proportion of the total weight for all resource record sets in the group for e.g., suppose for www.example.com has three resource record sets with weights of 1 (20%), 1 (20%), and 3 (60%)(sum = 5). On average, Route 53 selects each of the first two resource record sets one-fifth of the time, and returns the third resource record set three-fifths of the time.
	- Latency
	- Failover
	- Geolocation
