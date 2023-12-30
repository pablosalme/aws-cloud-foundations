### Section 1: AWS Well-Architected Framework.
Cloud architects:
- Engage with decision makers to identify the business goal and the capabilities that need improvement.
- Ensure alignment between technology deliverables of a solution and the business goals.
- Work with delivery teams that are implementing the solution to ensure that the technology features are appropriate.
The AWS Well-Architected Framework is a guide that is designed to help you build the most secure, high-performing, resilient and efficient infrastructure possible for your cloud apps and workloads.
The AWS Well-Architected Framework is organised into six pillars:
- Operational excellence.
- Security.
- Reliability.
- Performance Efficiency.
- Cost optomization.
- Sustainability.
#### Operational Excellence pillar.
- FOCUS: Run and monitor systems to deliver business value and to continually improve supporting processes and procedures.
- KEY TOPICS:
	- Automating changes.
	- Responding to events.
	- Defining standards to manage daily operations.
- DESIGN PRINCIPLES:
	- Perform operations as code.
	- Make frequent, small, reversible changes.
	- Refine operations procedures frequently.
	- Anticipate failure.
	- Learn from all operational events and failures.
- QUESTIONS:
	- Organization:
		- How do you determine what your priorities are?
		- How do you structure your organization to support your business outcomes?
		- How does your organizational culture support your business outcomes?
	- Prepare:
		- How do you design your workload so that you can understand its state?
		- How do you reduce defects, ease remediation and improve flow into production?
		- How do you mitigate deployment risks?
		- How do you know that you are ready to support a workload?
	- Operate:
		- How do you understand the health of your workload?
		- How do you understand the health of your operations?
		- How do you manage workload an operations events?
	- Evolve:
		- How do you evolve operations?

#### Security pillar.
- FOCUS: Protect information, systems and assets while delivering business value through risk assessments and mitigation strategies.
- KEY TOPICS:
	- Protecting confidentiality and integrity of data.
	- Identifying and managing who can do what.
	- Protecting systems.
	- Establishing controls to detect security events.
- DESIGN PRINCIPLES:
	- Implement a strong identity foundation.
	- Enable traceability.
	- Apply security at all layers.
	- Automate security best practices.
	- Protect data in transit and at rest.
	- Keep people away from data.
	- Prepare for security events.
- QUESTIONS:
	- Security:
		- How do you securely operate your workload?
	- Identity and access management:
		- How do you manage identities for people and machines?
		- How do you manage permissions for people and machines?
	- Detection:
		- How do you detect and investigate security events?
	- Infrastructure protection:
		- How do you protect your network resources?
		- How do you protect your compute resources?
	- Data protection:
		- How do you classify your data?
		- How do you protect your data at rest?
		- How do you protect your data in transit?
	- Incident response:
		- How do you anticipate, respond to and recover from incidents?

#### Reliability pillar.
- FOCUS: Ensure a workload performs its intended function correctly and consistently when it's expected to.
- KEY TOPICS:
	- Designing distributed systems.
	- Recovery planning.
	- Handling change.
- DESIGN PRINCIPLES:
	- Automatically recover from failure.
	- Test recovery procedures.
	- Scale horizontally to increase aggregate workload availability.
	- Stop guessing capacity.
	- Manage change in automation.
- QUESTIONS:
	- Foundations:
		- How do you manage service quotas and constraints?
		- How do you plan your network topology?
	- Workload architecture:
		- How do you design your workload service architecture?
		- How do you design interactions in a distributed system to prevent failure?
		- How do you design interactions in a distributed system to mitigate or withstand failures?
	- Change management:
		- How do you monitor workload resources?
		- How do you design your workload to adapt to changes in demand?
		- How do you implement change?
	- Failure management:
		- How do you back up data?
		- How do you use fault isolation to protect your workload?
		- How do you design your workload to withstand component failures?
		- How do you test reliability?
		- How do you plan for disaster recovery?

#### Performance Efficiency pillar.
- FOCUS: Use IT and computing resources efficiently to meet system requirements and to maintain that efficiency as demand changes and technologies evolve.
- KEY TOPICS:
	- Selecting the right resource types and sizes based on workload requirements.
	- Monitoring performance.
	- Making informed decisions to maintain efficiency as business needs evolve.
- DESIGN PRINCIPLES:
	- Democratize advanced technologies.
	- Go global in minutes.
	- User serverless architectures.
	- Experiment more often.
	- Consider mechanical sympathy.
- QUESTIONS:
	- Selection:
		- How do you select the best performing architecture?
		- How do you select your compute solution?
		- How do you select your storage solution?
		- How do you select your database solution?
		- How do you configure your networking solution?
	- Review:
		- How do you evolve your workload to take advantage of new releases?
	- Monitoring:
		- How do you monitor your resources to ensure the are performing?
	- Tradeoffs:
		- How do you use tradeoffs to improve performance?

#### Cost Optimization pillar
- FOCUS: Avoid unnecessary costs.
- KEY TOPICS:
	- Understanding and controlling where money is being spent.
	- Selecting the most appropriate and right number of resource types.
	- Analyzing spend over time.
	- Scaling to meeting business needs without overspending.
- DESIGN PRINCIPLES:
	- Implement Cloud Financial Management.
	- Adopt a consumption model.
	- Measure overall efficiency.
	- Stop spending money on undifferentiated heavy lifting.
	- Analyze and attribute expenditure.
- QUESTIONS:
	- Practice cloud financial management:
		- How do you implement cloud financial management?
	- Expenditure and usage awareness:
		- How do you govern usage?
		- How do you monitor usage and cost?
		- How do you decommission resources?
	- Cost-effective resources:
		- How do you evaluate cost when you select services?
		- How do you meet cost targets when you select resource type, size and number?
		- How do you use pricing models to reduce cost?
		- How do you plan for data transfer changes?
	- Manage demand and supply resources:
		- How do you manage demand and supply resources?
	- Optimize over time:
		- How do you evaluate new services?

### Section 2: Reliability and availability.
#### Reliability.
A measure of your system's ability to provide functionality when desired by the user.
System includes all system components: hardware, firmware and software.
Probability that your entire systems will function as intended for a specified period.
Mean time between failures (MTBF) = total time in service/number of failures.
**Metrics.**
- Mean Time to Failure (MTTF).
- Mean Time to Repair (MTTR).
- Mean Time Between Failures (MTBF) = MTTF + MTTR.

#### Availability.
Normal operation time / total time.
A percentage of uptime (for example, 99.9 percent) over time.
Number of 9s - Five 9s means 99.999 percent availability.
**High Availability.**
System can withstand come measure of degradation while still remaining available.
Downtime is minimized.
Minimal human intervention is required.
**Availability Factors.**
- Fault tolerance: The built-in redundancy of an application's components and its ability to remain operational.
- Scalability: The ability of an application to accommodate increases in capacity needs without changing design.
- Recoverability: The process, policies and procedures that are related to restoring service after a catastrophic event.

### Section 3: AWS Trusted Advisor.
AWS Trusted Advisor is an online tool that provides real-time guidance to help you provision your resources following AWS best practices. It looks at your entire AWS environment and gives you real-time recommendations in the five mains pillars. You can use AWS Trusted Advisor to help you optimize your AWS environment as soon as you start implementing your architecture designs.


[[Module 10 - Automatic Scaling and Monitoring.]]
