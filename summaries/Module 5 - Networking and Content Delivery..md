### Section 1 - Networking basics.
A computer network is two or more client machines that are connected together to share resources. Can be logically partitioned into subnets.
An PIv4 address is a numerical label in decimal format that identifies the machine in the network. It has 32-bits, 8 bits in octal format.
An IPv6 address is composed of 8 groups of 4 letters and numbers that are separated by colons (:). Colons separate 8 groups that represent 16 bits in hexadecimal.

**Classless Inter-Domain Routing (CIDR)**
A common method to describe networks. The CIDR address is expressed as follows:
- An IP address.
- Slash (/).
- Number that tells you how many bits of the routing prefix must be fixed or allocated for the network identifier.
The bits that are not fixed are allowed to change. CIDR is a way to express a group of IP addresses that are consecutive to each other.

**Open Systems Interconnection (OSI) model.**
Is a conceptual model that is used to explain how data travels over a network.
![](https://lh7-us.googleusercontent.com/PL2oH9vrIlVqvgMtUsLkj2Icd-c6ayx5aVFVVC_jsJmcoVw6ms5JnwfvKmxnwKIdfhUOKZNptK_LJo52ZoUKKfumB55NWDHJ7yy1DHGd1TrkgUN66GeX9TIpL6RKdVMVkl0MGK2dPz4CQJHWa7wuVMQ)

### Section 2 - Amazon VPC.
Amazon Virtual Private Cloud is a service that lets you provision a logically isolated section of the AWS Cloud, where you can launch your AWS resources.
It includes the selection of your own IP address range, the creation of subnets and the configuration of route tables and network gateways.
You can expose your VPC like you want, you can make subnets and make it private or public.
You can use multiple layers of security, including security groups and network access control lists.

**VPCs and subnets.**
VPC is a virtual network that is logically isolated from other virtual networks in the AWS Cloud. VPCs belong to a single Region and can span multiple AZs.
After you create a VPC, you can divide it into one or more subnets, you can create subnets in different AZs for high availability.

**IP addressing.**
IP addresses enable resources in your VPC to communicate with each other and with resources over the internet, when you create a VPC, you assign an IPv4 CIDR block to it.
After you create a VPC, you cannot change the address range. The IPv4 CIDR block might be as large as /16 or as small as /28. It can also be done with IPv6.

**Reserved IP addresses.**
For each CIDR block that you specify, AWS reserves 5 IP addresses:
- Network address.
- VPC local router (link-local).
- Domain Name System (DNS) resolution.
- Future use.
- Network broadcast address.

**Public IP address types.**
Every VPC gets a private IP address automatically. You can also request a public IP to be assigned when you create the instance by modifying the subnet's auto-assign.
An Elastic IP address is a static an public IPv4 that is designed for dynamic cloud computing. You can associate an Elastic IP address with any instance or network interface for any VPC in your account. You can move all of the attributes of the network interface from one instance to another in a single step. (Additional costs with Elastic IP).

**Elastic network interfaces.**
An elastic network interface is a virtual network interface that you can attach or detach from an instance in a VPC. When you move a network interface from one instance to another, network traffics is redirected to the new instance.
Each instance in your VPC has a default network interface that is assigned a private IPv4 from the IPv4 address range of your VPC.

**Route tables and routes.**
A route table contains a set of rules (routes) that directs network traffics from your subnet. Each route specifies a destination and a target. You can customize route tables by adding routes. You cannot delete the local route entry that is used for internal communications. Each subnet in your VPC must be associated with a route table. The main route table is the route table that is automatically assigned to your VPC.

### Section 3 - VPC networking.
**Internet gateway.**
An internet gateway is scalable, redundant and highly available VPC component that allows communication between instances in your VPC and the internet. It has two purposes, to provide a target in your VPC route tables and to perform network address translation for instances that were assigned public IPv4 addresses.
To make a subnet public, you attach an internet gateway to your VPC and add a route to the route table to send non-local traffic through the internet gateway to the internet.

**Network address translation (NAT) gateway.**
NAT gateways enable instances in a private subnet to connect to the internet or other AWS services, but prevents the internet from initiating a connection with those instances.
You must specify the public subnet in which the NAT gateway should reside, also specify an Elastic IP to associate with the NAT gateway when you create it.
After creating a NAT gateway, you must update the route table that is associated with one or more of your private subnets to point internet-bound traffic to the NAT gateway.

**VPC sharing.**
Enables customer to share subnets with other AWS accounts in the same organization in AWS Organizations. Enables multiple accounts to create their app resources into shared, centrally managed VPCs. Participants cannot view, modify or delete resources that belong to other participant or the VPC owner.
Benefits of VPC sharing:
- Separation of duties.
- Ownership.
- Security Groups.
- Efficiencies.
- No hard limits.
- Optimized costs.

**VPC peering.**
A VPC peering connection is a networking connection between two VPCs that enables you to route traffic between them privately. Instances in either VPC can communicate with each other as if there are within the same network.
When you set up the peering connection, you create rules in your route table to allow the VPCs to communicate with each other through the peering resources.
Restrictions:
- IP address ranges cannot overlap.
- Transitive peering is not supported.
- You can only have one peering resource between the same two VPCs.

**AWS Site-To-Site VPN.**
To connect your VPC to your remote network, you:
1. Create a new virtual gateway device and attach it to your VPC.
2. Define the configuration of the VPN device or the customer gateway.
3. Create a custom route table to point corporate data center-bound traffic to the VPN gateway.
4. Establish an AWS Site-to-Site VPN connection to link the two systems together.
5. Configure routing to pass traffic through the connection.

**AWS Direct Connect.**
Enables you to establish a dedicated, private network connection between your network and one of the DX locations. This connection can reduce your network costs, increase bandwidth throughput and provide a more consistent network experience than internet-based connections. DX uses VLANs 802.1. ^bc5136

**VPC endpoints.**
Is a virtual device that enables you to privately connect your VPC to supported AWS services and VPC endpoint services that are powered by AWS PrivateLInk.
Traffic between you VPC and the other service does not leave the Amazon network.
There are two types of VPC endpoint:
- An interface VPC endpoint enables you to connect to services that are powered by AWS PrivateLink. The owner of the service is the service provider and you are the service customer. You are charged for creating and using an interface endpoint to a service.
- Gateway endpoints (S3 and DynamoDB). Provide reliable connectivity to S3 and DynamoDB without requiring an internet gateway or a NAT device for your VPC.

**AWS Transit Gateway.**
Is useful to simplify your networking model. You only need to create and manage a single connection from the central gateway into each VPC, on-premises data center or remote office across your network.
![](https://lh7-us.googleusercontent.com/LGWYad5hgmAJAov5QzfZS4GwUItWRX9DB7Bvrx9PLfN-JOZsVdMj3737o8HOPsaa6DGN0qWY5IeZkkPEfcv_8GX3BFN9uqGQLwPJnXwcZvxvuHJGjNmjWkWYjo4z00IzEP9_fkuXbmyH_iUEbz2RhOA) ^08eb8d

### Section 4 - VPC security.
**Security Groups.**
A security group acts as a virtual firewall for your instance and it controls inbound and outbound traffic. Act at the instance level not the subnet level. Each instance in a subnet in your VPC can be assigned to a different set of security groups.
Security groups have rules that control the inbound and outbound traffics. No inbound traffic that originates from another hosts to your instance is allowed until you add inbound rules to the security group.
Security groups are stateful, which means that state information is kept even after a request is processed.
![](https://lh7-us.googleusercontent.com/yreShqQQvB8En48-U86HkLY3lyOnJcTxHIKpTr4pDGsg4IvA6O4tnAP5meO2-Ow1rrKazl9KBLhKPZ5mxHZHJzoSKgElwf2Yi6giqmdaMPdPisA96Dt--XPqitmq4lD09ZzDM5tovImfLoJM3BBDHyw)

**Network Access Control List (ACL).**
Is an optional layer of security for your VPC, it acts as a firewall for controlling traffics in and out of one or more subnets.
Each subnet in your VPC must be associated with a network ACL. You can associate a network ACL with multiple subnets. A subnet can be associated with only one network ACL at a time.
A ACL has separated inbound and outbound rules and each rule can either allow or deny traffic. Network ACLs are stateless, which means that no information about a request is maintained after a request is processed.
You can create a custom network ACL and associate it with a subnet.
![](https://lh7-us.googleusercontent.com/ejZStUyRtMy1HEFRtJJ0bAyDXoFs3R0-krw0B8uKK12v00UMGO1eLO1M10OyPg9aFGBntKYnu5GpF5pbwFfZjvWEY1fmR1oU-0aWC3VOko8KY8jMHhZ_85VDMlACUCcCRP-3zsm0T4Be-dLYXyH24m4)

**Security groups vs network ACLs.**
![](https://lh7-us.googleusercontent.com/XJa0vxLORNygHgH-evc0MaMlQZYntL3jS09HjH4_jarC8NTXAwH0aorQ7JFY3Sq4XTqdQQKimtnhN8DT0rkFelizkNGtK4-_sVin65rUZXc26OirS6r0YzbBQkZQ2iF_Wa9KYnGAz_G7lqZikY7T9-Y)

### Section 5 - Amazon Route 53.
Is a highly available and scalable cloud DNS web service. It is designed to give developers and businesses a reliable and cost-effective way to route users to internet apps by translating names into the numeric IP.
Route 53 traffic flow helps you manage traffic globally through several routing types, which can be combined with DNS failover to enable various low-latency, fault-tolerant architectures.
It also offers DN Registration.

**Route 53 supported routing.**
- Simple routing (round robin), use for a single resource that performs a given function for your domain.
- Weighted round robin routing, used to route traffic to multiple resources in proportions that you specify. Enables you to assign wights to resource record sets to specify the frequency with which different responses are served.
- Latency routing (LBR), used when you have resources in multiple Regions and you want to route traffic to the Region that provides the best latency.
- Geolocation routing. Use when you want to route traffics based on the location of your users. When you use geolocation routing, you can localize your content and present some or all of your website in the language of your users.
- Geoproximity routing, used when you want to route traffic based on the location of your resources.
- Failover router (DNS failover), used when you want to configure active-passive failover. Route 53 can help detect an outage of your website and redirect your users to alternate locations where your app is operating properly.
- Multivalued answer routing, used when you want Route 53 to respond to DNS queries with up to eight healthy records that are selected at random.

**Amazon Route 53 DNS failover.**
Enables you to improve the availability of your app that run on AWS by:
- Configuring backup and failover scenarios for your own applications.
- Enabling highly available multi-region architectures on AWS.
- Creating health checks to monitor the health and performance of your web apps.

**DNS failover for a multi-tiered web app.**
You can do the following tasks with Route 53 to ensure high availability:
1. Create two DNS records for the Canonical Name Record (CNAME) with a routing policy of Failover Router.
2. Use Route 53 health checks to make sure that the primary is running.

### Section 6 - Amazon CloudFront.
The number of network hops and the distance that the request must travel significantly affect the performance and responsiveness of the website. Further, network latency is different in various geographic locations. For these reasons, a content delivery network might be the solution.

**Content delivery network (CDN)**
Is a globally distributed system of caching servers, a CDN caches copies of commonly requested files that are hosted on the app origin server.
CDNs also deliver dynamic content that is unique to the requester and is not cacheable. The CDN establishes and maintains secure connections closer to the requester. If the CDN is on the same network as the origin, routing back to the origin to retrieve dynamic content is accelerated.

**Amazon CloudFront.**
Is a fast CDN service that securely delivers data, videos, apps and app programming interface (APIs) to customers globally with low latency and high transfer speeds. Amazon CloudFront delivers files to users over a global network of edge locations and Regional edge caches.

**Amazon CloudFront infrastructure.**
CloudFront delivers content through a worldwide network of data centers that are called edge locations. When a user requests content that you server with CloudFront, the user is routed to the edge location that provides the lowest latency, so that content is delivered with the best possible performance.

**Amazon CloudFront benefits.**
Key features of CloudFront include:
- **Global Reach:** CloudFront's extensive network spans the globe, enabling it to deliver content with minimal latency. This network comprises edge locations and regional caches.
- **Security:** provides robust security measures at both the network and app levels. It includes built-in protections like AWS Shield at no extra cost. You can use AWS ACM to manage SSL certificates.
- **Customization:** is highly programmable and can be tailored to meet specific application requirements. It integrates with Lambda & Edge, allowing you to run custom code across AWS locations worldwide, enhancing responsiveness. It also supports integrations with other tools and offers CI/CD capabilities for DevOps environments.
- **Integration with AWS:** connecting to the AWS Global Infrastructure and other AWS services. You can programmatically configure its features using APIs or the AWS Management Console.
- **Cost-Effective:** it operates on a pay-as-you-go model with no minimum commitments. Unlike self-hosting, it eliminates the need to manage a network of cache servers across multiple sites, reducing complexity and costs. It also optimizes resource usage by collapsing simultaneous viewer requests, reducing the load on origin servers. When using AWS origins like S3 or ELB, you only pay for storage costs, not data transfer between these services and CloudFront.

**CloudFront pricing.**
- Data transfer Out: you're billed for the data transferred from CloudFront edge locations to the internet or your origin server. Pricing varies by geographic region.
- HTTP(S) Requests: You pay for the number of HTTP(S) requests made to CloudFront for your content.
- Invalidation Requests: Charges apply per path in your invalidation requests. The first 1000 paths each month are free and beyond that, you're charged per path.
- Dedicated IP Custom SSL: if you use custom SSL certificates with Dedicated IP support, it costs $600 per month per certificate, with prorated charges based on hours of use.







[[Module 6 - Compute]]
