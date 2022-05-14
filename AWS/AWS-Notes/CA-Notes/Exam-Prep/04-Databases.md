# AWS Databases Exam Preperation

* **Amazon RDS**:
    > RDS is a managed relational database service that supports multiple database engines, specifically Amazon Aurora which is highly performant and cost effective PostgreSQL and MySQL compatible engine
    - A relational database service that provides a simple way to provision, create and scale a relational database
    - Its a managed service, removing any administrative operations
    - Supports a range of different DB Engines including MySQL / MariaDB / Amazon Aurora / PostgreSQL / Oracle / SQL Server
    - Run accross a range of compute sizes and types
    - Deploy your instance in Single AZ or Multi-AZ for HA
    - Multi-AZ configures a second RDS instance within different AZ within same region
    - The second instance acts as a failover for your primary RDS instance
    - The replication of data between your primary and secondary replica happens synchronously
    - During failure RDS will update the DNS record to point to your second instance
    - Aurora storage automatically grows as your database grows
    - RDS provides an automatic backup feature
    - Manual backups can also be taken
    - Aurora backtracks allows you to go back in time on the database to recover from an error
    ---
    *Multi-AZ failove happens when*:
    - Patching maintenance is performed in the primary instance
    - The primary database has a host failure
    - If the AZ of the primary database fails
    - If the primary instance was rebooted with failover
    - If the primary database instance class on the primary instance has changed
---
* **Amazon Aurora**:
    - Fully Managed
    - SQL - MySQL and PostgreSQL
    - Distributed, fault-tolerant, selfhealing storage system that auto scales
    - Replication across 3 AZs
    - Upto 15 low latency read replicas
    - Aurora Multimaster
    - Aurora Serverless
    - Automated failover
    - Point in time recovery
    - Continuous Backups to S3
    - Encryption at rest - KMS customer key
    - Encryption in-transit - SSL
---
* **Amazon DynamoDB**:
    > DynamoDB is a managed serverless NoSQL database service designed for ultra high-performance providing single digit latency
    - DynamoDB is a NoSQL database
    - Designed to be used for ultra high performance at any scale with single digit latency
    - Used commonly for gaming and IoT
    - A fully managed service
    - Easy to configure, you can set a table name and a primary key and accept all other defaults
    - Ability to set the provisioned level of throughput of read and write capacity
    - DynamoDB global indexes let you query across the entire table to find any record that matches a particular value
    - Local secondary indexes can only help find data within a single partitionkey
    - DynamoDB will automatically allocates more space for your table as it grows
    - Encryption of your tables enabled by default, for data at rest
    - Data is automatically replicated accross three different availability zones
    - DynamoDB will be fast no matter how large your table grows, unlike replational database, which can slow down as the table gets large
    - Although DynamoDB performance can scale up as your needs grow, your performance is limited to the amount of read and write throughput that you've provisioned for each table

---
* **Amazon ElastiCache**:
    > ElastiCache is used as an in-memory datastore to improve the read performance of your applications through caching. And is supported by Redis and Memcached
    - ElastiCache makes it easy to deploy, operate, and scale open-source, in-memory datastores in the cloud
    - Improves the performance through cache
    - ElastiCache can be used for any application that can benefit from increased performance using in-memory cache
    - Generally used to improve read-only performance
    - Supports both Memchached and Redis engines
    * **Memcached**:
        - A high performance sub-millisecond latency Memcached-compatible in-memory key store service
        - Can either be used as a cache in addition to your data store
        - Recognized for its speed, performance and simplicity
        - Suits workloads where memory allocation is going to be consistent and the increased-performance is more important than the additional features that Redis offers
    * **Amazon ElastiCache for Redis**:
        - Purely an in-memory datastore designed for high performance and again sub-millisecond latency on a huge scale to real time applications 
        - Offers a more robust set of features to that of Memcached