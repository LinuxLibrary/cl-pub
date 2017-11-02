# Elastic Block Storage (EBS)

- Billed on storage capacity and IO
- Does not need to be attached to an instance
- Can be transferred between AZs
- EBS volumes are designed for an annual failure rate (AFR) of between 0.1% to 0.2%
- EBS volume data is replicated accross multiple servers in an availability zone
- SLA is 99.95%

[Amazon EBS Volumes Types](https://aws.amazon.com/ebs/details/)

General Purpose (SSD) | Provisioned IOPS (SSD) | Magnetic
----------------------|------------------------|---------
System boot volumes | I/O intensives | Infrequent Data Access
Virtual Desktops | Relational DBs |
Small to medium DBs | NoSQL DBs |
Dev and Test | | 

---

***EBS - Optimized Instances***

- Dedicated capacity for Amazon EBS I/O
- Available at speeds 500 Mbps to 4000 Mbps
- GP-SSD within 10% base line and burst performance 99% of the time
- PIOPS within 10% of provisioned performance 99% of time
- EBS optimized instances are designed for use with all EBS volume types
- Additional hourly price
