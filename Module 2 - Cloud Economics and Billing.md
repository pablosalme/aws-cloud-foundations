### Section 1 - Fundamentals of Pricing.
There are three fundamental drivers of cost with AWS: **compute, storage and outbound data transfer.**
- Pay for what you use.
- Pay less when you reserve.
	- All Upfront Reserved Instance (AURI).
	- Partial Upfront Reserved Instance (PURI).
	- No Upfront Reserved Instance (NURI).
- Pay less when you use more.
- Pay even less as AWS grows.
**Service with no charge.**
- **Amazon Virtual Private Cloud (Amazon VPC)**, enables you to provision logically isolated section of the AWS Cloud where you can launch AWS resources in a virtual network that you define.
- **AWS Identify and Access Management (IAM),** controls your users access to AWS services and resources.
- **Consolidated Billing,** is a billing feature in AWS Organizations to consolidates payment for multiple Amazon Internet Services Private Limited (AISPL) accounts. Consolidated billing provides:
	- One bill for multiple accounts.
	- The ability to easily track each accounts charges.
	- The opportunity to decrease charges as a result of volume pricing discounts from combines usage.
	- And you can consolidate all of your accounts using consolidated billing and get tiered benefits
- **AWS Elastic Beanstalk,** is and even easier way for you to quickly deploy and manage apps in the AWS Cloud.
- **AWS CloudFormation,** gives developers and systems administrators and easy way to create a collection of related AWS resources and provision them in an orderly and predictable fashion.
- **Automatic Scaling,** automatically adds or removes resources according to conditions you define. The resources you are using increase seamlessly during demand spikes to maintain performance and decrease automatically during demand lulls to minimize costs.
- **AWS OpsWorks,** is an application management service that makes it easy to deploy and operate applications of all shapes and sizes.
### Section 2 - Total Cost of Ownership (TCO).
TCO is the financial estimate to help identify direct and indirect costs of a system. Include:
- **Server** costs for both hardware and software and facilities costs to house the equipment.
- **Storage** costs for the hardware, administration and facilities.
- **Network** costs for hardware, administration and facilities.
- And **IT labor** costs that are required to administer the entire solution.
**Pricing calculator:**
- Estimate monthly costs.
- Identify opportunities to reduce monthly costs.
- Model the solutions before building them.
- Explore price point and calculations behind your estimate.
- Find the available instance types and contract terms that meet your needs.
**Hard benefits:**
- Reduced spending on compute, storage, networking and security.
- Reductions in hardware and software purchases ([capex](https://es.wikipedia.org/wiki/Capex)).
- Reductions in operational costs, backup and disaster recovery.
- Reduction in operations personnel.
**Soft benefits.**
- Reuse of service and apps that enable you to define by using the same cloud service.
- Increases developer productivity.
- Improved customer satisfaction.
- Agile business processes that can quickly respond to new and emerging opportunities.
- Increase in global reach.
### Section 3 - AWS Organizations.
The main benefits of AWS Organizations are:
- **Service control policies (SCPs),** centrally managed access policies across multiple AWS account.
- Controlled access to AWS services.
- Automated AWS account creation and management.
- Consolidated billing across multiple AWS accounts simplify the billing process by setting up a single payment method for all the AWS accounts.
An OU (Organization Unit) is a container for accounts within a root.
An OU can also contain others OUs.
When you attach a policy to one of the nodes in the hierarchy, it flows down and it affects all the branches and leaves.
AWS Organizations does not replace associating IAM policies with users, groups and roles within an AWS account.
With Organizations, you use SCPs to allow or deny access to particular AWS services for individual AWS accounts or for groups of accounts in an OU.
The specified actions from and attached SCP affect all IAM users, groups and roles for an account, including the AWS account root user.
AWS Organizations can be managed through **AWS Management Console, AWS Command Line Interface (CLI) and AWS Software Development Kits (SDKs)** to handle tasks such as cryptographically signing request, managing errors and retrying requests automatically.
**AWS Organizations HTTPS Query API** gives you programmatic access to AWS Organizations and AWS.
![[Pasted image 20231201174813.png]]
### Section 4 - AWS Billing and Cost Management.
**AWS Billing Dashboard** contains:
- The **Spend Summary** shows you how much you spent last month, the estimated costs of your AWS usage for the month to date and a forecast for how much you are likely to spend this month.
- The **AWS Bills Page,** lists the costs that you incurred over the past month for each AWS service, with a further breakdown by AWS Region and linked account. This tool gives you access to the most up-to-date information on your costs and usage, including your monthly bill and the detailed breakdown of the AWS services that you use.
- The **Cost Explorer** enables you to:
	- View charts of your costs.
	- View cost data for the past 13 months.
	- Forecast how much your are likely to spend over the next 3 months.
	- Discover patterns in how much you spend on AWS resources over time and identify cost problem areas.
	- Identify the services that you use the most.
	- View metrics, like which Az have the most traffic or which linked AWS account is used the most.
- **AWS Budgets,** uses the cost visualisation that is provided by Cost Explorer to show you the status of your budgets and to provide forecasts of your estimated costs. You can also create notifications for when you go over your budget for the mont, or when your estimated costs exceed your budget.
- The **AWS Cost and Usage Report** is a single location for accessing comprehensive information about your AWS costs and usage. This tools lists the usage for each service category that is used by an account in hourly or daily line items and any tax that you activated for tax allocation purposes.
### Section 5 - Technical support.
|                                 | Critical           | Urgent         | High            | Normal           | Low              |
| ------------------------------- | ------------------ | -------------- | --------------- | ---------------- | ---------------- |
| Basic                           |                    |                | No Case Support |                  |                  |
| Developer Plan (Business hours) |                    |                |                 | 12 hours or less | 24 hours or less |
| Business Plan (24/7)            |                    | 1 hour or less | 4 hours or less | 12 hours or less | 24 hours or less |
| Enterprise Plan (24/7)          | 15 minutes or less | 1 hour or less | 4 hours or less | 12 hours or less | 24 hours or less                 |




[[Module 3 - AWS Global Infrastructure Overview.]]
