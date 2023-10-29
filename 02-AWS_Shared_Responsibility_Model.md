# AWS Shared Responsibility Model

### "AWS has the responsibilty OF the cloud. Customer has the responsibility IN the cloud."

<img src="https://d1.awsstatic.com/security-center/Shared_Responsibility_Model_V2.59d1eccec334b366627e9295b304202faf7b899b.jpg" width="800px">
Source: https://aws.amazon.com/compliance/shared-responsibility-model/

As a customer of AWS - you are not responsible for the hardware, software, networking, and facilities that run AWS Cloud services across its regions, AZs,  data centers and edge locations.

Depending on the Cloud Model - AWS and it's customer share responsibilities for different layers. However, the customer is Never responsible for the virtualization or the underlying physical infrastructure.

1. Inherited Controls (AWS only)
    * Controls which a customer fully inherits from AWS.
    * Physical and Environmental controls
1. Shared Controls (AWS and Customer)
    * Patch Management
    * Configuration Management
    * Awareness & Training
1. Customer Controls (Customer only)
    * Service and Communications Protection
    * Zone Security
        * which may require a customer to route or zone data within specific security environments.

<img src="https://img.alicdn.com/tfs/TB1WyglO7voK1RjSZFwXXciCFXa-2305-1450.png" width="800px">


AWS is responsible for protecting and securing their infrastructure like whatever is in their data centers. Physical security of AWS data center. AWS maintains UPS, CRAC, fire suppression systems and more. AWS is responisble for any managed service and underlying software, operating system.

You are responsible for your data and applications. Application Data including encryption options. Security configuration - rotating credentials, APIs, VPC access etc. Patching guest operating system of EC2 instances. IAM - application security, identity and access management for systems. Network traffice - you are responsible for it including group firewall configuration.


### Report AWS abuse resource
Rotate your keys and change your password, then contact the AWS Trust & Safety team using the Report Amazon AWS abuse form.


##  [BACK](./05-AWS_Core_Services.md)  |  [NEXT](./03-AWS_Security_Best_Practices.md)