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
To assign permission to a user, group or role, 