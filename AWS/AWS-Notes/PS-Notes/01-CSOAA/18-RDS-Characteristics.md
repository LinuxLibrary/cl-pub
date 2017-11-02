# AWS RDS (Relational Database Service)

- It is a database engine managed by AWS
- DB Services available throu RDS:
	- MySQL
	- Oracle
	- MSSQL
	- PostgreSQL
	- Amazon Aurora
- DB Servers can also be deployed through multiple AZs
- RDS pricing is similar to EC2 pricing
- We have the below types of hard-drives/disks available for RDS instances as per our choice
	- Magnetic
	- GP-SSD / General Purpose SSD
	- PIOPS / Provisioned IOPS

---

# Multiple AvailabilityZone Failover

- Multi-AZ RDS deployment designed for HA
- Synchronous replica in secondary AZ
- Standby replica RDS instance is invisible
- DB snapshots always taken against standby instances
- AWS automatically adjusts the DNS record when needed
- Multi-AZ is different from RDS read-replica

---

# RDS Read-Replica

- Read replicas are designed for workload sharing / offloading
- Created from the snapshot of the master instance
- Asynchronous replication / Read-only connections
- Read-only disaster recovery
