# Route Tables

A route table contains set of rules, called routes, that are used to determine where the network traffic is routed.

> The default VPC already will have a main Route Table.

> To have a better understanding about the Route Tables we need to go through the Basic Networking concepts.

- If we have networks of different classes say Class-A, Class-B and Class-C by default we can't route our traffic from one network to another.
- We split a network into multiple subnets to prevent IP wastage and also to have some additional security.
- It is also impossible to have connection between different subnets even those belong to same network.
- In such cases we need to route our traffic from one network to another or else from one subnet to another.
- Whenever we have a physical network we'll use a router to route the traffic.
- In such case we'll add our networks or subnets to a route table in the router.
- The list of networks we are using is referred to as route table.
- Same thing is being done in AWS Route Tables.

Follow the below navigation to add your routes to the route table.
- Go to VPC console
- Route Tables
- Select your Route Table
- Go to the Routes Tab
- Click edit and add your networks and the Internet Gateway
- If you have multiple subnets within a network then click on Subnet Association tab
- Click Edit and select all your subnets and save

> We can have multiple Route tables within a VPC. We should not delete the route table if it has dependencies.
