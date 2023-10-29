# 01 Value of AWS Cloud

AWS is faster, cheaper, durable and more reliable than most internally managed data centers.
### Public cloud general benefits 
1. Fast Global Deployment in Minutes
    * AWS has regions globally and deployments can be done in minutes.
1. Speed to Market with Agility
    * Faster innovation with AWS allows for faster delivery to customers.
1. Discounts from economies of scale 
    * Costs are shared across users and cheap due to economies of scale.
1. No upfront cost to running and maintaining data centers
    * Quickly get an application deployed without thinking about IT infrastructure.
1. OpEx in favor of CapEx
    * Capital Expenditures - are big upfront costs. Operating Expenses are funds to run day-to-day operations. The accounting department will care.
1. Elastic Capacity
    * No need to guess upfront Capacity - pay as you go.


### Non-functional requirements can be met with ease when hosting on public cloud
The following cloud terminology is important for the exam:
1. High Availability
    * Redundancy, and Failovers allow for a system to have longer uptimes.
1. Elasticity
    * Demand based capacity provisioning allows for optimal usage of resources that minimizes waste.
1. Agility
    * AWS Services can help customers innovate faster allowing for reduced time to market.
1. Durability
    * AWS provides data services that offer long-term data protection and storage.
1. Latency
    * Time elapsed between a user request and reponse. Low latency is a good thing.
### Cloud Computing Models

1. IaaS: Infrastructure as a Service e.g.EC2
1. PaaS: Platform as a Service e.g. Cloud9
1. SaaS: Software as a Service e.g. Sagemaker

[Click Here for details](https://aws.amazon.com/what-is-cloud-computing/?pg=TOCC)
## Cloud Hosting Models

1. Private Cloud: On-prem virtualization as well as off-prem fully managed private cloud, also with Amazone Outpost
1. Public Cloud: Fully publicly hosted and managed cloud.
1. Hybrid Cloud: AWS Direct Connect service connects customer's data center with Amazon.

## AWS Regions, AZs and Region

Amazon EC2 is hosted in multiple locations world-wide. These locations are composed of AWS Regions, Availability Zones, Local Zones, AWS Outposts, and Wavelength Zones.
1. [Region](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html)
    * Is a separate geographic area. Therefore if one is impacted by a natural disaster, chances are that another will not.
    * Regions are fully independent.
    * Services and resources vary by region.
    * No automagic replication across regions. 
1. [Availability Zone](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/)
    * An Availability Zone (AZ) is one or more discrete data centers with redundant power, networking, and connectivity in an AWS Region. 
    * AZs give customers the ability to operate production applications and databases that are more highly available, fault tolerant, and scalable than would be possible from a single data center. 
    * All AZs in an AWS Region are interconnected with high-bandwidth, low-latency networking, over fully redundant, dedicated metro fiber providing high-throughput, low-latency networking between AZs. 
    * All traffic between AZs is encrypted. 
    * The network performance is sufficient to accomplish synchronous replication between AZs. 
    * If applications are distrbuted - deploy to multiple AZs with load balancing.
1. [Data Center](https://aws.amazon.com/compliance/data-center/data-centers/)
    * Two or more data centers together are part of an AZ.
    * Each data center has protections across 4 layers:
    * Perimeter - secured perimeter for physical access.
    * Infrastrucutre - HVAC, power, fire suppression.
    * Data - servers within the building, racked and stacked.
    * Environment - site location, seismic data, flooding etc.
1. [Local Zones](https://aws.amazon.com/about-aws/global-infrastructure/localzones/)
    * A Local Zone is an extension of an AWS Region in geographic proximity to your users. 
    * Local Zones have their own connections to the internet and support AWS Direct Connect, so that resources created in a Local Zone can serve local users with low-latency communications. 
    * Local Zones provide you the ability to place resources, such as compute and storage, in multiple locations closer to your end users.
    * Use case: Run latency sensitive applications closer to the end users.
1. [Wavelength Zone](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html#concepts-wavelength-zones)
    * A Wavelength Zone is an isolated zone in the carrier location where the Wavelength infrastructure is deployed. Wavelength Zones are tied to a Region. 
    * A Wavelength Zone is a logical extension of a Region, and is managed by the control plane in the Region.
1. [Global Edge Network](https://aws.amazon.com/cloudfront/features/?p=ugi&l=na&whats-new-cloudfront.sort-by=item.additionalFields.postDateTime&whats-new-cloudfront.sort-order=desc) 
    * Amazon CloudFront peers with thousands of Tier 1/2/3 telecom carriers globally.
    * CloudFront is well connected with all major access networks for optimal performance, and has hundreds of terabits of deployed capacity. 
    * CloudFront edge locations are connected to the AWS Regions through the AWS network backbone - fully redundant, multiple 100GbE parallel fiber that circles the globe and links with tens of thousands of networks for improved origin fetches and dynamic content acceleration.these are cached closest to audience.
    * Mini-data centers created for low latency between applications and users.
    * There are many more edge locations than AZs or regions.


 # Leveraging the Well-Architected Framework
[AWS Well Architected](https://aws.amazon.com/architecture/well-architected/?wa-lens-whitepapers.sort-by=item.additionalFields.sortDate&wa-lens-whitepapers.sort-order=desc&wa-guidance-whitepapers.sort-by=item.additionalFields.sortDate&wa-guidance-whitepapers.sort-order=des=) helps cloud architects build secure, high-performing, resilient, and efficient infrastructure for a variety of applications and workloads.

1. Operational Excellence
    * Plan for and anticipate failure. 
    * Deploy smaller, reversible changes. 
    * Script infrastructure as code. 
    * Learn from failure and refine.
    * Use case: AWS CodeCommit for versioning application as well as infrastructure.
1. Security
    * Automate security tasks.
    * Encrypt data in transit and at rest.
    * Assign only the least privileges required.
    * Track who did what and when.
    * Ensure security at all application layers.
    * Use case: CloudTrail to log all actions performed on your account.
1. Reliability
    * Recover from failure automatically.
    * Scale horizontally for resilience.
    * Stop guessing capacity.
    * Manage change through automation.
    * Test recovery procedures.
    * Use Case: RDS on multi-AZ deployments.
1. Performance Efficiency
    * Use serverless architectures first.
    * Use multi-region deployments.
    * Delegate tasks to a cloud vendor.
    * Experiement with virtual resources.
    * Use Case: Lambda to run serverless compute workloads.
1. Cost Optimization
    * Utilize consumption-based pricing.
    * Implement Cloud Financial Management.
    * Measure overall efficiency.
    * Pay only for resources your application requires.
    * Use case: S3 Intelligent Tiering to automatically move your data between access tiers based on usage patterns.
1. Sustainability
    * Understand your impact.
    * Establish sustainability goals.
    * Maximize utilization.
    * Use managed services.
    * Reduce downstream impact.
    * Use Case: EC2 Auto-scaling to scale down when demand is low.


## [NEXT](./05-AWS_Core_Services.md)
