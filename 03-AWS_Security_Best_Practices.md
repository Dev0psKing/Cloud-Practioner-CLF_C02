# AWS Security Best Practices

_This is 25% of the weight of the exam_

## Root User
* Automatically created when you create an AWS account.
* Only root user can delete the account.
* There is just one root user that can exclusively:
    * Change your account settings. This includes the account name, email address, root user password, and root user access keys. 
    * Restore IAM user permissions. If the only IAM administrator accidentally revokes their own permissions, you can sign in as the root user to edit policies and restore those permissions.
    * Activate IAM access to the Billing and Cost Management console.
    * View certain tax invoices. An IAM user with the aws-portal:ViewBilling permission can view and download VAT invoices from AWS Europe, but not AWS Inc. or Amazon Internet Services Private Limited (AISPL).
    * Close your AWS account.
    * Register as a seller in the Reserved Instance Marketplace.
    * Configure an Amazon S3 bucket to enable MFA (multi-factor authentication).
    * Edit or delete an Amazon Simple Storage Service (Amazon S3) bucket policy that includes an invalid virtual private cloud (VPC) ID or VPC endpoint ID
    * Sign up for AWS GovCloud (US).
    * Request AWS GovCloud (US) account root user access keys from AWS Support.

_Best Practice:_ Identity and Access Management - create a new user and provide a role. Never use the root user unless absolutely required. Protect root account with MFA (Multi-factor authentication).

VPC - Vitual Private Cloud. Default VPC will always be created for you.
* AWS Management Console
    * Easy to navigate via web-browser.
    * Good for non-technical roles.
Use the search feature for easy access.
* AWS CLI - same features as the management console
    * New features show up here first.
    * Programmatic access provides access to your AWS resources.
* AWS SDK - can be leveraged to make changes to the environment via programmatic access. 

# Concepts

1. Authentication
    * An identity that is verified.
    * Credentials such as username and password.
1. Authorization
    * Determines which services and resources the idenitity has access to.
    * Permissions are granted via a policy.
1. Least Privilege
    * Give a user the minimum access required to get the job done.

# IAM 

1. [IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html)
    * A web service that allows you securely control access to AWS resources.
1. Users
    * Entities in IAM to represent a person or application that can be given access to your AWS resources.
    * Applications can be users. This is normally done via access keys.
1. Group
    * Collection of users - conveniently apply common permissions.
    * This is not EC2 Security Group - that is a firewall.
    * Can you nest groups? Can you have group inheritance? Are there unlimited groups that can be created?
1. Roles
    * Roles define access permissions and are temporarily assumed by an IAM user or service.
    * DevOps role, Lambda-Execution role are examples.
    * Access is assigned using policies.
    * You grant users in one AWS account access to resources in another AWS acccount using roles.
    * Attach a role to an EC2 instance for access to S3. Applications running on that instance will have access to S3 via roles. This is useful because the application will not need credentials or access keys. This is most secure.
1. Policies
    * You manage persmissions for IAM users, groups, and roles by creating a policy document in JSON format and attaching it. The policy itself is decoupled from IAM identitieis.
    * User - {Policy:Access} - Resource
    * Developer Group = {Policy: Resource Access} - Resource
    * Role - {Policy:Allow-S3-Access} - S3
    * How to limit access to an Amazeon S3 to specific users only? You can add a bucket access policy directly to an Amazon S3 bucket to grant IAM users accesss. I wonder if there is another way, create a special bucket access group with policy to the group, and then add users to the group. Or add users to the policy directly.
1. IAM Credentials Report 
    * Assistance with compliance and auditing by offering a downloadable report that lists all your IAM users in this account and the status of their various credentials including MFA devices in your account.

## Security Services

1. [WAF](https://aws.amazon.com/waf/) : XSS SQL-Injection 
    * WAF is a Web Application Firewall that can protect against common attacks such as XSS or SQL injection.
1. [Shield](https://aws.amazon.com/shield/) DDOS 
    * AWS Shielf is a managed DDOS protection service. Sheild standard is free but Sheild Advanced provides access to AWS experts for a fee.
    * DDOS protections from CloudFront, Route53, Elastic Load Balancing, and AWS Global Accelerator.
    * Receive real-time notifications of suspected DDoS incidents via CloudWatch metrics and assistance from AWS during the attack.
    * Automatically scrub bad traffic at specific layers: layer 3,4 and 7. Minimize application downtime and latency. Monitor and protect up to 1000 resource types.
1. [Macie](https://aws.amazon.com/macie/) Sensitive Data
    * hHelps you discover and protect sensitive data. Uses maching learning, evaluates S3 environment, uncovers PII information. 
    * Use cases: discover passport numbers stored on S3 using Macie. Find SSNs in S3 files.
1. [Config](https://aws.amazon.com/config/) Audit config
    * Assess, audit, and evaluate configurations of your resources.
    * Record and altert by storing in S3.
    * Use cases: Streamline operational troubleshooting and change management. Deploy a complicant-as-code framework. Continually audit security monitoring and analysis.
1. [GuardDuty](https://aws.amazon.com/guardduty/) Threat detection
    * Protect your AWS accounts with intelligent threat detection.
    * Continuously monitors workload for malicious activity and delivers detailed security findings for visibility and remediation. Network and API calls.
    * Use cases: Improve security operations visibility. Assist security analysts in investigations. Identify files containing malware. Route insightful information on security findings.
1. [Inspector](https://aws.amazon.com/inspector/) Vulnerability (EC2)
    * Automate vulnerability management at scale in EC2, Lambda and ECR container images and network exposure.
    * Automated vulnerability management service that continually scans workloads for software vulnerabilities and unintended network exposure. EC2.
    * Use cases: Quickly discover vulnerabilities in compute workloads. Prioritize patch remediation. Meet compliance requirements. Identify zero-day vulnerabilities sooner.
1. [Artifact](https://aws.amazon.com/artifact/) Compliance Report
    * Access Independent Software Vendor compliance report.
    * Use artifact to SOC and PCI compliance reports. You can generate the report. Access to the report can be provided. Self-service portal.
1. [Cognito](https://aws.amazon.com/cognito/) CIAM
    * Customer identity and acess management.
    * Delivery frictionless CIAM. Adaptive authentication, support compliance, and data residency requirements. Scale to millions of users with a fully managed, high-performantm and reliable identity store. Federate sign-in using OIDC or SAML 2.0 connect to a broad group of AWS services and products.
    * Use-cases: Social media accounts to log in to your application.

# Data Encryption and Secrets Management Services

1. [KMS](https://aws.amazon.com/kms/) Key Management
    * Key Management Service is multi-tenant encryption key management service. 
    * Create and control encryption keys managed by AWS used to encrypt or digitally sign your data.
    * Centrally manage keys and define policies across integrated services and application from a single point. 
    * Encrypt data within your applications with the AWS Encryption SDK data encryption library.
    * Encrypt EBS volume using KMS.
1. [CloudHSM](https://aws.amazon.com/cloudhsm/) Encryption Key Generator. 
    * Manage single-tenant hardware security modules (HSMs) on AWS.
    * Use case: Generate and use cryptographic keys on dedicated FIPS 140-2 Level 3 single-tenant HSM instances. Deploy workloads with high reliability and low latency, and help meet regulatory compliance. Pay by the hour, and backup and shut down HSMS when they're not needed. Manage HSM capacity and control your costs by adding and removing HSMs from your cluster.
1. [Secrets Manager](https://aws.amazon.com/secrets-manager/) Secrets Management
    * Use cases: Store secrets securely, manage acess with fine-grained policies, automate secrets rotation, audit and monitor secrets usage.
    * Database credentials, API keys, encrypt secrets at rest, integreates with RDS, DOcumentDB, Redshift.
    * Retrieve database credentials needed for your application code.  Secrets Manager allows you to retrieve database credentials with a call to Secrets Manager APIs, removing the need to hardcode sensitive information in plain text within your application code.
1. [AWS Certificate Manager](https://aws.amazon.com/certificate-manager/) Certificate Manager
    * Provisiong public and private certificats for free.
    * SSL/TLS certificates are supported.
    * Use key management for certs and get managed certificate renewal.
    * Integrates with Elastic Load Balancing, API Gateway and more.

##  [BACK](02-AWS_Shared_Responsibility_Model.md)  |  [NEXT](./04-AWS_Costs_Economics_Billing.md)