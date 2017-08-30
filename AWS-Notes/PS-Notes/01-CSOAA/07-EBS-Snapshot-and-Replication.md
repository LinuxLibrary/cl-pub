#  EBS Snapshots and Replication

- EBS Snapshot Characteristics
	- Point-in-time snapshot, which freezes the instance at the point it is and will take a snapshot
	- Supports incremental snapshots
	- Billed only for the changed blocks
	- Deleting the snapshot removes only the data not needed by any other snapshot
	- EBS leverages S3 for snapshot storage. Means the EBS snapshots will be stored in S3

- EBS Snapshots features
	- Resizing EBS volumes
	- Sharing EBS snapshots
	- Copying EBS snapshots across regions
	- Lazy loading means the recalling process of an EBS volume from S3 will be slow
	
- Pre-Warming of EBS Volumes
	- Pre-Warming on Windows
		- Format the drive (New Volume)
		- Use dd for Windows (drive with data)
	- Pre-Warming on Linux
		- Use dd to write or read
