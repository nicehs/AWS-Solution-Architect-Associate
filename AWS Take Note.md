## AWS Take Note

### Lambda
- Auto Scaling
- First we invoke, lambda create a instance and automatically run code
- While first invoke is in progress, lambda will create another instance and run code
- Burst traffic 500 -> 3000 per region

### STS
- Temporary credential
- Provide credential in maximum 36h

### Aurora
- Serverless
  - Intermittent, unpridicable workload
  - On-demand, auto-scaling
  - Automatically increase size of data storage

- Provision
  - Must reserve size of instance, number replicate

### Dynamo
- Table
  - Use many unique partition key to spread I/O request (high-cardinality attributes). I/O request will spread cross physical partions

- Can't intergrated SNS directly. We must use Dynamo Stream -> Lambda -> SNS

- Dynamo Stream
  - Monitor data changes in real time

### AWS Artifact
- Provide compliance-related document

### AWS Directory
- AWS Directory Service AD Connector 
  - We can assign IAM Role to users and groups through AWS Directory Service AD Connector
- AWS Directory Service Simple AD
  - manage users, group memberships, policy

### AWS Control Tower
- Manage config, setup in multiple account
- Doesn't manage AWS resources

### API Gateway
- Intergrated: Cloudwatch, WAF, Lambda
- Throttling per account, per request (rate limit)
- Caching
- Rate limit: when 10 request come, it will process those simultaneously. Limit number of processing request is called rate lmit
- Burst limit: Additional limit processing request is calld burst. It mean when burst limit is 2, total allowed process is 12 request

### RPO vs RTO
- Indicate to disaster recovery plan in backup stragies
- RPO (Recovery Point Object): a point time that we want to recovery data (example: 1 minute ago, 1 day ago, ...)
- RTO (Recovery Time Object): it mean how many time data take to restore (example: within 2 hours, within 1 day)

### Permission boundary
- Maximum permission that user is allowed to access a resource
- Example: If a user assign in group Dev (S3 full permission) but you want restrict permission that only allow user list object, bucket. You must set permission boundary

### IAM
- Principle
  - Person or application that used an entity (user or role) to send request
  - 4 type: IAM user, AWS Service, IAM Role, Idp
- Federation
  - Use user that do not reside on AWS to login AWS

### ELB
- ALB can't attach EIP, just use DNS

### EMR
- Amazon EMR provides a managed Hadoop framework that makes it easy, fast, and cost-effective to process vast amounts of data across dynamically scalable Amazon EC2 instances. It securely and reliably handles a broad set of big data use cases, including log analysis, web indexing, data transformations (ETL), machine learning, financial analysis, scientific simulation, and bioinformatics. You can also run other popular distributed frameworks such as Apache Spark, HBase, Presto, and Flink in Amazon EMR, and interact with data in other AWS data stores such as Amazon S3 and Amazon DynamoDB.

### S3
- S3 Select enables applications to retrieve only a subset of data from an object by using simple SQL expressions. By using S3 Select to retrieve only the data needed by your application, you can achieve drastic performance increases. You can perform S3 Select to query only the necessary data inside the CSV files based on the bucket's name and the object's key.

### Cloudfront
- Origin Access Identity (OAI) is to restrict access to the origin server (such as an Amazon S3 bucket or a custom origin) and ensure that the content is only served through CloudFront. CloudFront authenticates itself to the origin server using the assigned OAI credentials. This allows CloudFront to retrieve the requested content from the origin and serve it to the user without the need for the user to authenticate directly with the origin server.

### EKS Anywhere and ECS Anywhere
- It is a deployment option that allow deploy EKS and ECS in customer-managed infrastructure (such as: on-primese)

### EC2
- Statement billed:
  - stopping prepare for hibernate
  - terminate during Reserved Instances purchase option

### Amazon Comprehend
- A natural language processing (NLP) service that uses machine learning to find meaning and insights in text.

### RDS
- Automated backup retention period for automated backup is only 35 days.

### Redshift
- We can copy snapshots for a cluster to another region

### Transit Gateway
A transit gateway attachment is both a source and a destination of packets. You can attach the following resources to your transit gateway:

- One or more VPCs

- One or more VPN connections

- One or more AWS Direct Connect gateways

- One or more transit gateway peering connections

If you attach a transit gateway peering connection, the transit gateway must be in a different Region.

### Cloudtrail
- Monitor account activity level

### Eventbridge
- Monitor changes maked by AWS services

### AWS Application Migration Service (AWS MGN)
The primary migration service recommended for lift-and-shift migrations to AWS.

### AWS Application Discovery Service
is primarily used to track the migration status of your on-premises applications from the Migration Hub console in your home Region

### Amazon SWF
provides useful guarantees around task assignments. It ensures that a task is never duplicated and is assigned only once. 

### EBS
io1:
- An io1 volume can range in size from 4 GiB to 16 TiB. You can provision from 100 IOPS up to 64,000 IOPS per volume on Nitro system instance families and up to 32,000 on other instance families. The maximum ratio of provisioned IOPS to the requested volume size (in GiB) is 50:1.
- For example, a 100 GiB volume can be provisioned with up to 5,000 IOPS. On a supported instance type, any volume 1,280 GiB in size or greater allows provisioning up to the 64,000 IOPS maximum (50 × 1,280 GiB = 64,000).

### AWS License Manager 
- a service that makes it easier for you to manage your software licenses from software vendors (for example, Microsoft, SAP, Oracle, and IBM) 

### AWS Resource Access Manager (AWS RAM)
AWS RAM is used securely share your resources across AWS accounts in your AWS organization and not for tracking or controlling software licenses.

### AWS VPC
- A single VPN tunnel still has a maximum throughput of 1.25 Gbps. If you establish multiple VPN tunnels to an Equal Cost Multipath Routing (ECMP)-enabled transit gateway, it can scale beyond the default limit of 1.25 Gbps.

### AWS AppSync
- A serverless GraphQL and Pub/Sub API service that simplifies building modern web and mobile applications. It provides a robust, scalable GraphQL interface for application developers to combine data from multiple sources, including Amazon DynamoDB, AWS Lambda, and HTTP APIs.

### AWS Wavelength
- combines the high bandwidth and ultralow latency of 5G networks with AWS compute and storage services so that developers can innovate and build a new class of applications.
- Wavelength Zones are AWS infrastructure deployments that embed AWS compute and storage services within telecommunications providers’ data centers at the edge of the 5G network, so application traffic can reach application servers running in Wavelength Zones without leaving the mobile providers’ network.

### ENA vs EFA
- An Elastic Fabric Adapter (EFA) is simply an Elastic Network Adapter (ENA) with added capabilities. It provides all of the functionality of an ENA, with additional OS-bypass functionality.
- **The OS-bypass capabilities of the Elastic Fabric Adapter (EFA) are not supported on Windows instances.**
- Amazon EC2 provides enhanced networking capabilities through the Elastic Network Adapter (ENA). It supports network speeds of up to 100 Gbps for supported instance types. Elastic Network Adapters (ENAs) provide traditional IP networking features that are required to support VPC networking.

### AWS ParallelCluster 
- is AWS-supported open-source cluster management tool that makes it easy for you to deploy and manage High-Performance Computing (HPC) clusters on AWS.

### Storage Gateway
#### File gateway
- Supported protocol: SMB, NFS
#### Volume gateway
- Supported protocol: iSCSI

### Transit Gateway
- AWS Transit Gateway also enables you to scale the IPsec VPN throughput with equal-cost multi-path (ECMP) routing support over multiple VPN tunnels. A single VPN tunnel still has a maximum throughput of 1.25 Gbps. If you establish multiple VPN tunnels to an ECMP-enabled transit gateway, it can scale beyond the default limit of 1.25 Gbps.

### Network Firewall
AWS Network Firewall is a stateful, managed, network firewall, and intrusion detection and prevention service for your virtual private cloud (VPC). With Network Firewall, you can filter traffic at the perimeter of your VPC.

You can use Network Firewall to monitor and protect your Amazon VPC traffic in a number of ways, including the following:

- Pass traffic through only from known AWS service domains or IP address endpoints, such as Amazon S3.

- Use custom lists of known bad domains to limit the types of domain names that your applications can access.

- Perform deep packet inspection on traffic entering or leaving your VPC.

- Use stateful protocol detection to filter protocols like HTTPS, independent of the port used.

### Network Access Analyzer 
A feature of VPC that reports on unintended access to your AWS resources based on the security and compliance that you set. 

### Reachability Analyzer
A configuration analysis tool that enables you to perform connectivity testing between a source resource and a destination resource in your virtual private clouds (VPCs).

### Lifecycle hook

### Cloudtrail
There are two types of events that you configure your CloudTrail for:

- Management Events

- Data Events

Management Events provide visibility into management operations that are performed on resources in your AWS account. These are also known as control plane operations. Management events can also include non-API events that occur in your account.

Data Events, on the other hand, provide visibility into the resource operations performed on or within a resource. These are also known as data plane operations. It allows granular control of data event logging with advanced event selectors. You can currently log data events on different resource types such as Amazon S3 object-level API activity (e.g. GetObject, DeleteObject, and PutObject API operations), AWS Lambda function execution activity (the Invoke API), DynamoDB Item actions, and many more.

### Beantalk
- Deploy code with no brain about infrastructure (just upload your code and enjoy :)
- Auto-scaling, load balacing, monitoring, place your containers across cluster
- Beantalk is free and just pay for infrastructure that you use
- Beantalk automatically choose infrastructure for you and you can't modify deployment infrastructure progress

### Cloudformation
- Write your infrastructure as code (YAML or Json)
- If Beantaik deploy code with no brain, with cloudformation you must write yaml (config resource, connection between resource)
- Flexible choose what resource include deployment infrastructure progress

### High Avaibility
- Failover + load balancing = high availability concept

### Athena
- Query Apache Parquet file faster than other file (CSV, Json)

### Push-button scalability
- This is just a very fancy term to say you can scale your instance resources using a graphical user interface. To be precise, it means that you can scale the size of an instance(memory, CPU, PIOPS, disk etc) either up or down, with the click of a button.

### DataSync and Data Migration
- Datasync transfer data at file and object level from on-primese to S3 or EFS or Amazon FSx for Windows File Server
- Data Migration migrate data from on-primese DB to AWS DB

### EFS
Performance mode: Number IOPS operation can execute
- General purpose performance mode (default): Ideal for latency-sensitive use cases.
- Max I/O mode: higher number operation can execute same time

Throughput Modes: Speed of data transfer (MiB/s or GiB/s)
-    Enhance Elastic - Use this mode for workloads with unpredictable I/O. With Elastic mode, your throughput scales automatically and you only pay for what you use.
-    Enhance Provisioned – Throughput is fixed at the specified amount.
-    “Bursting” – throughput scales with file system size.

