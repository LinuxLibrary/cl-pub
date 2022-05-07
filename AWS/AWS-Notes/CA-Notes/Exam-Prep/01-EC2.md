# AWS EC2 Exam Preperation

* **AMIs and Instance Types**:
    - AMIs are digital templates of pre-configured EC2 Instances allowing you to quickly launch a new instance
    - You have the choice of AWS Managed, custom, market place and community AMIs

* **Instance Types**:
    - Instance types are defined ny different parameters and their values such as amount of memory, network performance, storage etc.
    - As your instance size gets bigger, the parameter values (vCPU, network performance, storage) also increases
    - Some instances only support EBS and do not support for ephermal storage
    - General purpose instances gives a good balance of compute, memory and network resources, so its great for lots of different use cases
    - Compute optimized instances are designed for compute intensive workloads requiring high performance processors
    - Memory optimized instances help you deliver super fast performance for processing data sets in memory
    - Accelerated computing instance types use hardware accelerators which are great for graphics and data pattern matching
    - Storage optimzed instances maintain low latency IOPS and sequential read and write access to massive data sets locally

* **EC2 Purchase Options**:
    * **On-Demand Instances**:
        - Can be launched at any time
        - Provisioned and available within minutes
        - No duration limit
        - A flat cost rate paid by the second
        - Suitable for short time workloads
        - Used for irregular an interruptible workloads
        - Stop paying when the resource is stopped or terminated
    * **Spot Instances**:
        - Bid for unused EC2 compute resources
        - Huge cost saving can be achieved
        - There is no assurance that you will have spot instances for a fixed period of time
        - The instance is purchased when your bid price is higher than the fluctuating spot price
        - Spot price fluctuates depending on the supply and demand of the unused resources
        - If your bid price drops below spot price a two minute warning is issued before the instance automatically terminates
        - Useful for workloads that can be suddenly interrupted
    * **Reserved Instances**:
        - Purchase instances at a discounted rate over a 1 or 3 year period
        - Savings can be as much as 75% compared to on-demand instances
        - All upfront payment allows you to pay the entire resource for a single or three year period, and provides the biggest discount
        - Partial upfront payment allows you to pay a partial upfront and then a discount is applied to any hours used by the instance
        - No upront payment gives the smallest discount of the 3 options
        - Used for long term predictable workloads
    * **Scheduled Instances**:
        - Pay for the reservation of an instance on a recurring schedule, either daily, weelky or monthly
        - You are charged for the instance even if you don't use it
        - Used to run scheduled workloads that are not running continuously
    * **Capacity Reservations**:
        - Reserve capacity for EC2 instances based on attributes such as instance type, platform and tenancy etc.
        - Reserved within particular availibility zone for a period of time
        - Ensures you have capacity when its required
        - Can also be used in conjunction with your reserved instances discount providing you additional savings
    
* **EC2 Tenancy**:
    - Tenancy relates to how many customers are using the underlying hardware that your EC2 instance is running on
    - By default, your instance will run on shared tenancy
    - Dedicated tenancy ensures that your AWS account is the only account to run the EC2 instances on a single host
    - Dedicated tenancy can be used to meet security compliance controls
    - Dedicated tenancy comes at an increased cost
    - Dedicated hosts have the same principle as the dedicated instance, but provides additional flexibility and control
    - Dedicated hosts provide EC2 instance placement control and host recovery

* **User Data & Meta Data**:
    * **User Data**:
        - User data allows you to run commands during the first boot cycle of your new instance
        - Useful to install software from a repository or perform OS updates
    * **Meta Data**:
        - Used to gather and query instance data that is running, such as hostnames, events and security groups etc.
        - Navigate to http://169.254.169.254/latest/meta-data/ to retrieve instance metadata

* **EC2 Storage**:
    - 2 types of storage. Ephermal and EBS
    - Ephermal storage physically resides on the same host as the EC2 instance
    - Ephermal storage is temporary, if the instance stops or terminates the data will be lost. If it just restarts then the data is retained
    - EBS provides persistant storage as volumes
    - If your instance is stopped or terminated, EBS will retain your data
    - EBS volumes can be encrypted if you are storing sensitive data
    - EBS backups can be taken as snapshots and stored on Amazon S3

* **EC2 Security**:
    - Key pairs are used to encrypt the credentials to the instance
    - Being a key pair, there is a Public Key and a Private Key
    - The public key encrypts the username and password for the Windows instance
    - The private key is used to decrypt this data
    - Connectivity to Windows instances is managed over RDP (3389)
    - For Linux instances the private key is used in conjunction with the public key to remotely connect onto the instance via SSH (22)
    - The public key is held and kept by AWS
    - The private key is kept by you and you only have one opportunity to download it when its created
    - You can use the same key pair for multiple instances

* **EC2 AutoScaling**:
    - Allows you to automatically increase or decrease your EC2 resources to meet demands of your applications based on defined metrics and thresholds
    - Optimizes the cost of your EC2 instances by scaling in resources that are no longer required
    - *Scaling-Up*: Increasing the compute power of your instance. For example going from M3-Large to an M3-XLarge
    - *Scaling-Out*: Adds more instances of the same instance type. For example going from 2 M3-Large instances to 4 M3-Large instances
    - Launch templates outline the AMI, instance type, IP requirements, storage etc., when launching a new instance
    - Autoscaling groups define the desired capacity of the group using scaling policies and which AZs should be used

* **Elastic LoadBalancer**:
    - ELBs help control the flow od inbound requests destined to a group of targets
    - Requests are distributed evenly across the targeted resource group
    - Targets can be a fleet of EC2 Instances, Lambda Functions, a range of IP addresses or even containers split across different AZs or in a single AZ
    - Internet facing ELBs re accessible via internet and so have a public DNS name which can be resolved with public IP address
    - Internal ELB only has an internal IP address. It will only serve requests that originate within your VPC itself
    - ELBs will automatically scale to meet your incoming traffic
    - To receive encrypted traffic over HTTPS your ELB needs a server certificate
    - The certificate should be issued by a Certificate Authority (CA) which could be the AWS Certificate Manager (ACM)
    - ELB allows you to manage loads across your target groups where as EC2 autoscaling allows you to automaticlly scale those target groups baed upon the demand
    - There are 3 types of ELB: Application / Network / Classic
    
* **LoadBalancer Types**:
    * **Application ELB**:
        - Operates at the Application layer
        - When it receives a request, it uses the configured listeners and rules to determine which target group to direct traffic to
        - Offers a flexible feature set for web apps running HTTP/HTTPS
        - Offers TLS termination
        - Cross-zone loadbalancing is always enabled
    * **Network LoadBalancer**:
        - Operates at layer 4 of the OSI model
        - Balance request purely based on the TCP and UDP protocols
        - Ultra-high performance with low latency
        - Capable of handling millions of requests a second
        - Cross-zone loadbalancing on the NLB can be enabled or disabled
    * **Classic LoadBalancer**:
        - Minimal feature set
        - It is considered best practice to use the ALB over the classic load balancer
        - Used for application running in the EC2 classic network

* **AWS Lambda**:
    - AWS Lambda is a serverless compute service designed to run application code without having to manage and provision your own EC2 instances
    - You only pay for compute power when Lambda functions are invoked
    - In addition to compute power, you are also charged based on the number of times your code runs
    - You can upload your code using the Management Console, AWS CLI or he SDK
    - Lambda functions execute your code upon specific triggers from supported event sources such as S3
    - Event sources are AWS services that can be used to trigger your Lambda functions
    - Downstream resources are resources that are required during the execution of your Lambda function
    - Logging streams help you identify if your code is operating as expected
    - Event sources can be poll or push-based
    - Event source mapping is the confugaration that links your event source with your Lambda function
    - Monitoring statistics related to your Lambda function within Cloudwatch is configured by default
    - A dead-letter queue is used to receive payload that are not processed due to a failed execution
    - The number of invocations determines how many times the function has been invoked