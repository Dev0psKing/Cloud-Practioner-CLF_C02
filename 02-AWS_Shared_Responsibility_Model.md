# AWS Shared Responsibility Model

![AWS Shared Responsibility Model](https://d1.awsstatic.com/security-center/Shared_Responsibility_Model_V2.59d1eccec334b366627e9295b304202faf7b899b.jpg)

Source: [AWS Shared Responsibility Model](https://aws.amazon.com/compliance/shared-responsibility-model/)

As an AWS customer, understanding the shared responsibility model is essential. AWS and its customers have distinct roles in ensuring the security and compliance of the cloud environment:

**AWS has the responsibility OF the cloud. The customer has responsibilities IN the cloud.**

## AWS Responsibilities
As an AWS customer, you are not responsible for the hardware, software, networking, and facilities that support AWS Cloud services across its regions, availability zones (AZs), data centers, and edge locations. AWS shoulders the following key responsibilities:

1. **Inherited Controls (AWS only):**
    - These are controls fully inherited from AWS, including physical and environmental controls.

2. **Shared Controls (AWS and Customer):**
    - Responsibilities shared between AWS and the customer include patch management, configuration management, awareness, and training.

3. **Customer Controls (Customer only):**
    - Customer-specific controls encompass service and communications protection, as well as zone security, which may require routing or zoning data within specific security environments.

![AWS Shared Responsibility Model Layers](https://img.alicdn.com/tfs/TB1WyglO7voK1RjSZFwXXciCFXa-2305-1450.png)

## Customer Responsibilities
Your responsibilities as an AWS customer encompass:

- **Data and Application Security:**
    - Ensuring the security of your data and applications, including encryption options and proper security configurations.
  
- **Identity and Access Management (IAM):**
    - Managing IAM for application security and controlling identity and access for your systems.

- **Network Traffic and Firewall Configuration:**
    - Managing network traffic and configuring group firewall settings.

- **Patching and Maintenance:**
    - Regularly patching guest operating systems of EC2 instances and maintaining the security of your AWS resources.

## Report AWS Abuse
If you suspect any abuse of AWS resources, take the following steps:

1. **Rotate Keys and Change Passwords:** Ensure that your AWS access keys and passwords are up to date and secure.
2. **Contact the AWS Trust & Safety Team:** Report the abuse to the AWS Trust & Safety team using the [Report Amazon AWS abuse form](https://aws.amazon.com/premiumsupport/knowledge-center/report-aws-abuse/).

By understanding and fulfilling your responsibilities within the AWS shared responsibility model, you can help maintain the security and compliance of your cloud environment.

[BACK](./05-AWS_Core_Services.md) | [NEXT](./03-AWS_Security_Best_Practices.md)