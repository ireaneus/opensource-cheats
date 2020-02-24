# Microsoft AZ-900 Certification notes

[Back](README.md) to Linux CheatSheets by Ireaneus

## Azure Services

- Public Preview:
- Private Preview:

## Compliance Offerings

- Criminal Justice Information Services - CJIS
- Cloud Security Alliance (CSA) STAR Certification
- General Data Protection Regulation (GDPR)
- EU Model Clauses
- Health Insurance Portability and Accountability Act (HIPAA)
- International Organization for Standardization(ISO)
- International Electrotechnical Commission (IEC)
- Multi-Tier Cloud Security (MTCS) Singapore
- Service Organization Controls (SOC) 1,2, and 3.
- National Institute of Standards and Technology (NIST) Cybersecurity Framework (CSF)
- UK Government G-Cloud

Economies of scale - lower power, cooling, network costs

## Infrastructure as a Service(IaaS)

Requires the most user management of all the cloud services. The user is responsible for managing the operating systems, data, and applications.

**Definition:**

> - Managed by Cloud Provider: networking,storage,servers,virtualization.
> - Managed by Client: OS,Middleware,runtime,data,applications.

- Migrating workloads
- Test and development
- Website hosting
- Storage, backup, and recovery

## Platform as a service (PaaS)

Requires less user management. The cloud provider manages the operating systems, and the user is responsible for the applications and data they run and store.

**Definition:**  *is a complete development and deployment environment in the cloud - OS, Middleware and runtime.  Client managed Data, applications*

- Development framework
- Analytics or business intelligence

## Software as a service (SaaS)

Requires the least amount of management. The cloud provider is responsible for managing everything, and the end user just uses the software.

**Definition:**  *provides a complete software solution that you purchage on a pay as you go. Salesforce, Office365*

## Public, private, hybrid cloud

### Public

- Multi-tenant implementation
- Owned and operated by Service provider
- Bound by multi-tenant data management policies
- Similar self-service and automation capabilities as private cloud

#### public cloud best use

- Transitioning to cloud
- New applications
- Standard workloads
- Not as much customization

### Private cloud

*A private cloud consists of computing resources used exclusively by one business or organization.*

- On site datacenter or isolated in a public datacenter
- Flexibility
- Upfront capital expenses
- Highly secure
- Customization

### Hybrid Cloud

*Often called “the best of both worlds,” hybrid clouds combine on-premises infrastructure, or private clouds, with public clouds so organizations can reap the advantages of both*

- Transition to cloud
- Enhanced security
- Some data apps system on prem.

## 8 services

### Compute

| Compute Service | Description |
| --- | ---|
| Azure Virtual Machines | Windows or Linux virtual machines (VMs) hosted in Azure |
| Azure Virtual Machine Scale Sets | Scaling for Windows or Linux VMs hosted in Azure |
| Azure Kubernetes Service | Enables management of a cluster of VMs that run containerized services |
| Azure Service Fabric | Distributed systems platform. Runs in Azure or on-premises |
| Azure Batch | Managed service for parallel and high-performance computing applications |
| Azure Container Instances | Run containerized apps on Azure without provisioning servers or VMs |
| Azure Functions | An event-driven, serverless compute service |
| | |

### Networking

| Network Service | Description |
| --- | --- |
| Azure Virtual Network | Connects VMs to incoming Virtual Private Network (VPN) connections |
| Azure Load Balancer | Balances inbound and outbound connections to applications or service endpoints |
| Azure Application Gateway | Optimizes app server farm delivery while increasing application security |
| Azure VPN Gateway | Accesses Azure Virtual Networks through high-performance VPN gateways |
| Azure DNS | Provides ultra-fast DNS responses and ultra-high domain availability |
| Azure Content Delivery Network | Delivers high-bandwidth content to customers globally |
| Azure DDoS Protection | Protects Azure-hosted applications from distributed denial of service (DDOS) attacks |
| Azure Traffic Manager | Distributes network traffic across Azure regions worldwide |
| Azure ExpressRoute | Connects to Azure over high-bandwidth dedicated secure connections |
| Azure Network Watcher | Monitors and diagnoses network issues using scenario-based analysis |
| Azure Firewall | Implements high-security, high-availability firewall with unlimited scalability |
| Azure Virtual WAN | Creates a unified wide area network (WAN), connecting local and remote sites |
| | |

| Network Services | Description |
| --- | --- |
| Azure region: | geographic location. East US, West US, and North Europe are examples of region |
| Virtual network: | a logically isolated network on Azure |
| Network security group: | A network security group, or NSG, allows or denies inbound network traffic to your Azure resources. Think of a network security group as a cloud-level firewall for your network |
| Azure Load Balancer: | Azure Load Balancer is a load balancer service that Microsoft provides that helps take care of the maintenance for you. Load Balancer supports inbound and outbound scenarios, provides low latency and high throughput, and scales up to millions of flows for all Transmission Control Protocol (TCP) and User Datagram Protocol (UDP) applications |
| Azure Application Gateway: | If all your traffic is HTTP, a potentially better option is to use Azure Application Gateway. Application Gateway is a load balancer designed for web applications. It uses Azure Load Balancer at the transport level (TCP) and applies sophisticated URL-based routing rules to support several advanced scenarios. |
| Content Delivery Network: | A content delivery network (CDN) is a distributed network of servers that can efficiently deliver web content to users. It is a way to get content to users in their local region to minimize latency. CDN can be hosted in Azure or any other location. You can cache content at strategically placed physical nodes across the world and provide better performance to end users. Typical usage scenarios include web applications containing multimedia content, a product launch event in a particular region, or any event where you expect a high-bandwidth requirement in a region. |

### Storage

| Storage Service | Description |
| --- | --- |
| Azure Blob storage | Storage service for very large objects, such as video files or bitmaps |
| Azure File storage | File shares that you can access and manage like a file server |
| Azure Queue storage | A data store for queuing and reliably delivering messages between applications |
| Azure Table storage | A NoSQL store that hosts unstructured data independent of any schema |

#### SQL, NoSQL, Blob

| DB Services | Description |
| --- | --- |
| Azure SQL Database | a relational database as a service (DaaS) based on the latest stable version of the Microsoft SQL Server database engine |
| Azure Cosmos DB | globally distributed database service. It supports schema-less data |
| Azure Blob Storage | unstructured, meaning that there are no restrictions on the kinds of data it can hold |
| Azure Data Lake Storage Gen2 | The Data Lake feature allows you to perform analytics on your data usage and prepare reports. Data Lake is a large repository that stores both structured and unstructured data |
| Azure Files | fully managed file shares in the cloud that are accessible via the industry standard Server Message Block (SMB) protocol |
| Azure Queue storage | is a service for storing large numbers of messages that can be accessed from anywhere in the world |
| Disk storage | provides disks for virtual machines, applications, and other services to access |

#### Storage tiers

| Storage Services | Description |
| --- | --- |
| Hot storage tier: | optimized for storing data that is accessed frequently. |
| Cool storage tier: | optimized for data that is infrequently accessed and stored for at least 30 days. |
| Archive storage tier: | for data that is rarely accessed and stored for at least 180 days with flexible latency requirements. |

#### Storage Encryption

- Azure Storage Service Encryption (SSE) to meet the organization's security and regulatory compliance
- Client-side encryption is where the data is already encrypted by the client libraries.
- Replication for storage availability A replication type is set up when you create a storage account. The replication feature ensures that your data is durable and always available

### Databases

| Database Service | Description |
| --- | --- |
| Azure Cosmos DB | Globally distributed database that supports NoSQL options |
| Azure SQL Database | Fully managed relational database with auto-scale, integral intelligence, and robust security |
| Azure Database for MySQL | Fully managed and scalable MySQL relational database with high availability and security |
| Azure Database for PostgreSQL | Fully managed and scalable PostgreSQL relational database with high availability and security |
| SQL Server on VMs | Host enterprise SQL Server apps in the cloud |
| Azure SQL Data Warehouse | Fully managed data warehouse with integral security at every level of scale at no extra cost |
| Azure Database Migration Service | Migrates your databases to the cloud with no application code changes |
| Azure Cache for Redis | Caches frequently used and static data to reduce data and application latency |
| Azure Database for MariaDB | Fully managed and scalable MariaDB relational database with high availability and security |

### Web

| Web Services | Description |
| --- | --- |
| Azure App Service | Quickly create powerful cloud web-based apps |
| Azure Notification Hubs | Send push notifications to any platform from any back end |
| Azure API Management | Publish APIs to developers, partners, and employees securely and at scale |
| Azure Search | Fully managed search as a service |
| Web Apps feature of Azure App Service | Create and deploy mission-critical web apps at scale |
| Azure SignalR Service | Add real-time web functionalities easily |

### Internet of Things

| IoT Services | Description |
| --- | --- |
| IoT Central | Fully-managed global IoT software as a service (SaaS) solution that makes it easy to connect, monitor, and manage your IoT assets at scale |
| Azure IoT Hub | Messaging hub that provides secure communications and monitoring between millions of IoT devices |
| IoT Edge | Push your data analysis onto your IoT devices instead of in the cloud allowing them to react more quickly to state changes |

### Big Data

| Big Data Services | Description |
| --- | --- |
| Azure SQL Data Warehouse | Run analytics at a massive scale using a cloud-based Enterprise Data Warehouse (EDW) that leverages massive parallel processing (MPP) to run complex queries quickly across petabytes of data |
| Azure HDInsight | Process massive amounts of data with managed clusters of Hadoop clusters in the cloud |
| Azure Databricks (preview) | Collaborative Apache Spark–based analytics service that can be integrated with other Big Data services in Azure |

### Artificial Intelligence

| AI Services | Description |
| --- | --- |
| Azure Machine Learning Service | Cloud-based environment you can use to develop, train, test, deploy, manage, and track machine learning models. It can auto-generate a model and auto-tune it for you. It will let you start training on your local machine, and then scale out to the cloud |
| Azure Machine Learning Studio | Collaborative, drag-and-drop visual workspace where you can build, test, and deploy machine learning solutions using pre-built machine learning algorithms and data-handling modules |

### Cognitive Service

| CoG Services | Description |
| --- | --- |
| Vision | Image-processing algorithms to smartly identify, caption, index, and moderate your pictures and videos |
| Speech | Convert spoken audio into text, use voice for verification, or add speaker recognition to your app |
| Knowledge mapping | Map complex information and data in order to solve tasks such as intelligent recommendations and semantic search |
| Bing Search | Add Bing Search APIs to your apps and harness the ability to comb billions of webpages, images, videos, and news with a single API call |
| Natural Language processing | Allow your apps to process natural language with pre-built scripts, evaluate sentiment and learn how to recognize what users want |

### DevOps

| DevOps Services | Description |
| --- | --- |
| Azure DevOps | Azure DevOps Services (formerly known as Visual Studio Team Services, or VSTS), provides development collaboration tools including high-performance pipelines, free private Git repositories, configurable Kanban boards, and extensive automated and cloud-based load testing |
| Azure DevTest Labs | Quickly create on-demand Windows and Linux environments you can use to test or demo your applications directly from your deployment pipelines |

## Azure account services

### Azure Management group

Manages subscriptions, resources ..

*An Azure free subscription includes a $200 credit to spend on any service for the first 30 days, free access to the most popular Azure products for 12 months, and access to more than 25 products that are always free. This is an excellent way for new users to get started. To set up a free subscription, you need a phone number, a credit card, and a Microsoft account.*

- A Pay-As-You-Go (PAYG) subscription charges you monthly for the services you used in that billing period.

- An Enterprise Agreement provides flexibility to buy cloud services and software licenses under one agreement

- An Azure for Students subscription includes $100 in Azure credits to be used within the first 12 months plus select free services without requiring a credit card at sign-up

- You can create multiple subscriptions under a single Azure account. This is particularly useful for businesses because access control and billing occur at the subscription level, not the account level.

- One bill is generated for every Azure subscription on a monthly basis

### Authentication with Azure Active Directory

- Azure AD is a modern identity provider that supports multiple authentication protocols to secure applications and services in the cloud.
- Azure AD is all about web-based authentication standards such as OpenID and OAuth.

### Pricing for VMs - Pay as you go

| VM Type | Hardware Specs | Pricing | info |
| --- | --- | --- | --- |
| Burstable VMs: B1S | B1S1 vCPU1 GiB RAM | $0.068/hour | normally don't use a lot of CPU, burst to handle higher workloads. Free for 12 months |
| Compute optimized: Fsv2 | F2s v22 vCPU4 GiB RAM | $0.145/hour | Fsv2 is our newest compute-optimized VM family and uses the Intel Skylake processor |
| General purpose: Dv3 | D2 v32 vCPU8 GiB RAM | $0.156/hour | general purpose VMs. It's appropriate for a variety of workloads |
| Memory optimized: Ev3 | E2 v32 vCPU16 GiB RAM | $0.186/hour | High memory-to-core ratio memory-optimized VM. Relational database servers, caches, in-memory analytics |

### Pricing for VMs - 1yr reservation

| VM Type | Pricing |
| --- | --- |
| Burstable VMs: B1S | $0.067/hour |
| Compute optimized: Fsv2 | $0.11/hour |
| General purpose: Dv3 | $0.115/hour |
| Memory optimized: Ev3 | $0.136/hour |

### Pricing for VMs - 3yr reservation

| VM Type | Pricing |
| --- | --- |
| Burstable VMs: B1S | $0.064/hour |
| Compute optimized: Fsv2 | $0.091/hour |
| General purpose: Dv3 | $0.097/hour |
| Memory optimized: Ev3 | $0.109/hour |

*Focus a bit extra on non technical questions like - pricing, support, SLA, subscription,cost management, pricing calculator, advisor (including cloudyn)*

>Hey folks! @Mike G. just told me that there is a discount code for the Whizlabs practice test.  Use azure50, and you will get a 50% discount for the paid practice test.  Many of your peers have reported that this test was extremely helpful in their exam prep.

- https://www.whizlabs.com/microsoft-azure-certification-az-900/free-test/
- https://docs.microsoft.com/en-us/learn/paths/azure-fundamentals/
- https://www.microsoft.com/en-us/learning/exam-AZ-900.aspx

### App Service costs

You pay for the Azure compute resources your app uses while it processes requests based on the App Service Plan you choose. The App Service plan determines how much hardware is devoted to your host - for example, whether it's dedicated or shared hardware, and how much memory is reserved for it. There is even a free tier you can use to host small, low-traffic sites.

### Web Apps

App Service includes full support for hosting web apps using ASP.NET, ASP.NET Core, Java, Ruby, Node.js, PHP, or Python. You can choose either Windows or Linux as the host operating system.

### API Apps

Much like hosting a website, you can build REST-based Web APIs using your choice of language and framework. You get full Swagger support, and the ability to package and publish your API in the Azure Marketplace

### Web Jobs

WebJobs allows you to run a program (.exe, Java, PHP, Python or Node.js) or script (.cmd, .bat, PowerShell, or Bash) in the same context as a web app, API app, or mobile app

### Mobile Apps

Use the Mobile Apps feature of Azure App Service to quickly build a back-end for iOS and Android apps. With just a few clicks in the Azure portal you can:

- Store mobile app data in a cloud-based SQL database
- Authenticate customers against common social providers such as MSA, Google, Twitter and Facebook
- Send push notifications
- Execute custom back-end logic in C# or Node.js

On the mobile app side, there is SDK support for native iOS & Android, Xamarin, and React native apps.

## Serverless computing

Azure Functions which can execute code in almost any modern language.
Azure Logic Apps which are designed in a web-based designer and can execute logic triggered by Azure services without writing any code.

## Azure DNS

### Latency

| DNS Services | Description |
| --- | --- |
|Traffic Manager: | Traffic Manager uses the DNS server that's closest to the user to direct user traffic to a globally distributed endpoint |
| | |
| Azure Load Balancer: | distributes traffic within the same region to make your services more highly available and resilient. Traffic Manager works at the DNS level, and directs the client to a preferred endpoint |

## Security

**Azure Security Center:**

- Free. Available as part of your Azure subscription, this tier is limited to assessments and recommendations of Azure resources only.
- Standard. This tier provides a full suite of security-related services including continuous monitoring, threat detection, just-in-time access control for ports, and more.
- After the 60-day trial period is over, Azure Security Center is $15 per node per month

**Azure Active Directory Identity Protection:**

- Authentication. This includes verifying identity to access applications and resources, and providing functionality such as self-service password reset, multi-factor authentication (MFA), a custom banned password list, and smart lockout services.
- Single-Sign-On (SSO). SSO enables users to remember only one ID and one password to access multiple applications. A single identity is tied to a user, simplifying the security model. As users change roles or leave an organization, access modifications are tied to that identity, greatly reducing the effort needed to change or disable accounts.
- Application management. You can manage your cloud and on-premises apps using Azure AD Application Proxy, SSO, the My apps portal (also referred to as Access panel), and SaaS apps.
- Business to business (B2B) identity services. Manage your guest users and external partners while maintaining control over your own corporate data Business-to-Customer (B2C) identity services. Customize and control how users sign up, sign in, and manage their profiles when using your apps with services.
- Device Management. Manage how your cloud or on-premises devices access your corporate data.

**Azure Advanced Threat protection:**

- Azure Advanced Threat Protection (ATP) is a cloud-based security solution that leverages your on-premises Active Directory signals to identify, detect, and investigate advanced threats, compromised identities, and malicious insider actions directed at your organization. Azure ATP enables SecOp analysts and security professionals struggling to detect advanced attacks in hybrid environments to:
- Monitor users, entity behavior, and activities with learning-based analytics
Protect user identities and credentials stored in Active Directory
Identify and investigate suspicious user activities and advanced attacks throughout the kill chain
- Provide clear incident information on a simple timeline for fast triage

### Encryption

- Symmetric encryption uses the same key to encrypt and decrypt the data
- Asymmetric encryption uses a public key and private key pair.
- Encryption of data at rest ensures that the stored data is unreadable without the keys and secrets needed to decrypt it
- Encrypting data in transit protects the data from outside observers and provides a mechanism to transmit data while limiting risk of exposure.

#### Types of Encryption

|  Encryption Types | Description |
| --- | --- |
| Encrypt raw storage: | Azure Storage Service Encryption for data at rest helps you protect your data to meet your organizational security and compliance commitments |
| Encrypt Virtual machine disks: | Azure Disk Encryption is a capability that helps you encrypt your Windows and Linux IaaS virtual machine disks |
| Encrypt databases: | Transparent data encryption (TDE) helps protect Azure SQL Database and Azure Data Warehouse against the threat of malicious activity |
| Encrypt secrets: | Azure Key Vault to protect our secrets. |
| | |

#### Firewalls

- Azure Firewall is a managed, cloud-based, network security service that protects your Azure Virtual Network resources
- Azure Application Gateway is a load balancer that includes a Web Application Firewall (WAF) that provides protection from common, known vulnerabilities in websites
- Network virtual appliances (NVAs) are ideal options for non-HTTP services or advanced configurations, and are similar to hardware firewall appliances.

*Microsoft Azure Information Protection (MSIP or sometimes referred to as AIP) # is a cloud-based solution that helps organizations classify and optionally protect documents and emails by applying labels.*

## Azure Policy

**Azure Policy: Azure Policy is a service you can use to create, assign, and manage policies. These policies apply and enforce rules that your resources need to follow.**

| Azure Policies | Description |
| --- | --- |
| Azure Policy | is a service in Azure that you use to define, assign, and, manage standards for resources in your environment. It can prevent the creation of disallowed resources, ensure new resources have specific settings applied, and run evaluations of your existing resources to scan for non-compliance.|
| Policy definition: | expresses what to evaluate and what action to take. For example, you could ensure all public websites are secured with HTTPS, prevent a particular storage type from being created, or force a specific version of SQL Server to be used. |
| Initiatives: | Initiatives work alongside policies in Azure Policy. An initiative definition is a set or group of policy definitions to help track your compliance state for a larger goal. Even if you have a single policy, we recommend using initiatives if you anticipate increasing the number of policies over time. |
| Enterprise governance management | Access management occurs at the Azure subscription level. This allows an organization to configure each division of the company in a specific fashion based on their responsibilities and requirements |
| Azure Blueprints | allows you to define a repeatable set of Azure resources that implement and adhere to your organization's standards, patterns, and requirements |
| Compliance Manager | is a workflow-based risk assessment dashboard within the Trust Portal that enables you to track, assign, and verify your organization's regulatory compliance activities related to Microsoft professional services and Microsoft cloud services such as Office 365, Dynamics 365, and Azure. |
| Microsoft Privacy Statement: | The Microsoft privacy statement explains what personal data Microsoft processes, how Microsoft processes it, and for what purposes. |
| Microsoft Trust Center: | Trust Center is a website resource containing information and details about how Microsoft implements and supports security, privacy, compliance, and transparency in all Microsoft cloud products and services |
| Service Trust Portal (STP): | hosts the Compliance Manager service, and is the Microsoft public site for publishing audit reports and other compliance-related information relevant to Microsoft’s cloud services |
| Azure Monitor: | Azure Monitor maximizes the availability and performance of your applications by delivering a comprehensive solution for collecting, analyzing, and acting on telemetry from your cloud and on-premises environments. |
| Azure Service Health: | Azure Service Health is a suite of experiences that provide personalized guidance and support when issues with Azure services affect you. It can notify you, help you understand the impact of issues, and keep you updated as the issue is resolved. Azure Service Health can also help you prepare for planned maintenance and changes that could affect the availability of your resources. |

>**Resource Health can view the Virtual Machine blade**

## Azure Resource Manager

**Resource groups: A resource group is a logical container for resources deployed on Azure.**

- Logical grouping is the aspect that we're most interested in here, since there's a lot of disorder among our resources.
- If you delete a resource group, all resources contained within are also deleted. Organizing resources by life cycle can be useful in non-production environments
- Resource groups are also a scope for applying role-based access control (RBAC) permissions
- Azure portal
- Azure PowerShell
- Azure CLI
- Templates
- Azure SDKs (like .NET, Java)
- A resource can have up to 15 tags. The name is limited to 512 characters for all types of resources except storage accounts, which have a limit of 128 characters

>**role-based access control (RBAC): RBAC provides fine-grained access management for Azure resources, enabling you to grant users the specific rights they need to perform their jobs. RBAC is considered a core service and is included with all subscription levels at no cost**

- Segregate duties within your team and grant only the amount of access to users that they need to perform their jobs. Instead of giving everybody unrestricted permissions in your Azure subscription or resources, allow only specific actions at a particular scope.
- When planning your access control strategy, grant users the lowest privilege level that they need to do their work.
- Use Resource Locks to ensure critical resources aren't modified or deleted (more on that next!)

>**resource locks: Resource locks are a setting that can be applied to any resource to block modification or deletion. Resource locks can set to either Delete or Read-only**

## Predict costs and optimize spending

| Billing Services | Description |
| --- | --- |
| Enterprise | Enterprise customers sign an Enterprise Agreement with Azure that commits them to spend a negotiated amount on Azure services, which they typically pay annually. Enterprise customers also have access to customized Azure pricing. |
| Web direct | Direct Web customers pay general public prices for Azure resources, and their monthly billing and payments occur through the Azure website. |
| Cloud Solution Provider | Cloud Solution Provider (CSP) typically are Microsoft partner companies that a customer hires to build solutions on top of Azure. Payment and billing for Azure usage occur through the customer's CSP. |
| Usage Meters: | When you provision an Azure resource, Azure creates one or more meter instances for that resource. The meters track the resources' usage, and generate a usage record that is used to calculate your bill. |
| Resource type: | Each meter tracks a particular kind of usage. For example, a meter might track bandwidth usage (ingress or egress network traffic in bits-per-second), the number of operations, size (storage capacity in bytes), or similar items. |
| Services: | The Azure team develops and offers first-party products and services, while products and services from third-party vendors are available in the Azure Marketplace . Different billing structures apply to each of these categories. |
| Azure billing zones: | Most of the time inbound data transfers (data going into Azure datacenters) are free. For outbound data transfers (data going out of Azure datacenters), the data transfer pricing is based on Billing Zones. |

| Zone | Areas |
| --- | --- |
| Zone 1 | United States, Europe, Canada, UK, France |
| Zone 2 | Asia Pacific, Japan, Australia, India, Korea |
| Zone 3 | Brazil |
| DE Zone 1 | Germany |

>**In most zones, the first outbound 5 GB per month is free. After that, you are billed a fixed price per GB.**

________________
**Azure pricing calculator:** The Azure pricing calculator is a free web-based tool that allows you to input Azure services and modify properties and options of the services. It outputs the costs per service and total cost for the full estimate.

| Calculator items | Description |
| --- | --- |
| Region | Lists the regions from which you can provision a product. Southeast Asia, central Canada, the western United States, and Northern Europe are among the possible regions available for some resources. |
| Tier | Sets the type of tier you wish to allocate to a selected resource, such as Free Tier, Basic Tier, etc. |
| Billing Options | Highlights the billing options available to different types of customer and subscriptions for a chosen product. |
| Support Options | Allows you to pick from included or paid support pricing options for a selected product. |
| Programs and Offers | Allows you to choose from available price offerings according to your customer or subscription type. |
| Azure Dev/Test Pricing | Lists the available development and test prices for a product. Dev/Test pricing applies only when you run resources within an Azure subscription that is based on a Dev/Test offer. |
| Products | This tab is where you'll do most of your activity. This tab has all the Azure services listed and is where you'll add or remove services to put together your estimate. |
| Estimates: | This tab has all of your previously saved estimates. We'll go through this process in a moment. |
| FAQ: | Just as it says, this tab has answers to some frequently asked questions. |

| Billing Tools | Description |
| --- | --- |
| Azure Advisor: | is a free service built into Azure that provides recommendations on high availability, security, performance, and cost. Advisor analyzes your deployed services and looks for ways to improve your environment across those four areas Reduce costs by eliminating unprovisioned Azure ExpressRoute circuits Buy reserved instances to save money over pay-as-you-go. Right-size or shutdown underutilized virtual machines |
| Azure Cost Management: |  Azure Cost Management is another free, built-in Azure tool that can be used to gain greater insights into where your cloud money is going. You can see historical breakdowns of what services you are spending your money on and how it is tracking against budgets that you have set. You can set budgets, schedule reports, and analyze your cost areas. |
| Cloudyn: | Cloudyn, a Microsoft subsidiary, allows you to track cloud usage and expenditures for your Azure resources and other cloud providers including Amazon Web Services and Google. Easy-to-understand dashboard reports help with cost allocation and chargebacks |
| Azure TCO calculator | If you are starting to migrate to the cloud, a useful tool you can use to predict your cost savings is the Total Cost of Ownership (TCO) calculator |

### Azure credits

- Spending limits:
- Use reserved instances
- low-cost locations and regions
- cost-saving offers
- right-size underutilized virtual machines
- deallocate virtual machines in off hours
- delete unused virt mach
- migrate to PaaS or SaaS services

### Licensing costs

#### Azure Hybrid Benefit for Windows Server

*To be eligible for this benefit, your Windows licenses must be covered by Software Assurance. The following guidelines will also apply:*

Each two-processor: *license or each set of 16-core licenses is entitled to two instances of up to 8 cores or one instance of up to 16 cores.*

Standard Edition: *licenses can only be used once either on-premises or in Azure. That means you can't use the same license for an Azure VM and a local computer.*

Datacenter Edition: *benefits allow for simultaneous usage both on-premises and in Azure so that the license will cover two running Windows machines.*

Azure Hybrid Benefit for SQL Server: *Azure Hybrid Benefit for SQL Server is an Azure-based benefit that enables you to use your SQL Server licenses with active Software Assurance to pay a reduced rate.*

Standard Edition per core licenses with active Software Assurance: *you can get one vCore in the General Purpose service tier for every one license core you own on-premises.*

Enterprise Edition per core licenses with active Software Assurance: *you can get one vCore in the Business Critical service tier for every one license core you own on-premises. Note that the Azure Hybrid Benefit for SQL Server for the Business Critical service tier is available only to customers who have Enterprise Edition licenses.*

highly virtualized Enterprise Edition per core licenses with active Software Assurance: *you can get four vCores in the General Purpose service tier for every one license core you own on-premises. This is a unique virtualization benefit available only on Azure SQL Database.*
