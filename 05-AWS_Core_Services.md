# AWS Core Services (and concepts)
 The following concepts and list of AWS Core Services are essential to understand various layers of an architecture.
AWS offers [Trusted Advisor](https://aws.amazon.com/premiumsupport/technology/trusted-advisor/) tool to business and higher subscriptions.
    * Provides recommendations that help you follow AWS best practices.
    * Benefits: cost optimization, performance, security, fault tolerance and service quotas.

 For example, a web-based enterprise application will utilize most if no all the layers and select technologies.
## Architecture

1. [Elasticity](https://www.ibm.com/cloud/blog/cloud-elasticity-vs-cloud-scalability): The ability to add or remove resources based on demand.
1. [Scalability](https://resources.sei.cmu.edu/asset_files/TechnicalNote/2006_004_001_14681.pdf): Scalability is the ability to handle increased workload by repeatedly applying a cost-effective strategy for extending a system’s capacity
1. [Fault Tolerance](https://en.wikipedia.org/wiki/Fault_tolerance): Is the property that enables a system to continue operating properly in the event of a failure of one or more faults withing some if its components.
1. [High Availability](https://redis.com/blog/high-availability-architecture/): Property of a system to serve the business without failure over a given period of time.
1. [Principle of least priviledge](https://www.cisa.gov/uscert/bsi/articles/knowledge/principles/least-privilege): Every program and every user of the system should operate using the least set of privileges necessary to complete the job. Primarily, this principle limits the damage that can result from an accident or error.

## Billing
1. [AWS Organization](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_introduction.html)
    * Account management services that enables you to consolidate multiple AWS Accounts into an organization that you create and centrally manage.
    * Use case: ease of billing, budgetary, security and compliance needs.
1. [Consolidated billing](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/consolidated-billing.html)
    * AWS Organizations has a management account that pays the charges of all the member accounts.
    * Multiple AWS Accounts can be consolidated for billing and payments.
## Security
1. [Firewall](https://aws.amazon.com/network-firewall/)
    * AWS Network Firewall automatically scales your network firewall to protect your managed infrastructure.
    * Open source rule formats and underlying rules engine easily implements policies.
1. [IAM](https://aws.amazon.com/iam/)
   * Identity and Access Managment (IAM) sets and manages guardrails and fine-grained access controls for your workforce and workloads.
   * Centrally connect identities to multiple AWS accounts.
   * Grant temporary security credentials for workloads that access your AWS resources.
   * Continually analyze access to right-size permissions on the journey to least privilege.
   * Usecase: "Who can access what" Who=users and workloads. Can access= Permissions with IAM policy. What=Resources within your AWS organization.
1. [Security Group (SG)](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-security-groups.html)
    * Is a virtual firewall for EC2 instances to control incomcing and outgoing traffic.
1. [User Credentials](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html)
    * Each identity has unique credentials within AWS.
    * Identity types: Account Root User, AWS Identity and Access Management user, AWS IAM Identity Center user and Federated identity.
1. [Access Control List (ACL)](https://docs.aws.amazon.com/AmazonS3/latest/userguide/acls.html): 
    * A firewall layer on the subnet level.
    * ACL cannot grant permissions to users in the account.
    * ACL can grant basic read/write permissions to other AWS accounts to buckets and objects.
## Networking and Content Delivery
1. [AWS Global Accelerator](https://aws.amazon.com/global-accelerator/) : Global Traffic
    * Improve application availability, performance, and security using the AWS global network.
    * Usecases: global traffic manager, API acceleration, Global static IP, low-latency gaming and media workloads.
    * Global accelerator sends your users through the AWS global network when accessing your content, speeding up delivery.
1. [AWS Transit Gateway](https://aws.amazon.com/transit-gateway/) : No more peering
    * AWS Transit Gateway connects your Amazon Virtual Private Clouds (VPCs) and on-premises networks through a central hub. 
    * Put an end to complex peering relationships. 
    * Highly scalable cloud router where each new connection is made only once.
1. [Virtual Private Cloud (VPC)](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html): Slice of the cloud
    * Foundational service that creates a private virtual network to launch resources.
    * Spans AZs in a region.
    * VPC A and VPC B can be [peered](https://docs.aws.amazon.com/vpc/latest/peering/what-is-vpc-peering.html) so they act as one logical VPC.You can create a VPC peering connection between your own VPCs, or with a VPC in another AWS account. The VPCs can be in different Regions (also known as an inter-Region VPC peering connection).
    * The default VPC always exists in every region. But all new VPCs are region specific.
1. [Subnet](https://docs.aws.amazon.com/vpc/latest/userguide/configure-subnets.html) : One per AZ
    * A subnet is a range of IP address in the VPC. This is a sub-network which allows you to split the network inside the VPC - it is where resources such as EC2 can be launched.
    * A private subnet is a good choice for hosting a Database - it will not be accessible directly from the Internet
    * A public subnet is a good choice for hosting a WebServer - however it requires a NACL, Router and IG to ensure Internet connectivity
    * Each subnet must reside entirely within one Availability Zone and cannot span zones. For HA, launch EC2 instances into subnets of separate AZs
    * Public subnet: The subnet has a direct route to an internet gateway. Resources in a public subnet can access the public internet.
    * Private subnet: The subnet does not have a direct route to an internet gateway. Resources in a private subnet require a NAT device to access the public internet.
    * VPN-only subnet: The subnet has a route to a Site-to-Site VPN connection through a virtual private gateway. The subnet does not have a route to an internet gateway.
    * A subnet CIDR reservation is a range of IPv4 or IPv6 addresses that you set aside so that AWS can't assign them to your network interfaces. 
1. [NACL versus Security Group](https://gocloudtech.medium.com/aws-security-groups-vs-nacl-whats-the-difference-a38b9eb6796b) Subnet and Instance traffic rules.
    * NACL is `stateless` and allow one-way traffic i.e. separatly specific inbound and outbound traffic to the subnet.
    * NACL allow and deny rules are supported. NACLs have an implicit `deny`. NACL rules are processed in order.
    * Security Group is stateful i.e. rules for inbound and outbound to EC2 instances are same. They allow return traffic.
    * Security Group only supports `allow` rules. 
1. [CloudFront](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html): CDN
    * A Content Delivery Network (CDN)
    * Provides low latency for content delivery.
    * Global distribution even when it is hosted in a region.
    * Static and dynamic web content. How? Edge location to cache content. 
1. [Route53](https://aws.amazon.com/route53/): DNS
    * DNS Service that routes users to Internet applications.
    * Domain Name System - a DNS server translates a domain name to an IP address.
    * Performs health checks on AWS resources
    * Supports hybrid cloud architectures - makes DNS resolution easier
1. [AWS Direct Connect](https://docs.aws.amazon.com/directconnect/latest/UserGuide/Welcome.html): VLAN
    * Dedicated physical network connection from your on-premises data center to AWS
    * Data travels over a private network - virtual LAN from on-prem data center over ethernet fiber optic cable.
    * Supports hybrid cloud architecture e.g. host database in the private cloud and the application on the public cloud, direct connect ensures the two talk and allows for data sovereignity 
    * Use case: Transfer internal data directly to AWS bypassing your ISP, or, build hybrid models or transfer large data sets to AWS.
1. [AWS VPN](https://aws.amazon.com/vpn/): VPN
    * Site-to-site VPN creates a secure connection between your internal network and your AWS VPCs.
    * Similar to Direct Connect - but the data travels through the public internet
    * Cheaper than Direct Connect 
    * Customer Gateway hosted on-prem connects with a virtual private gateway to establish a site-to-site VPN over the Internet via an ISP.
1. [API Gateway](https://aws.amazon.com/api-gateway/): API Management
    * Build, manage, secure, and scale APIs.
    * API Gateway can invoke services such as Lambda functions.
    * Support RESTful APIs and WEBSOCKET APIs.
## Compute
1. [Lambda](https://aws.amazon.com/lambda/): Serverless Compute
    * Serverless: write functions and deploy. AWS manages the servers but no direct access.
    * Scales automatically - no need to configure, patch or manage.
    * Use case: Real-time file processing, sending email notifications, Backend business logic
    * Supports Java, Go, PoweShell, Node.Js, C#, Python, and Ruby. Executes code in response to events, timers or other triggers. Lambda has ’re actively hiring engineers as we respond to changing market conditr - deploy a db or web server whatever you need
    * SSH securly connects with a key pair. SSH Client uses private key, the EC2 instance uses a public key
    * EIC is EC2 Instance Connect - uses IAM polices to control SSH access to your instances 
    * AWS Systems Manager- use a web browser, or AWS CLI to manage EC2 instances directly
1. [ELB](https://aws.amazon.com/elasticloadbalancing/): Block Storage
    * Distribute network traffic to improve application scalability.
    * Elastic Load  Balancing and Auto-Scaling is offered by EC2.
    * Automatically distribute load across servers - classic, application, gateway and network load balancers.    
1. [Fargate](https://aws.amazon.com/fargate/): Containers
    * Serverless compute engine for containers.
    * Manages containers like Docker.
    * Scaled automatically - and serverless.
1. [ECS](https://aws.amazon.com/ecs/): Containers
    * Elastic container service.
    * Run highly secure, reliable, and scalable containers.
1. [EKS](https://aws.amazon.com/eks/): Containers
    * Amazone Elastic Kubernetes Service.
    * Start, run, and scale Kubernetes.
1. [Lightsail](https://aws.amazon.com/lightsail/): IAC
    * Quickly lauch all resources you need for small projects.
    * Simple for folks with no cloud experience.
    * Low and predictable fees.
1. [Outpost](https://aws.amazon.com/outposts/): Hybrid Cloud
    * Run AWS Infrastructure and services on premises for a consistent hybrid cloud architecture.
    * Allows cloud services in the internal data ’re actively hiring engineers as we respond to changing market conditcenter
    * Useful for latency or data sovereignty needs
    * Used for hybrid experience
1. [Batch](https://aws.amazon.com/batch/): IAC Spot
    * Process large workloads in smaller chunks.
    * Dynamically provisions instances based on volume.
    * Example - send high volume email 1000 emails at a time or process ML.

## Operational Databases and Caching
1. [Relational Database Service (RDS)](https://aws.amazon.com/rds/)
    * Launch, manage and scale relational databases on the cloud. Supports Aurora, PostgreSQL, MySQL, MariaDB, Oracle, SQLServer.
    * Offers HA, fault tolerance using Multi-AZ deployment option.
    * AWS manages the database with automatic software patching, automated backups, OS updates.
    * Launch read-repliccas across Regions in order to provide enhanced performance and durability.
    * Does not automatically add capacity or storage.
1. [Aurora](https://aws.amazon.com/rds/aurora/)
    * AWS build Aurora for the cloud compatible with MySQL and PostgreSQL - created by AWS.
    * Supported MySQL and PostgreSQL database enginges. 5x and 3x faster that native.
    * Scales automatically by adding capacity and storage while providing durability and high availability.
    * Backs up to S3, replication to multiple region and storage across 6 stores.
1. [DynamoDB](https://docs.aws.amazon.com/dynamodb/index.html)
    * Fully managed serverless NoSQL key-value and document database.
    * Scales automatically to massive workloads.
    * Adds capacity automatically.
1. [DocumentDB](https://aws.amazon.com/documentdb/)
    * Fully managed document database that supports MongoDB.
    * Serverless, scales enterprise workloads using a fully managed native JSON document database.
1. [Neptune](https://aws.amazon.com/neptune/)
    * Graph database service, fully managed and serverless.
    * Fast, reliable and durable.
    * User profiles and social connections.
    * Usecases: Customer360, Detect fraud patterns, machine learning predictions, IT security detection and investigation.
1. [ElastiCache](https://aws.amazon.com/elasticache/)
    * Microsecond latency and scale with in-memory caching.
    * In-memory data cache compatible with [Redis and Memcache](https://aws.amazon.com/elasticache/redis-vs-memcached/).
    * High-performance, low latency and no durability.
    * Usecases: Application performance, ease backend database load, low latency data retrieval needs.

## Data Migration and Transfer
1. [Database Migration Service](https://aws.amazon.com/dms/)
    * 
    * [Feature rich tool](https://aws.amazon.com/dms/features/) that helps you migrate databases to or within AWS.
    * Homogenous and hetrogenous databases can be migrated with virtually no downtime.
    * Data is synchronized between the source and target continuously.
1. [Server Migration Service](https://aws.amazon.com/server-migration-service/): Deprecated in favor of AWS MGN (AWS Application Migration Services)
    * AWS Server Migration Service will automatically replicate live server volumes to AWS and create Amazon Machine Images (AMI) as needed.
    * This is being discontiuned in favor of AWS Application Migration Service.
1. [Application Migration Service](https://aws.amazon.com/application-migration-service/): Lift and Shift
    * Migrate applications from any source infrastructure that runs supported operating systems.
    * Application Migration Service is the next generation of CloudEndure Migration
1. [Snow Family](https://aws.amazon.com/snow/)
    * Move large amounts of data to and from AWS physically or process data at the edge.
    * Snowcone: Smallest member holds 8TB of usable storage, collect process
    * 
    * Snowball: 80TB. Cheaper And Snowball Edge used for petabyte scale data migration and has local processing when in a remote environment - supports EC2 and lambda. 
    * Snowmobile: 100PB. Multi-perabyte or exabyte scale. Data loaded to S3 - securely transported with escort vehicle.
1. [Data Sync](https://docs.aws.amazon.com/datasync/latest/userguide/what-is-datasync.html) Data Transfer Service
    * Data transfer online with speeds are 10x faster. 
    * Data replication cross-region and cross-account.
## Data Analytics
1. [RedShift](https://aws.amazon.com/redshift/) : Data warehouse
    * Data warehouse: data storage solution with historical data from disparate sources. 
    * Business intelligence, querying and business intelligence.
    * Handles exabyte-scale data.
    * Use case: Data consolidation. Run a database when it doesn't require CRUD.
    * Analytics - allows querying to gain business insights.
1. [Glue](https://aws.amazon.com/glue/) : ETL
    * 
    * Discover, prepare, and integrate all your data at any scale.
    * ETL Service.
    * Prepare to better understand your data.
1. [Lake Formation](https://aws.amazon.com/lake-formation/) : Data Lake
    * Build, manage, and secure data lakes in days.
    * Create, administer, and protect data lakes using familiar database-like features quickly.
1. [QuickSight](https://aws.amazon.com/quicksight/): BI
    * Business Analytics visualization of data with interactive dashboards that can be embedded in your applications
1. [Athena](https://aws.amazon.com/athena/) : SQL for S3
    * Analyze petabyte-scale data where it lives with ease and flexibility.
    * S3 SQL. Pre-configured to work with Glue.
    * Query service to analyze data using SQL. It is serverless.
    * Use cases: run federated queries across relational, nonrelational, object, and custom data sources running on premises or in the cloud. Use ML models in SQL queries or Python. Build distributed big data reconciliation engines. Analyze google analytics data by using AppFlow to store in S3 to query it.
1. [Data Pipeline](https://aws.amazon.com/datapipeline/) : 
    * Helps you move data between compute and storage services running either AWS or on-premises
    * Move data based on conditions, intervals and sends notifactions
    * Move from S3 to Redshift.
## Big Data and Search
1. [EMR](https://aws.amazon.com/emr/) Map Reduce
    * Process large amounts of data via map reduce.
    * Analyze data using Hadoop and Apache Spark.
    * Usecase: Perform big data analytics, build scalable data piplelines, process real-time data streams, accelerate data science and ML adoption.
2. [OpenSearch](https://aws.amazon.com/opensearch-service/) Interactive Log Analytics
    * Search petabytes of unstructured data.
    * 
    * Open source Elastic Search, Open Search Dashboard and Kibana.

## Streams
1. [Kinesis](https://aws.amazon.com/kinesis/): Stream proecessor 
    * Easily collect, process, and analyze video and data streams in real time.
    * Usecase: Real-time video and data streams, IoT Data, Click Log, Web Stream logs are good use-cases.
    * Evolve from batch to real-time analytics.
1. [MSK](https://aws.amazon.com/msk/): Kafka
    * Managed Streaming for Apache Kafka.
    * Usecase: Ingest and process log and event streams, run centralized state or data buses, power your event-driven systems.
## Artificial Intelligence and Machine Learning
1. [Rekognition](https://aws.amazon.com/rekognition/)usecases: Computer Vision
    * Automate image and video analysis
    * Identify custom labels in image and video
    * Use cases: Analyze pizza images to ensure toppings
1. [Comprehend](https://aws.amazon.com/comprehend/): NLP
    * Natural Language Processing (NLP) Service that finds relationships in text
    * Customer sentiment analysis on social media
1. [Polly](https://aws.amazon.com/polly/): Speech-to-text
    * High quality natural sounding human voices in dozens of languages.
    * Customize Text to speech output with Speech Synthesis Markup Language tags.
    * Usecases: Generate speech in dozens of languages, engage customers with a natural-sounding voice, adjust speaking style, speech rate, pitch and loudness.
1. [SageMaker](https://aws.amazon.com/sagemaker/): ML
    * Machine Learning service.
    * Helps you build, train and deploy machine learning models quickly.
    * Prepare data for models, train and deploy models, provides deep learning AMIs.
    * Recommendation engine for movies, music etc.
1. [Translate](https://aws.amazon.com/translate/): Translate
    * Provides language tanslation and support many languages and content formats.
    * Use case: Add localization to websites and applications.
    * 
1. [Lex](https://aws.amazon.com/lex/): Chatbot
    * Chatbots with conversational AI.
    * Helps you build conversational interfaces like chatbots.
    * Recognize speech and understand language.
    * Powers Amazon Alexa.
    * Integrate voice into device.
    * Usecases: Build virtual agents and voice assistants, automate informational responses, improve productivity with application bots, maxminize the information trapped in transcripts.
## Storage
1. [Simple Storage Service S3](https://docs.aws.amazon.com/cli/latest/reference/s3/) - Regional Service with global namespace and bucket policies
    * Unique name across all buckets in AWS
    * 11 9s of durability: regional level redundancy
    * 4 9s of availability 
    * S3 does not automatically replicate across regions - it can be setup.
    * Usecase: Host static websites, data archivale, analytics such as redshift and athena. Upload with S3 transfer acceleration for file uploads from mobile applications.
    1. S3 Storage Class
        * Standard: Durable 11-9s. 4-9s available.
        * Intelligent Tiering: Unknown or changing access. Standard durability with 3-9s availability
        * Infrequent Access: For Long-Lived, Infrequently Accessed, Millisecond access when needed. Durable with 3 9s availability. 
        * One-Zone Infrequent Access: Cost 20% less than IA. Use if data is recreatable, infrequent millisecond access, availability is 99.5%.
        * Glacier: Data retrieval options 1-5 minutes, 3-5 hours, 5-12 hours. Multiple AZs. Standard durability. Cheap storage options.
        * Glacier Deep Archieve: 12hrs or 48hr retrieval options. Cheapest. Long-term data archivale accessed once or twice a year. No availability - but standard durability.
        * Outposts: Data that needs to be kept local. Demanding application performance needs.
    1. Buckets: Root level 'folders' for file storage
        * Folder
        * Object Durability
        * Object Availability
        * Object Lifecycle
        * Object sharing
        * Object versioning
    1. [S3 Transfer Acceleration](https://aws.amazon.com/s3/transfer-acceleration/)
    * S3TA improves uploads and downloads to and from S3 buckets between 50% and 500%.
    * Moves data faster over longer distances.
    * Shorten distance to S3 via CloudFront.
1. [EC2 Instance Storage](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Storage.html)
    * Emphemeral storage that is temporary block-level for your instance.
    * Lasts during the life of the instance. 
    * It is temporary block-level storage for instances. 
    * Provides local fastest I/O.
1. [EBS - Elastic Block Storage](https://aws.amazon.com/ebs/)
    * Scalable block storage at any scale. Raw volume.
    * Good for database storage. 
    * HDD with an independent life from the instance it is attached to. 
    * Only one per instance.
    * Use cases: Build SAn in the cloud for I/O intensive applications, Run relational or NoSQL databases, reight-size your big-data analytic engine.
1. [EFS - Elastic File System](https://aws.amazon.com/efs/) : Shared file system.
    * EFS file system as a common data source for workloads and applications running on multiple instances
    * Regional serverless network file system. Like dropbox. 
    * Only for Linux filesystems. 
    * Shared directories. Expensive option.
    * 11-9s durability and 4-9s availability.
1. [Storage Gateway](https://aws.amazon.com/storagegateway/): Hybrid storage 
    * On-prem extends storage to cloud.
    * Some on the cloud, some local. File directory - some hosted locally some on the cloud. 
    * Moving backups to the cloud. 
    * Reduce costs by being selective, opt for low latency local files.
1. [AWS Backup](https://aws.amazon.com/backup/): Backup and recovery
    * Create a backup plan for all storage.


## Messaging and Integration Services

1. [SQS](https://aws.amazon.com/sqs/): Queue
    * Fully managed message queuing for microservices, distributed systems, and servlerless applications.
    * Sends messages on a queue between publisher and a single subscriber.
    * Securely send sensitive data between applications and centrally manage your keys using AWS Key Management.
    * Reliably deliver large volumes of data, at any level of throughput, without losing messages or needing other services to be available.
    * Usecase: architect a loosely coupled system architecture such as money transfer application. Improve performance and scalability. Requests are processed in FIFO.
1. [SNS](https://aws.amazon.com/sns/): Topic
    * Simple Notification Service - Fully managed Pub/Sub service for A2A and A2P messaging.
    * A2P with SMS, texts, push notifactions and email (plain text).
1. [SES](https://aws.amazon.com/ses/): Email
    * Sends rich text HTML Emails from your applications.
    * Get reliable, scalable email to communicate with customers at the lowest industry prices.
    * Marketing campaigns, and professional richly formatted HTML text.

## Developer Tools
1. [Cloud9](https://aws.amazon.com/cloud9/): IDE
    * IDE write and debug code in your browser
    * Build serverless applications - preconfigures environment.
1. [CodeCommit](https://aws.amazon.com/codecommit/) : Git
    * Source Control system for private Git repositories.
1. [CodeBuild](https://aws.amazon.com/codebuild/): Build Server
    * Allows you to build and test your applicaton source code.
    * Compiles source code and runs tests. 
    * Enables CI-CD
    * Produces build artifacts ready to be deployed
1. [CodeDeploy](https://aws.amazon.com/codedeploy/) : Delivery Server
    * Automate code edeployment to maintain application uptime.
    * Manage the deployment of code to on-premises as well as cloud.
    * Use prepackaged build environments or your own, and encrypt artifacts with your own keys.
    * Maintain application uptime, deploy to EC2, lambda, fargate and others.
    * Supports rolling deployments - it minimizes application downtime. 
1. [CodePipeline](https://aws.amazon.com/codepipeline/):  Release Server
    * Automate release pipelines with CI-CD. 
    * AWS offers continuous integration and continuous delivery service.
1. [CodeStar](https://aws.amazon.com/codestar/features/): Pre-configured CI-CD with CodeCommit, CodeBuild, CodeDeploy and CodePipeline out of the box.
    * AWS CodeStar allows you to accelerate application delivery by providing a pre-configured continuous delivery toolchain for developing, building, testing, and deploying your projects on AWS. 
1. [X-Ray](https://docs.aws.amazon.com/xray/latest/devguide/aws-xray.html): NDC Logs
    * X-Ray uses trace data from the AWS resources that power your cloud applications to generate a detailed service map. Typically, applications use nested diagnostic context (NDC) for distributed tracing for microservices.
    * The service map shows the client, your front-end service, and backend services that your front-end service calls to process requests and persist data. 
    * Use the service map to identify bottlenecks, latency spikes, and other issues to solve to improve the performance of your applications.
## Deployment and Infrastructure Management Service

1. [CloudFormation](https://aws.amazon.com/cloudformation/): IaC
    * Speed up cloud provisioning with infrastructure as code (IaC).
    * A CloudFormation template describes your desired resources and their dependencies so you can launch and configure them together as a stack. 
    * JSON and YAML are supported - define templates to create stacks.
    * Repeatable process for provisioning of resources.
    * Usecase: automate the infrastructure-provisiong for EC2 servers
1. [Elastic Beanstalk](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/Welcome.html): IaC for dummies
    * Deploy your web applications and services to AWS and not on-prem.
    * Orchestration service that provisions resources.
    * Automatically handles deployments, handles capacity provisioning, load balancing and auto-scaling.
    * Monitors application health via a health dashboard.
    * Usecase: Quickly deploy a scalable Java-based web application to AWS.
1. [OpsWorks](https://aws.amazon.com/opsworks/): DevSecOps
    * Automate operations with Chef and Puppet on-premises or AWS.
    * OpsWorks has three offerings, AWS Opsworks for Chef Automate, AWS OpsWorks for Puppet Enterprise, and AWS OpsWorks Stacks.

## Auditing, Monitoring and Logging

1. [CloudTrail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-user-guide.html): Audit Trails
    * Log and retain account activity as well as unusual activity - enable operational and risk auditing, governance, and compliance of your AWS account
    * Actions taken by a user, role, or an AWS service are recorded as events in CloudTrail. 
    * Events include actions taken in the AWS Management Console, AWS Command Line Interface, and AWS SDKs and APIs.
    * If a user terminates an EC2 instance via an API. Cloudtrail will be able to tell which user took that action.
    * Username, event time and name, IP address, access key, region, and error code can be tracked.
1. [CloudWatch](https://aws.amazon.com/cloudwatch/): Logs
    * Observe and monitor resources and applications on AWS, on premises, and on other clouds e.g. EC2 on AWS can be watched.
    * Amazon CloudWatch is a monitoring and management service for AWS, hybrid, and on-premises applications and infrastructure resources.
    * Performance and operational data in the form of logs and metrics.
    * Use to detect anomalies in your environment. Set alarms.
    * Use cases: Monitor full stack (applications, infrastructure, network, and services) and use alarms, logs, and events data to take automated actions and reduce mean time to resolution (MTTR). 

1. [Amazon Workspace](https://clients.amazonworkspaces.com/) : VDI
    * Allows you to host virtual desktops in the cloud.
    * Enables employees to work from Home with no data stored on local devices.
    * Use cases: Desktop as a service, Virtual Desktop (VDI).

1. [Amazon Connect](https://aws.amazon.com/connect/) : Contact Center
    * Provide customer service at a lower cost with a cloud contact center.
    * Cloud contact center service.
    * Provides customer service functionality.
    * Improves productivity of help desk.
    * Use cases: omnichannel self-service experience, agent productivity with AI, optimize from insights.


    ##  [BACK](./01-Value_Of_AWS_Cloud.md)  |  [NEXT](./02-AWS_Shared_Responsibility_Model.md)