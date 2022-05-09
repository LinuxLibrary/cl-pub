# AWS Networking Exam Preparation

* **Virtual Private Clouds (VPCs)**:
    - A VPC resides inside of the AWS cloud and it's essentially your own isolated segment of the AAWS Cloud itself
    - By default when you create your VPC only your account has access to it
    - VPC allows you to deploy resources within your own secure environment, such as compute, storage, database, etc
    - You are allowed up to 5 VPCs per region per AWS account
    - When you create your VPC you must define a CIDR IP Block (/16 - /28)
    - Management network components include Subnets / NACLs / Security Groups / NAT Gateways / Internet Gateways / Route Tables / Direct Connect / VPN Gateways

* **Networking Components**:
    * **Subnets**:
        - Used to segment your VPC into multiple networks
        - Each subnet has it's own IP range which falls in the VPC CIDR Block range
        - Public and Private subnets
        - A public subnet is accessible from outside of your VPC
        - Resources in public subnet must have a public IP address
        - Public subnets require an IGW and a route pointing to the IGW
        - Resources in private subnet are inaccessible from internet
        - Each subnet exists in a single AZ

    * **Security Groups**:
        - Filter traffic both inbound and outbound at the instance level
        - All the rules within the SG will be assessed before a decision is made on the action 
        - Allow rules only (deny rules not possible)
        - They have both inbound and outbound rule sets
        - Security groups are stateful

    * **NACLs**:
        - Virtual network level firewalls associated to subnets
        - Control ingress and egress traffic between subnets
        - The default NACL allows ALL traffic
        - Each entry has a rule number
        - NACL is read in rule order
        - NACLs are stateless

    * **Internet Gateway (IGW)**:
        - A managed component that can be attached to your VPC
        - Acts as a gateway between your VPC and outside world
        - Allows resources in the public subnet to access the internet

    * **NAT Gateway**:
        - A NAT gateway sits within the public subnet with an EIP
        - NAT GW allows private resources to access the internet
        - Private subnets need a route to the NAT GW to access it
        - It will block all incoming communications from the internet

    * **Virtual Private Network (VPN)**:
        - To enable communication between VPC resources and those in a datacenter you can use a VPN connection accross the public internet
        - In your VPC you must attach a Virtual Gateway (VGW)
        - In your datacenter you must add a Customer Gateway (CGW) (a hardware or software appliance)
        - The customer gateway has an endpoint attached to the virtual private gateway
        - Dynamic or static routing can be configured
        - Initiate a tunnel between the two end points which can only be done from your customer gateway
        - Configure the necessary routing to enable communication over the VPN link

    * **Direct Connect**:
        - Direct connect enables you to create a private connection between your data center and AWS region, not just a VPC
        - Your Datacenter will connect to an AWS Partner using dedicated links which contain Direct Connect Infrasturcture
        - This is a separate building to your remote Datacenter
        - You can configure private virtual interfaces and also public virtual interfaces on your router for DC
        - Private virtual interfaces will connect to a virtual gateway in your VPC
        - Public virtual interfaces connects to an AWS region allowing access to the public resources such as Amazon S3
        - Offers high speed network connectivity to AWS

* **VPC EndPoints**:
    - There are 2 types of VPC endpoints
        - *Interface Endpoints*: During the creation of an interface endpoint for a service, a DNS hostname is associate with a private hosted zone in your VPC. In this hosted zone a record set for the default DNS name for the service is created resolving to the IP address of your resolving endpoint. Applications already using that service do not need to be reconfigured, requests to that service using the default DNS name will now be resolved to the private IP address of the interface endpoint and will route through the internal AWS network instead of the internet.
        - *Gateway Endpoints*: Act as target used within your route tables to allow you to reach supported services(S3 and DynamoDB). During the creation of your gateway endpoint you specify which route tables to be updated to add the new target of the Gateway endpoint. Any route table selected will have a route automatically added to include the new gateway endpoint. The entry of the route will have a new prefix list ID of the associated service (S3 or DynamoDB) and the target entry will be the VPC endpoint ID. Gateway endpoints only works with IPv4.

* **Networking Features**:
    * **Elastic IP Address (EIP)**:
        - EIPs provide a persistant public IP address that you can associate with your instance
        - The IP address is associated with your account rather than your instance
        - You can attach an EIP to an instance or an Elastic Netwoek Interface (ENI)
        - You can also detach the EIP from an instance and re-attach to another instance
        - Any unused EIPs will incur cost

    * **Elastic Network Interfaces (ENI)**:
        - ENIs are logical virtual network cards within your VPC
        - They can be attached to your EC2 instances
        - The configuration is bound to the ENI and not the instance that it is attached to
        - You can detach your ENI from one instance and re-attach it to another instance
        - Useful to create a management network

    * **Elastic Network Adapter (ENA)**:
        - Provides enhanced networking speeds to reach speeds upto 100Gbps for your linux compute instances
        - They are not supported for all instances (must be running kernel versions 2.6.32 and 3.2 and above)
        - Offers higher bandwidth with increased packet per second (PPS) performance
        - Offered to no extra cost, and is included with the latest version of the Amazon Linux AMI

* **AWS Global Accelerator**:
    - Allows you to get UDP and TCP traffic from your end user clients to your applications faster, quicker and more reliably using the AWS global infrastructure and specified endpoints
    - It uses two static IP addresses associated with a DNS name which is used as a fixed source to gain access to your application
    - These IP addesses can be mapped to multiple different endpoints
    - Global accelerator intelligently routes customers requests across the most optimized path
    - There are 4 steps to setup AWS Global Accelerator:
        1. Create your accelerator, select 2 IP addresses
        2. Create a listener to receive and process incoming connections based upon protocols and ports (UDP or TCP)
        3. Associate the listener with an endpoint group. Each endpoint group is associated with a different region, and within each group there are multiple endpoints
        4. Associate and register your endpoints for your applications. Either an ALB, NLB, an EC2 instance or an EIP

* **Amazon Route 53**:
    - A highly available and scalable DNS, providing secure and reliable routing requests
    - Uses the AWS global network of authoritative DNS servers to reduce latency
    - Hosted Zones: A container that holds information about how you want to route traffic for a domain
    - Public Hosted Zones: Determines how traffic is routed on the internet
    - Private Hosted Zones: Determines how traffic is routed within a VPC
    - Generic Top Level Domains (TLD): TLDs are used to help determine what information you might expect to find on the website
    - Geographic Domains: Used to represent the geographical location of the site itself
    - Resource record types: Route 53 supports the most common types
    - Alias records: Acts as a CNAME record allowing you to route your traffic to other AWS resources, such as ELBs, VPC Interface Endpoints, etc.

    * **Routing Policies**:
        - *Simple Routing Policy*: This is the default policy and it is for single resources that perform a single function
        - *Failover Routing Policy*: This allows you to route traffic to different resources based upon their health
        - *Geo-Location Routing Policy*: This lets you route traffic based on the geographical location of your users
        - *Geoprozimity Routing Policy*: This policy is based upon both the users and the resources
        - *Latency Routing Policy*: This is suitable when you have resources in multiple regions and want low latency
        - *Multivalue Answer Routing Policy*: This allows you to get a response from a DNS request from upto 8 records at once that are picked at random
        - *Weighted Routing Policy*: This is suitable when you have multiple resource records that perform the same function. To determine the probability the formula is the weight of the individual resource record divided by the sum of the total value in the resource record set.

* **Amazon CloudFront**:
    - A fault tolerant and globally scalable content delivery network service
    - Speeds up distribution of static and dynamic content through its worldwide network of edge locations providing low latency to deliver the best performance through cached data
    - CloudFront uses distributions to control which source data it needs to redistribute
    - 2 types of distributions: Web distribution and RTMP distribution
    - A CloudFront origin defines where the distribution is going to get the data to distribute across edge locations and it will be the DNS name of the S3 bucket or the HTTP server.
    - For additional security when working with S3 you can create and associate a CloudFront user called an Origin Access Identity (OAI). Only the OAI can access and serve content from your bucket preventing anyone circumventing your CloudFront
    - CloudFront offers ability to different caching behavior options, defining how you want the data at the edge location to be cached via various methods and policies
    - Ability to define the locations of where your data should be distributed to ensure you receive the best performance for your customers.