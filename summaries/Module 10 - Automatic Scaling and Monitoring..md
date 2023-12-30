### Section 1: Elastic Load Balancing.
Elastic Load Balancing is an AWS service that distributes incoming application or network traffic across multiple targets in a single AZ or across multiple AZs. Scales your load balancer as traffic to your application changes over timer. It can automatically scale to most workloads.

**Types of load balancers:**
- *Application Load Balancer,* operates at the application level (OSI 7). It router traffic to targets based on the content of the request, ideal for advanced load balancing on HTTP and HTTPS traffic.
- *Network Load Balancer,* operates at the networks transport level (OSI 4). It routes connections to targets based on IP protocol data and works well for load balancing both TCP and UDP traffic.
- *Classic Load Balancer,* provides basic load balancing across multiple EC2 instances and it operates at both the application level and network transport level. It is an older implementation.

**How Elastic Load Balancing works.**
A loas balancer accepts incoming traffic from clients an routes requests to its registered targets.
A listener is a process that checks for connection requests, configured with a protocol an port number for connections from clientes to the load balancer.
Load Balancer can also perform health checks, used to monitor the health of the registered targets so that the load balancer only sends requests to the healthy instances.
You can register targets in target groups and route traffic to the target groups.

**Elastic Load Balancer use cases.**
- Achieve high availability and better fault tolerance for you applications.
- Automatically load balance your containerized applications.
- Automatically scale your applications.
- Use Elastic Load Balancing in your VPC.
- Enable hybrid load balancing.
- Invoking Lambda functions over HTTP(S).

**Load Balancer monitoring.**
You can monitor your load balancers with:
- Amazon CloudWatch metrics.
- Access logs.
- AWS CloudTrail logs.

### Section 2: Amazon CloudWatch.
Amazon CloudWatch is a monitoring and observability service, it monitors your AWS resources in real time.
You can create an alarm to monitor any Amazon CloudWatch metric in your account and use the alarm to automatically send a notification to an Amazon SNS topic or perform an Amazon EC2 Auto Scaling or EC2 action.
You can also use Amazon CloudWatch Events to define rules that match incoming events and route them to targets for processing.

**CloudWatch alarms.**
You can create a CloudWatch alarm that watches a single CloudWatch metric or the result of a math expression based on CloudWatch metrics. You can create a CloudWatch alarm based on a static threshold, anomaly detection, or a metric math expression.
For an alarm based on a static threshold, you must specify the:
- Namespace.
- Metric.
- Statistic.
- Period.
- Conditions.
- Additional Configuration information.
- Actions.

### Section 3: Amazon EC2 Auto Scaling.
- Monitors your applications and automatically adjusts capacity to maintain steady, predictable performance at the lowest possible cost.
- Provides a simple, powerful user interface that enables you to build scaling plans for resources.
- Helps you maintain application availability.
- Enables you to automatically add or remove EC2 instances according to conditions that you define.
- Detects impaired EC2 instances and unhealthy apps and replaces the instances without your intervention.
- Provides several scaling options:
	- Manual.
	- Scheduled.
	- Dynamic or on-demand.
	- Predictive.
- An Auto Scaling group is a collection of EC2 instances that are treated as a logical grouping for the purpose of automatic scaling and management.
- Scale out (launch instances), Scale in (terminate instances).
