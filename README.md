# AWS_documentation

IAM - IAM stands for Identity and Access Management, a web service in AWS that helps control access to AWS resources: 
1. User identities: IAM allows you to manage user identities 
2. Access permissions: IAM allows you to manage access permissions for users and applications 
3. Security policies: IAM allows you to manage security policies 
4. AM roles: IAM roles are entities that you create and assign specific permissions to 


Login to amazon console through root user account.

We can Use IAM to give someone access to the account and give them some kind of permisssions.

When ever we created a IAM account to an user there will be some groups where we can add then to the particular group and give permissions accordingly

So to login into IAM account we have some ID or we can create some alias and there will be userid and password now user can login into his account.


# IAM policies:

# IAM MFA

# AWS access keys:
AWS access keys are a set of credentials used to authenticate and authorize programmatic access to Amazon Web Services (AWS). They are essential for accessing AWS services through the AWS Command Line Interface (CLI), Software Development Kits (SDKs), or APIs.

Components of an AWS Access Key
Access Key ID:

A unique identifier for the key.
Example: AKIAIOSFODNN7EXAMPLE.
Secret Access Key:

A secret string that works like a password, used to sign API requests.
Example: wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY.
How Access Keys Work
When you make a request to AWS, the Access Key ID is included in the request to identify the user or application making the call.
The Secret Access Key is used to generate a signature, which verifies the request's authenticity.
Types of Access Keys
Root User Access Keys:

Associated with the root AWS account.
Highly sensitive and should not be used for daily tasks or programmatic access.
IAM User Access Keys:

Created for Identity and Access Management (IAM) users.
Provide controlled and limited access to AWS services, adhering to the principle of least privilege.
Managing AWS Access Keys
Creation:

Keys are created via the AWS Management Console, AWS CLI, or SDKs for IAM users.
Storage:

Keys should be stored securely (e.g., in environment variables, AWS Secrets Manager, or a credentials file).
Rotation:

Regularly rotate keys to enhance security.
Update applications or scripts with the new keys during rotation.
Deletion:

Delete unused keys to minimize security risks.
Best Practices
Use IAM roles instead of access keys when working with AWS services in environments like EC2 or Lambda.
Never share access keys or include them in source code repositories.
Monitor and audit key usage through AWS CloudTrail.
Apply policies to limit access based on the principle of least privilege.


# AWS CLI

# Connecting AWS To command prompt

```
aws configure
```
Enter access key 
Enter password 
Enter Region
Enter Output format

# command to print all the users

```
aws iam list-users

```

# IAM roles:
An AWS Identity and Access Management (IAM) role is a mechanism for granting temporary access permissions to AWS resources without requiring access keys or passwords. IAM roles are commonly used to delegate permissions to services, applications, or users for specific tasks in a secure and scalable way.

Key Characteristics of IAM Roles
Temporary Security Credentials:

When an entity assumes a role, AWS generates short-term access keys (Access Key ID, Secret Access Key, and Session Token) that expire after a specified time.
This reduces the risk associated with long-lived credentials.
No Static Credentials:

Unlike IAM users, roles do not have fixed credentials. Permissions are assigned through policies.
Assumable:

A role must be assumed by an entity, such as:
AWS services (e.g., EC2, Lambda, ECS).
Users or applications from another AWS account.
Federated users from external identity providers.
Use Cases for IAM Roles
AWS Service Access:

Grant an EC2 instance access to S3, DynamoDB, or other services without embedding credentials.
Cross-Account Access:

Allow resources in one AWS account to access resources in another account securely.
Federated Access:

Enable users from an external identity provider (like Google Workspace or Active Directory) to assume roles and access AWS resources.
Delegating Permissions to Applications:

Allow applications or workloads to access AWS resources securely.
Temporary Administrative Access:

Assign temporary elevated permissions to users or services for specific tasks.
How IAM Roles Work
Define the Role:

Specify a trust policy that defines which entities (users, AWS services, or accounts) can assume the role.
Attach permissions policies that dictate what actions are allowed for the role.
Assume the Role:

The entity requesting the role (e.g., EC2, Lambda, or an IAM user) sends a request to AWS.
If the request matches the trust policy, AWS returns temporary credentials.
Use Temporary Credentials:

The entity uses the temporary credentials to interact with AWS services according to the permissions policy.
Example: Role for EC2 Instance to Access S3
Create an IAM role with:

A trust policy allowing the EC2 service to assume the role.
A permissions policy allowing s3:GetObject and s3:PutObject on a specific S3 bucket.
Attach the role to an EC2 instance.

The instance can now access the S3 bucket without needing static credentials, as AWS provides temporary credentials.

Best Practices for IAM Roles
Use Roles Over Access Keys:

Avoid embedding credentials in code. Assign roles to AWS resources instead.
Follow the Principle of Least Privilege:

Grant only the permissions required for the task.
Use Role Sessions:

Use unique session names for better tracking and auditing.
Monitor Role Usage:

Enable AWS CloudTrail to log who or what is assuming a role.
Rotate and Expire Temporary Credentials:

Leverage automatic expiration of temporary credentials for enhanced security.




