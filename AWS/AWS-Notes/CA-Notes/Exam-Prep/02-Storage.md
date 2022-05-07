# AWS Storage Exam Preperation

* **Amazon Simple Store Service (S3)**:
    - Promoted as having unlimited storage capabilities making Amazon S3 extremely scalable.
    - Limitations on the individual size of a single file that it can support. 
    - The smallest size it supports is 0 Bytes and the largest size it supports is 5 Terrabytes.

    * **Storage Classes**:
        * **S3 Standard**: Considered a general purpose storage class. Ideal for a range of use cases where you need high throughput/low latency with frequent access to your data.
        * **S3 Intelligent Tiering**: Used when the frequency of access is unknown. Depending upon your data access patterns it will move your objects between frequent and infrequent access tiers, optimizing storage costs automatically.
        * **S3 Standard Infrequent Access**: Designed for data that does not need to be accessed frequently, yet still offers high throughput/low latency access.
        * **S3 One Zone Infrequent Access**: Being an infrequent storage class it is designed for objects that are unlikely to be accessed frequently. Durability remains at 11 9's but only across a single AZ.
    * **Lifecycle Rules**:
        - It provides an automatic method of managing the life of your data while it is being stored in Amazon S3.
        - Ability to configure and set specific criteria that will automatically move data from one class to another for cost optimization or compliance.
        - Once enabled on a bucket it can only be suspended, not disabled.
    * **Transfer Acceleration**:
        - Use transfer acceleration to speed up long-distance S3 data transfers.
        - Uses Edge locations to distribute traffic worldwide.
        - S3 operations not supported by transer acceleration.
            - GET Service (List buckets)
            - PUT Bucket (Create Bucket)
            - DELETE Bucket
            - Cross region copies using PUT object - copy.
    * **Versioning**:
        - Allows multiple versions of the same object to exist.
        - Retrieve previous versions of a file, or recover a deleted file.
        - Versioning is not enabled by default, however once you have enabled it, you can't disable it, you can only suspend it.
        - Additional storage costs as you are storing multiple versions of the same file.
    * **Security**:
        - Access to S3 resources can be controlled using both identity based policies and resource based policies.
        - Identity based policies are attached to the IAM identity requiring access.
        - Resource based policies are associated with the S3 bucket.
        - Bucket policies are attached to buckets and require "Principle" which defines the identity and permissions apply to.
        - You can grant cross-region access using bucket policies without having to create and assume roles that are created within IAM.
        - You can use both IAM policies and bucket policies to control access.
        - S3 access control lists allow you to control access to buckets in addition to specific objects within a bucket by groupings and AWS accounts.
        - It is not possible to implicitly deny access using ACLs.
        - All policies will be evaluated togather to determine the resulting access in accordance with the principle of least privileged.
        - By default all public access is blocked.
        - Cross Origin Resource Sharing, allows specific resources on a webpage to be requested from a different domain than its own.
        - You can utilize CORS support to access resources stored in S3.

* **Amazon Glacier**:
    * **S3 Glacier**: The default standard storage class with in S3 Glacier offering a highly secure using in transit and at rest encryption low cost and durable solution. Offers a variety of retrieval options depending on how urgently you need the data back, each offering a different price point.
    * **S3 Glacier Deep Archive**: The cheapest of all options focusing on long-term storage.
    * **S3 Glacier Retrieval Options**:
        * **Expedited**: Used for urgent requirements which can be made available to you in 1-5 mins if your data being retrieved is below 250MB. This is the most expensive retrieval options
        * **Standard**: Can retrieve any of your archives regardless of size. Data available in 3-5 hours
        * **Bulk**: Used to retrieve petabytes of data at a time and takes between 5-12 hours. This is the cheapest of the retrieval options.

* **Amazon Elastic File System (EFS)**:
    - EFS is a fully managed, highly available and durable service that allows you to create shared file systems that can easily scale upto petabytes in size with low latency access.
    - There are 2 different storage classes.
        - EFS Standard
        - EFS Infrequent-Access (IA)
    - A cost saving of upto 92% can be achieved with EFS-IA.
    - With EFS-IA there is an increased first-byte latency impact when both reading and writing data.
    * **Lifecycle Management**:
        - EFS will automatically move data between Standard storage and EFS-IA storage class.
        - Occurs when a file has not been read or written to for a set period of days.
        - EFS will move the data to the IA storage class to save on cost once that period has been met. If the same file is accessed again, the timer is reset, and it is moved back to standard storage class.
    * **Encryption**:
        - EFS supports both encryption at rest and encryption in transit.
        - Encryption at rest is managed by integrating with KMS.
    * **Performance & Throughput**:
        - 2 performance modes:
            - *General Purpose*: Default performance mode and typically used for most use cases.
            - *Max I/O*: Offers virtually unlimited amounts of throughput and IOPS.
        - 2 throughput modes:
            - *Bursting Throughput*: The default mode, the amount of throughput scales as your filesystem grows. So the more you store, the more throughput is available to you.
            - *Provisioned Throughput*: Allows you to burst above your allocated allowance, which is based upon your filesystem size.
    - Uses AWS DataSync to migrate data into EFS.

* **Amazon Elastic Block Store (EBS)**:
    - It is a block level storage
    - Understand the difference between the two storage types
        1. SSD backed storage
            - *General Purpose SSD (gp2)*:
                - Balances price and performance for a wide variety of workloads
                - *Use Cases*:
                    - Recommended for most workloads
                    - System boot volumes
                    - Virtual desktops
                    - Low latency interactive apps
                    - Development and test environments
            - *Provisioned IOPS SSD (io1)*:
                - Highest performance SSD volume for mission-critical low-latency or high-throughput workloads
                - *Use Cases*:
                    - Critical bussiness applications that requires sustained IOPS performance, or more than 16000 IOPS of 250 MiB/s of throughput per volume
                    - Large database workloads (MongoDB, Cassandra, Microsoft SQL Server, MySQL, PostgreSQL, Oracle) 
        2. HDD backed storage
            - *Throughput Optimized HDD (st1)*:
                - Low-cost HDD volume designed for frequently accessed, throughput-intensive workloads
                - *Use Cases*:
                    - Streaming workloads requiring consistent, fast throughput at a low price
                    - Big Data
                    - Data Warehouses
                    - Low Processing
                    - Cannot be a boot volume
            - *Cold HDD (sc1)*:
                - Lowest cost HDD volume designed for less frequently accessed workloads
                - *Use Cases*:
                    - Throughput-oriented storage for large volumes of data that is infrequently accesed
                    - Scenerios where the lowest storage cost is important
                    - Cannot be a boot volume
    - Data is persistant and durable even if you terminate/restart an EC2 instance
    - Provisioned IOPS (Input Output Operations per Second)
    - Flexibility: The volume can be elastically scaled within the console or via the AWS-CLI
    - They can only be attached to resources within the same AZ
    - Ability to create point in time snapshots either manually or using Amazon CloudWatch Events
    - Volumes can be encrypted using the KMS service
    
    * **Snapshots**:
        - EBS offers the ability to provide point in time backups of the entire volume as and when you need to using snapshots
        - Can be manually invoked at amy time
        - Can be automated on a recurring schedule using Amazon CloudWatch events
        - Snapshots are stored on Amazon S3 and so are very durable and reliable
        - Snapshot backups are incremental, so each snapshot will only copy data that has changed since the precious snapshot was taken
        - A new volume can be created from an existing snapshot
        - You can copy a snapshot from one region to another
        - Any snapshot taken from an encrypted volume will also be encrypted
        - Any volume created from an encrypted snapshot will be encrypted
        - You can't create an encrypted snapshot from an unencrypted volume
        - You can't create an unencrypted snapshot from an encrypted volume

* **Amazon FSx**:
    - Amazon FSx is another storage service that focuses on filesystems
    - FSx comes in 2 forms, Amazon FSx for Windows File Server, Amazon FSx for Lustre
    - Each FSx has been designed for very different needs and requirements
    - We can summarize the differences as shown below
    * **Amazon FSx for Windows File Server**:
        - Provides fully managed native Microsoft Windows Filesystem on AWS
        - Easily move and migrate your windows based workloads requiring file storage
        - The solution is built on Windows Server
        - Operates as Shared File Storage
        - Uses SSD storage for enhanced performance and throughput providing sub-millisecond latencies
        - Full support for 
            - SMB Protocol
            - Windows NTFS
            - Active Directory Integration
            - Distributed File System
    * **Amazon FSx for Lustre**:
        - A fully managed filesystem designed for compute intensive workloads, for example Machine Learning and HPC
        - Ability to process massive datasets
        - Performance can run upto hundreds of GB per second throughput, millions of IOPS and sub-millisecond latencies
        - Integration with Amazon S3
        - Supports cloud bursting workloads from on-premises over Direct-Connect and VPN connections

* **AWS Storage Gateway**:
    - Storage gateways offer three different configurations and options
    1. *File Gateways*:
        - Allow you to securely store your files as objects within S3
        - Mount or map drives to an S3 bucket as if the share was held locally on your own corporate network
        - Files are sent to S3 over HTTPS and encrypted SSE-S3
        - A local on-premise cache is provisioned for accessing your most recently accessed files to optimize latency
    2. *Volume Gateways*:
        1. *Stored Volume Gateways*:
            - Often used as a way to backup your local storage volumes to S3 while ensuring your entire data library also remains locally on premise for very low latency data access. Volumes are backed by Amazon S3.
            - Volumes are mapped to your on premise storage devices
            - Data is written to your local storage services(NAS, SAN or DAS) and then asynchronously copied to S3 as EBS snapshots
            - Having your entire dataset remain locally ensures you have the lowest latency possible to access your data
            - A buffer is used as a stagging point for data that is waiting to be written to S3
        2. *Cached Volume Gateways*:
            - The primary data storage is on S3 rather than your own local storage solution
            - Cached volume gateways utilize your local data storage as a buffer and a cache for recently accessed data
            - The volumes themselves are backed by the Amazon S3
    3. *Tape Gateways*:
        - Known as gateway VTL, Virtual Tape Library
        - Backup your data to S3 from your own datacenter leveraging Amazon Glacier for data archiving
        - Essentially a cloud based tape backup solution, replacing physical components with virtual ones.

* **Persistance of data with EC2 instances**:
    - EBS Volume
    - Block Storage
    - EBS Snapshots as backups
    - Encryption is possible with EBS
* **Network FileSystems**:
    - EFS
    - NFS Protocol
    - Mount points for connecting your EC2 instances
    - Multiple Availibility zones
    - Encryption in-transit and at-rest
    - Throusands of concurrent connections
* **Windows FileSystems using Server-Message-Block**:
    - Amazon FSx for Windows
    - File systems for HPC using Linux instances - Amazon FSx Lustre
* **Backups between your datacenter and AWS using S3 or Glacier**:
    - AWS Storage Gateway. Either using File, Volume or Tape Gateways