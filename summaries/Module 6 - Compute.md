### Section 1: Compute Services Overview
AWS offers many compute services:
- EC2
- EC2 Auto Scaling ^eb5f8b
- Elastic Container Registry (ECR) ^544ec8
- Elastic Container Service (ECS) ^8345e7
- VMWare Cloud on AWS
- Elastic Beanstalk
- Lambda
- Elastic Kubernetes Service (EKS) ^8f47c7
- Lightsail
- Batch
- Fargate
- Outposts
- Serverless Application Repository
The optimal compute services that you use will depend on your use case, some aspects to consider:
- What is your application design?
- What are your usage patterns?
- Which configuration settings will you want to manage?
You can take a look at [[AWS Services]] for more details.
### Section 2: Amazon Elastic Compute Cloud (EC2)
**Overview.**
- Provides virtual machines, referred to as EC2 instances, in the cloud.
- Gives you full control over the guest operating system on each instance.
- You can launch instances of any size into an AZ anywhere in the world with just a few clicks or a line of code and the are ready in minutes.
- Resizable compute capacity.
- You can launch instances form Amazon Machine Images (AMIs).
- You can control traffic to and from instances.
- Provides tools to build failure resilient applications and isolate them from common failure scenarios.

**Launching an EC2 instance.**
These are the nine key decisions to make when you create an EC2 instance by using the AWS Management Console Launch Instance Wizard.

1. **Select Amazon Machine Image (AMI).**
	- Is a template that is used to create an EC2 instance.
	- Contains a Windows or Linux OS and often has some software pre-installed.
	- AMI choices:
		- Quick Start. Linux and Windows AMIs that are provided by AWS.
		- My AMIs. Any AMI that you created.
		- AWS Marketplace. Pre-configured templates from third parties.
		- Community AMIs. AMIs shared by others.
2. **Select an instance type.**
	- Optimized to fit different use cases.
	- The instance type that you choose determines:
		- Memory (RAM).
		- Processing power (CPU).
		- Disk space and disk type (Storage).
		- Network performance.
	- Instance type categories:
		- General purpose.
		- Compute optimized.
		- Memory optimized.
		- Storage optimized.
		- Accelerated computing.
	- Instance types offer family generation and size.
	- Networking features:
		- The network bandwidth (Gbps) varies by instance type.
		- To maximize networking and bandwidth performance of your instance type enable enhanced networking and if you have interdependent instances, launch them into a cluster placement group.
		- Enhanced networking types are supported on most instance types. Enhanced networking types:
			- Elastic Network Adapter (ENA): Supports network speeds of up to 100 Gbps.
			- Intel 82599 Virtual Function interface: Support network speeds of up to 10 Gbps.
3. **Specify Network Settings.**
	- Where should the instance be deployed? Identify the VPC and optionally the subnet.
	- Should a public IP address be automatically assigned?
	- You can have multiple networks, such as different ones for development, testing and production.
4. **Attach IAM Role (optional).**
	- Will software on the EC2 instance need to interact with other AWS Services? If yes, attach an appropriate IAM Role. IAM Roles can be attached at any time.
	- An AWS Identity and Access Management (IAM) role that is attached to an EC2 instance is kept in an instance profile.
5. **User Data Script (optional).**
	- Specify a user data script at instance launch. Use user data scripts to customize the runtime environment of your instance.
	- Script executes the first time the instance starts.
6. **Specify Storage.**
	- Configure the root volume.
	- Attach additional storage volumes (optional). For each volume, specify:
		- Disk Size (in GB).
		- Volume type (SSFs or HDDs).
		- If the volume will be deleted when the instance is terminated.
		- If encryption should be used.
	- Storage Options:
		- Amazon Elastic Block Store (Amazon EBS):
			- Durable, block-storage volumes.
			- You can stop the instance and start it again and the data will still be there.
		- Amazon EC2 Instance Store:
			- Storage is provided on disks that are attached to the host computes where the EC2 instance is running.
			- If the instance stops, data stored here is deleted.
		- Other options for storage (not for the root volume):
			- Mount an Amazon Elastic File System (EFS) file system.
			- Connect to Amazon Simple Storage Service (S3).
7. **Add tags.**
	- Consists of a key and an optional value.
	- Tagging is how you can attach metadata to an EC2 instance.
	- Potential benefits:
		- Filtering.
		- Automation.
		- Cost allocation.
		- Access control.
8. **Security Group Settings.**
	- A security group is a set of firewall rules that control traffic to the instance.
	- When you launch an instance, you associate one or more security groups with it.
	- Create rules that specify the source, which ports that network communications can use and the protocol (TCP, UDP, ICMP).
	- Modify the rules for a security group at any time, the new rules are automatically applied to all instances that are associated with the security group.
9. **Identify or create the Key pair.**
	- At instance launch, you specify an existing key pair or create a new key pair.
	- A key pair consists of a public key that AWS stores and a private key file that you store.
	- It enables secure connections to the instance.
	- For Windows AMIs, Use the private key to obtain the administrator password that you need to log in to your instance.
	- For Linux AMIs, Use the private key to use SSH to securely connect to your instance.

**Miscellaneous.**
Consider using an Elastic IP Address if you require a persistent public IP address.
Instance metadata can be viewed in browser or a terminal window and can be used to configure or manage a running instances.
Amazon CloudWatch can be used to monitor an EC2 instance to provide near-real-time metrics, charts and 15 months of historical data. CloudWatch has basic monitoring (no additional cost) or detailed monitoring.

### Section 3: Amazon EC2 Cost Optimization.
**Amazon Pricing Models.**
- On-Demand instances.
	- Pay by the hour.
	- No long-term commitments.
	- Eligible for the AWS Free Tier.
- Dedicated Hosts.
	- A physical server with EC2 instance capacity fully dedicated to your use.
- Dedicated Instances.
	- Instances that run in a VPC on hardware that is dedicated to a single customer.
- Spot instances.
	- Instances run as long as they are available and your bid is above the Sport instance prices.
	- The can be interrupted by AWS with a 2 minutes notification.
	- Interruption options include terminated, stopped or hibernated.
	- Prices can be significantly less expensive compared to On-Demand instances.
	- Good choice when you have flexibility in when your applications can run.
- Reserved instances.
	- Full, partial or no upfront payment for instance you reserve.
	- Discount on hourly charge for that instance.
	- 1 year o 3 year term.
- Scheduled Reserved instances.
	- Purchase a capacity reservation that is always available on a recurring schedule you specify.
	- 1 year term.
Per second billing available for On-Demand Instances, reserved instances and spot instances that run amazon linux or ubuntu.

**Four pillars of cost optimization.**
- Right size.
	- Provision instances to match the need, CPU, memory, storage and network throughput.
	- Use CloudWatch metrics to downsize as needed.
	- Best practice: Right size, then reserve.
- Increase Elasticity.
	- Stop or hibernate EBS-backed instances that are not actively in use.
	- Use automatic scaling to match needs based on usage.
- Optimal Pricing Model.
	- Leverage the right pricing model for your use case.
	- Optimize and combine purchase types.
		- Use On-Demand instance and sport instances for variable workloads, use reserved instances for predictable workloads.
	- Consider serverless solutions (AWS Lambda).
- Optimize Storage Choices.
	- Reduce costs while maintaining storage performance and availability.
	- Resize EBS volumes and change EBS volume types.
	- Delete EBS snapshots that are no longer needed.
	- Identify the most appropriate destination for specific types of data.

### Section 4: Container Services.
**Container basics.**
Container are a method of operating system virtualization.
- Repeatable.
- Self-contained execution environments.
- Software runs the same in different environments.
- Faster to launch and stop or terminate than virtual machines.
Docker is a software platform that enables you to build, test and deploy applications quickly.
Containers are created from a template calle an image.

**Amazon Elastic Container Service (ECS).**
- A highly scalable, fast, container management service.
- Key benefits:
	- Orchestrates the execution of Docker containers.
	- Maintains and scales the fleet of node that run your containers.
	- Removes the complexity of standing up the infrastructure.
- Integrated with features that are familiar to Amazon EC2 service users.
	- Elastic Load Balancing.
	- EC2 security groups.
	- EBS volumes.
	- IAM roles.
Do you want to manage the Amazon ECS cluster that runs the containers?
- If yes, create an ECS cluster backed by EC2 (provides more granular control over infrastructure).
- If no, create an ECS cluster backed by Fargate (easier to maintain, focus on your applications).
Amazon ECR is a fully managed Docker container registry that makes it easy for developers to store, manage and deploy Docker container images.

**Amazon Elastic Kubernetes Service (EKS).**
- Kubernetes is open source software for container orchestration.
	- Deploy and manage containerized applications at scale.
	- The same toolset can be used on premises and in the cloud.
- Complements Docker.
	- Docker enables you to run multiple containers on a single OS host.
	- Kubernetes orchestrates multiple Docker hosts (nodes).
- Automates container provisioning, networking, load distribution and scaling.
Amazon EKS.
- Enables you to run Kubernetes on AWS.
- Certified Kubernetes conformant (support easy migrations).
- Support Linux and Windows containers.
- Compatible with Kubernetes community tools and support popular Kubernetes add-ons.
- Use Amazon EKS to manage clusters of Amazon EC2 compute instances and run containers that are orchestrated by Kubernetes on those instances.

### Section 5: Introduction to AWS Lambda.
- Serverless computing enables you to build and run applications and services without provisioning or managing servers.
- Supports multiple programming languages.
- Provides built-in fault tolerance and automatic scaling.
- An event source is and AWS service or developer-created application that triggers a Lambda function to run.
- Pay-per-use pricing.
- The maximum memory allocation for a single Lambda function is 3,008 MB.
- The maximum execution time for a Lambda function is 15 minutes.
- Deployment package size = 250 MB unzipped, including layers.

### Section 6: Introduction to Elastic Beanstalk.
- An easy way to get web applications up and running.
- A managed service that automatically handles:
	- Infrastructure provisioning and configuration.
	- Deployment.
	- Load balancing.
	- Automatic scaling.
	- Health monitoring.
	- Analysis and debugging.
	- Logging.
- No additional charge for Elastic Beanstalk, pay only for the underlying resources that are used.
- It supports web applications written for common platforms.
- You upload your code and Elastic Beanstalk automatically handles the deployment.


[[Module 7 - Storage]]
