### Section 1 - AWS Global Infrastructure.
AWS Global Infrastructure, designed and built to deliver a flexible, reliable, scalable and secure cloud computing environment with high-quality global network performance.
- **Data replication** across regions is controlled by you.
- **Communication** between regions uses AWS backbone networks infrastructure.
- Each region provides full redundancy and connectivity.
A region consist of two or more **Availability Zones**.
**Selecting a Region.**
Factor to determinate the right region:
- Data governance and legal requirements. Local laws change pending the regions, you have to consider which law allows you to offer content or services.
- Proximity to customers. This will help you reduce latency, it is desirable to run your app and store your data in a region close to your customer.
- Services available within the region.
- Costs (vary by region).
**Availability Zones.**
Each AWS region has multiple isolated locations that are known as AZs.
AZs provides the ability to operate apps and databases that are more highly available, fault-tolerant and scalable. Each zone can include multiple data centers and hundreds of thousands of servers. Fully isolated from AWS Global Infrastructure.
AZs are interconnected with high-bandwidth with dedicated fiber.
You should design your systems to survive the temporary or prolonged failure of and AZ if a disaster occurs.
**AWS data centers.**
Each location is carefully evaluated with several factors in mind:
- Redundant design that anticipates and tolerates failure while maintaining services levels.
- Critical system components are backed up across multiple AZs.
- AWS monitors service usage to deploy infrastructure to support availability commitments and requirements.
- Data center location are not disclosed and all access to them is restricted.
- In case of failure, automated processes move data traffic away from the affected area.
**Points of Presence.**
Consists of edge locations and a much smaller number of regional edge locations.
- Amazon CloudFront is a content delivery network (CDN) used to distribute content to end users to reduce latency.
- Amazon Route 53 is a DNS service.
- AWS Point of Presence deliver a better near real-time user experience, continuously measuring internet connectivity, performance and computing to find the best way to route requests.
- Regional edge caches are used when you have content that is not accessed frequently enough to remain in an edge location.


[[Module 4 - AWS Cloud Security]]
