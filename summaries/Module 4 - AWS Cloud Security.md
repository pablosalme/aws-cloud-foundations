### Section 1 - AWS shared responsibility model.
**AWS is responsible** for protecting the infrastructure that runs all the services that are offered in the AWS Cloud.
**The costumer is responsible** for the encryption of data at rest and data in transit, additionally, is responsible for the configuration of security groups and the configuration of the operating system that run on compute instances that they launch.

![](https://lh7-us.googleusercontent.com/fSkpJa_x-8XxmBv3zFH56KORJ5uP3vfD4n3MjgGOOlYAFAymt0-wDUWovBPY6-DJw7EGmoMFpfC9U4jsR-vimlXRcX8JpIOya6eVOPItwUQO9tm4m1p8fFVd0z8hxlmPCje83-Z0mb7XaSi88UZHF3I)

**AWS** is responsible for protecting the global infrastructure that runs all the services that are offered in the AWS Cloud. AWS is responsible for:
- **Physical security of data centers**
- **Hardware infrastructure.**
- **Software infrastructure.**
- **Network infrastructure.**
The customer is responsible for what is implemented by using AWS services and for the applications that are connected to AWS. Including:
- Amazon EC2, selecting and securing any instance.
- Securing applications, that are launched on AWS resources.
- Security group configurations.
- Firewall configurations.
- Network configurations.
- Secure account management.
### Section 2 - AWS Identity and Access Management (IAM)
IAM allows you to control access to compute, storage, database and app services in the AWS Cloud. IAM can be used to specify and enforce authorization policies so that you can specify which users can access which services.
You can manage which resources can be accessed by who and how these resources can be accessed. You can grant different permissions to different peoples for different resources.

**IAM: Essential components.**

- **IAM user**, is a person or app that is defined in an AWS account and that must make API calls to AWS products. Unique name and a set of security credentials.
- **IAM group**, collection of IAM users, you can use IAM groups to simplify specifying and managing permissions for multiple users.
	- A group can contain many users and a user can belong to multiple groups.
	- Groups cannot be nested. A group can contain only users.
	- There is no default group that automatically includes all users in the AWS account.
- **IAM policy**, document that defines permissions to determine what users can do in the AWS account. Grants access to specific resources and specifies what the user can do, can also be denied access.
- **IAM role**, tool for granting temporary access to specific AWS resources in an AWS account.
	- Instead of being uniquely associated with one person, a role is intended to be assumable by anyone who needs it.
	- Use roles to delegate access to users, apps or services that do not normally have access to your AWS resources.

**Authenticate as an IAM user to gain access**.
A user or system must first prove their identity. When you create an IAM user, you select what type of access the user is permitted to use to access AWS resources. There are two:
- **Grant programmatic access,** IAM user will be required to present an access key ID an a secret access key when they make an AWS API call.
- **Grant AWS Management Console access,** IAM user will be required to fill in the fields that appear in the browser login window. If multi-factor authentication (MFA) is enabled for the user, they will also be prompted for a n authentication code. MFA token before every access to AWS services and resources.

**Authorization: What actions are permitted.**
Authorization is the process of determining what permissions a user, service or application should be granted. By default IAM users do not have permissions to access any resources or data in an AWS account. You must grant permission by creating a policy, which is a document in JSON format.
To assign permission to a user, group or role, you must create an IAM policy. Any actions that you do not explicitly allow are denied.
Principle of least privilege is an important concept in computer security, it promotes that you grant only the minimal user privileges needed to the user, based on the needs of your users. Start with a minimum set of permissions and grant additional permissions as necessary.

**IAM policies.**
**IAM policy** is a formal statement of permissions that will be granted to an entity.
The order in which the policies are evaluated has no effect on the outcome of the evaluation.
When there is a conflict, the most restrictive policy applies.
- **Identity-based policies** are permissions policies that you can attach to a principal such as an IAM user, role or group.
	- **Managed policies,** standalone identity-based policies that you can attach to multiple entities.
	- **Inline policies,** policies that you create and manage and that are embedded directly into a single entity.
- **Resource-based policies** are JSON policy documents that you attach to a resource, such as an S3 bucket.
	- These policies specify who can access the resource and what actions they can perform on it.
	- Are defined inline only, which means that you define the policy on the resource itself, instead of creating a separate IAM policy document that you attach.

![](https://lh7-us.googleusercontent.com/_FIMKQiSL3O22QErvF4wZdaWCEvRSyd3U-KurIpXN4cPGoEzpYeMCRUc8z5IX4wR5h7rFJJkC-1HzpgBEQjzhjQa_Rztql9gPqYv491179APG3kfR_73WgFtI5ALru8ugnt6JaZ_eHaE1ajGUxa29QM)
Includes an explicit deny (“Effect”:”Deny”) element. NotResource helps to ensure that users cannot use any other DynamoDB or S3 actions or resources except the actions and resources that are specified in the policy.

**IAM Permissions.**
When IAM determines whether a permission is allowed, IAM first checks for the existence of any applicable **explicit denial policy**. If no explicit denial, it then checks for any applicable **explict allow policy.** If neither an explicit deny or and explicit allow policy exists, IAM reverts to default (**implicit deny**)
![](https://lh7-us.googleusercontent.com/zjdFKshbXU3wg2rFhZEDgYikqT3JTdVYsJbeQurJJ51-QUkezHpaW7ev1KYtArlJRV1MiOCOiAYIAYNDGvvxoZeL95T10twZ66xvnaIfScXXXoOfna-pLjetlMD-nua0fR1dXfF5ryVQ4ldpnPgygmg)
### Section 3 - Securing a new AWS Account.
You begin with a single sign-in identity that has complete access to all AWS services and resources in the account (**root user**) and it has ***full access to all resources.***
AWS recommends that you do not use account root user credential for day-to-day interaction with the account, instead, you can create additional users and assign permissions to the users.
Another recommendation is to require multi-factor authentication (MFA) for the account root user login and for all other IAM user logins.
AWS created **AWS CloudTrail** for storage the logs from all the API requests in 90 days before.
### Section 4 - Securing Accounts.
**AWS Organizations.** [[Module 2 - Cloud Economics and Billing#Section 3 - AWS Organizations.]]

**AWS Key Management Service (AWS KMS).**
Is a service that enables you to create and manage encryption keys and to control the use of encryption across a wide range of AWS services and your apps. AWS KMS also integrates with CloudTrail to provide you with logs of all key usage to help meet your regulatory and compliance needs.
Customer Master Keys (CMKs) are used to control access to data encryption keys that encrypt and decrypt your data. ^KMS

**Amazon Cognito.**
Provides solutions to control access to AWS resources from your app. You can define roles and map users to different roles so your app can access only the resources that are authorized for each user.
**Security Assertion Markup Language 2.0 (SAML 2.0)**, is an open standard for exchanging identity and security information with apps and services providers. ^629102

**AWS Shield.**
Is a managed DDoS protection service that safeguards apps that run on AWS. **Standard** is automatically enabled to all AWS customers at no additional cost, **advanced** is an optional paid service that provides additional protections against more sophisticated and larger attacks for your apps that run on EC2, ELB, CloudFront, Global Accelerator and Route 53. ^9345c3

### Section 5 - Securing data on AWS.
"Data at rest" refers to data that is physically stored on disk or on tape.
You can create encrypted file systems on AWS so that all your data and metadata is encrypted at rest by using the open standard Advanced Encryption Standard (AES)-256.

**Encryption of data in transit.**
Data in transit refers to data that is moving across the network. Is accomplished by using Transport Later Security (TLS)1.2 with AES-256. TLS = SSL.
AWS Certificate Manager is a service that enables you to provision, manage and deploy SSL or TLS certificates for use with AWS services and your internal connected resources.

**Securing Amazon S3 buckets and objects.**
AWS provides many tools and options for controlling access to your S3 buckets or objects:
- **Amazon S3 Block Public Access,** these settings override any other policies or object permissions. Enable it for all buckets that you don't want to be publicly accessible.
- **IAM policies.**
- **Bucket policies,** define access to specific buckets or objects.
- **Access Control Lists (ACLs),** are less commonly used.
- **AWS Trusted Advisor,** provides a bucket permission check feature that is a useful tool for discovering if any of the buckets in your account have permissions that grant global access.

### Section 6 - Working to Ensure Compliance.
AWS engages with external certifying bodies and independent auditor to provide customers with information about the policies, processes and controls that are established and operated by AWS.
AWS algo provides security features and legal agreements that are designed to help customers with common regulations and laws, like Health Insurance Portability and Accountability Act (HIPAA) and General Data Protection Regulation (GDPR).

**AWS Config.**
Is a service that enables you to assess, audit and evaluate the configurations of your AWS resources. AWS Config continuously monitors and records your AWS resource configurations and it enables you to automate the evaluation of recorded configuration against the desired configuration. Is a Regional service, to track resources across Regions, enable it in every Region that you use. ^be8150

**AWS Artifact.**
Provides on/demand downloads of AWS security and compliance documents, such as AWS ISO certifications, Payment Card Industry (PCI) and Service Organization Control (SOC) reports. You can submit the security and compliance documents to your auditor or regulators to demonstrate the security and compliance of the AWS infrastructure and services that you use. ^f5f864



[[Module 5 - Networking and Content Delivery.]]
