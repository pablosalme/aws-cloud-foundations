### Section 1: Amazon Elastic Block Store (Amazon EBS)
Amazon Elastic Block Storage (EBS) is an easy to use, high performance block storage service designed for use with Amazon Elastic Compute Cloud (EC2) for both throughput and transaction intensive workloads at any scale.

With blocks storage, files are split into evenly sized blocks of data, each with its own address but with no additional information (metadata) to provide more context for what that block of data is. Object storage, by contrast, doesn't split files up into raw blocks of data. Instead, entire clumps of data are stored in, yes, an object that contains the data, metadata and the unique identifier. With block storage you can update a single block without having to update the entire file like in object storage.

Amazon EBS enables you to create individual storage volumes and attach them to an Amazon EC2 instance:
- Offers block-level storage.
- HDD and SSD available.
- Volumes are automatically replicated within its AZ.
- It can be backed up automatically to Amazon S3 through snapshots.
- Designed for resiliency - Annual Failure Rate (AFR) is between 0.1% and 1%.
- Uses include:
	- Boot volumes and storage for EC2 instances.
	- Data storage with a file system.
	- Database hosts.
	- Enterprise applications.


**EBS Features and Charges**
- Snapshots:
	- Point-in-time images.
	- Recreate a new volume at any time.
	- Added cost of Amazon EBS snapshots to Amazon S3 is per GB-month of data stored.
- Encryption:
	- Encrypted Amazon EBS volumes.
	- No additional cost.
- Elasticity:
	- Increase capacity.
	- Change to different types.
- Volumes:
	- Amazon EBS volumes persist independently from the instance.
	- All volume types are charged by the amount that is provisioned per month.
- IOPS (Input/Output Operations Per Second):
	- General Purpose SSD: Charged by the amount that you provision in GB per month until storage is released.
	- Magnetic: Charged by the number of requests to the volume.
	- Provisioned IOPS SSD: Charged by the amount that you provision in IOPS (multiplied by the percentage of days that your provision for the month).
- Data transfer:
	- Inbound data transfer is free.
	- Outbound data transfer across Regions incurs charges.

### Section 2: Amazon Simple Storage Service (S3).
Amazon Simple Storage Service (S3) is an object storage service that offers scalability, data availability, security and performance. Amazon S3 offers a range of object-level storage classes that are designed for different use cases.
- Data is stored as objects in buckets.
- Virtually unlimited storage but a single object is limited to 5 TB.
- Designed for 11 9s of durability.
- Granular access to bucket and objects.
- Data is redundantly stored in the Region.
Data can be accessed via AWS Management Console, AWS Command Line Interface or the SDK.
Common use cases and scenarios:
- Storing application assets.
- Static web hosting.
- Backup and disaster recovery (DR).
- Staging area for big data.
- Application hosting.
- Media hosting.
- Software delivery.
**S3 Pricing.**
Pay only for what you use.
- GBs per month.
- Transfer OUT to other Regions.
- PUT, COPY, POST, LIST and GET requests.
You do not pay for:
- Transfers IN to Amazon S3.
- Transfers OUT from Amazon S3 to Amazon CloudFront or Amazon EC2 in the same Region.
**Estimating S3 Pricing.**
1. Storage class type.
	- Standard storage is designed for: 11 9s of durability and four 9s of availability.
	- S3 Standard-Infrequent Access is designed for 11 9s of durability and three 9s of availability.
2. Amount of storage.
3. Requests.
	- The number and type of requests (GET, PUT, COPY).
	- Type of requests: Different rates for GET requests than other requests.
4. Data transfer.
	- Pricing is based on the amount of data that is transferred out of the Amazon S3 Region.

![[Pasted image 20231229184940.png]]
### Section 3: Amazon Elastic File System.
Amazon Elastic File System (Amazon EFS) provides a simple, scalable, fully managed elastic NFS file system for use with AWS Cloud services and on-premises resources. It is built to scale on demand to petabytes without disrupting applications, growing and shrinking automatically as you add and remove files, eliminating the need to provision and manage capacity to accommodate growth.

**EFS features.**
- File storage in the AWS Cloud.
- Works well for big data and analytics, media processing workflows, content management, web serving and home directories.
- Petabyte-scale, low-latency file system.
- Shared storage.
- Elastic capacity.
- Supports Network File System (NFS) versions 4.0 and 4.1 (NFSv4).
- Compatible with all Linux-based AMIs for Amazon EC2.
**EFS Implementation.**
1. Create your Amazon EC2 resources and launch your EC2 instance.
2. Create your EFS file system. Create your mount targets in the appropriate subnets.
3. Connect your EC2 instances to the mount targets.
4. Verify the resources and protection of your AWS account.
Each file system has properties such as:
- ID.
- Creation Token.
- Creation time.
- File system size in bytes.
- Number of mount targets that are created for the file system.
- File system state.

### Section 4: Amazon S3 Glacier.
Amazon S3 Glacier is a data archiving service that is designed for security, durability and an extremely low cost.
- Amazon S3 Glacier is designed to provide 11 9s of durability for objects.
- It supports the encryption of data in transit and at rest through Secure Sockets Layer (SSL) or Transport Layer Security (TLS).
- The Vault Lock feature enforces compliance through a policy.
- Extremely low-cost design works well for long-term archiving. Pricing is varied on region and where the data is being sent.
- You can configure lifecycle arching of Amazon S3 content to Amazon S3 Glacier. Lifecycles policies enable you to delete or move objects based on age.
- Retrieval options:
	- Standard: 3-5 hours.
	- Bulk: 5-12 hours.
	- Expedited: 1-5 minutes.
- Secure Storage
- Server-side encryption with AES-256.
- Control access with IAM.
- Manage your keys.

[[Module 8 - Databases]]
