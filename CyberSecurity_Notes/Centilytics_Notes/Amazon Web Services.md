Link : https://aws.amazon.com/what-is-cloud-computing/

### Services in Cloud Computing
1. **Iaas - Infrastructure as a Service** : Access to networking features, computers and data storage spaces.
2. **PaaS - Platform as a Service** : Removes the need to manage infrastructure (hardware and OS). Focuses on Deployment and Management of Apps. 
3. **SaaS - Software as a Service** : referred to as the end-user applications provided to user like Web-based Emails.

### Uses of Cloud Services
- Resizable Compute Capacity
- Databases and Data Storage
- Ai/ML
- Networking & Content Delivery
- Security, Identity and Compliance
- Migration and Modernization

### AWS Cloud Services
1. **Amazon Elastic Compute Cloud (Amazon EC2)** - 
	- Things I can do over them - 
		1. Run cloud native and enterprise applications
		2. Scale for HPC applications
		3. Develop for Apple Platforms
		4. Train and deploy ML Applications
	- I'll get computing instance. 
	- I can choose the Operating Systems and Software I want on the Instance / VM. 
	- Software can be selected from AWS Marketplace on EC2 Instance. 
	- Uses Elastic Fabric Adapter - is a network interface that enables customers to run applications requiring high levels of inter-instance communications, like ML, computational fluid dynamics, weather modelling and reservoir simulation.  
	- Elastic IP Addresses are static IP Addresses designed for dynamic cloud computing.
	- AWS PrivateLink is a purpose built technology designed for customers to access Amazon services.

2. **AWS Lambda** - 
	- is a compute services that runs your code in response to events and automatically manages the compute resources , fastest way to to create serverless applications.
	- Doesn't require you to manage infrastructure.
	- Write the code and upload inn .zip file or container image.
	- We can run interactive web and mobile backends on Lambda.
	- Amazon Elastic File System (EFS) handles infrastructure management and provisioning to simply scaling.
	- Events may include changes in state or an update, such as user placinng an item in a shopping cart or e-commerce website.

3. **Amazon Elastic File System (Amazon EFS)**  - 
	 - EFS automatically grows and shrinks as you add and remove files with no need for management or provisioning.
	 - ![[Pasted image 20250205112726.png]]

4. **Amazon S3 Glacier Storage Classes** - 
	- are built for data archiving, providing you with highest performance, most retrieval flexibility, and lowest archive storage in cloud.
	- provides virtually unlimited scalability and are designed for 11 nines (999.9999999999%) of data durability.
	- For instant retrieval use S3 Glacier Instant Retrieval Storage Class
	- S3 Glacier Flexible Retrieval - to retrieve large sets of data at no cost
	- S3 Glacier Deep Archive - for long-lived archive storages

5. **Amazon Simple Storage Service (Amazon S3)** - 
	- object storage service
	- fully elastic i.e. automatically growing or shrinking as we add or remove data.
	- provides 11 nines data durability.
	- provides 4 nines availability by default.
	- S3 is secure, private, and encrypted by default and numerous auditing capabilities to monitor access requests to your S3 resources.
	- ![[Pasted image 20250205120214.png]]

6. **Amazon Relation Database Service ( Amazon RDS)** - 
	- is an easy-to-manage relational database service optimized.
	- automated database management tasks such as provisioning, configuring, backing up and patching.
	- We're given the choice of engines to deploy and scale the RD Engines.
	- Achieves high availability with Amazon RDS Multi-AZ Deployments.
	- Offered with DB Software like PostgreSQL, MySQL, SQL Server, Oracle and Db2.
	- **Aurora** - provides unparalleled high performance and availability at global scale with full MYSQL and PostgreSQL compatibility.

7. **Amazon API Gateway** - 
	- is a fully managed service that makes it easy for developers to create, publish, maintain, monitor and secure APIs at any scale
	- We can create RESTful APIs and WebSocket APIs that enable real-time 2 way communication applications.
	- handles all tasks involved in accepting and processing up to hundreds of thousands of concurrent API calls, including traffic management, CORS support, authorization and access control, throttling, monitoring, and API version management. 
	- We can run multiple versions of same API simultaneously with API Gateway, allowing you to quickly iterate, test and release new versions. 
	- can throttle traffic and authorize API calls to ensure that backend operations withstand traffic spikes and backend systems are not unnecessarily called.

8. **Amazon CloudFront** - 
	- reduces latency by delivering data through 600+ globally dispersed Points of Presence (PoPs) with automated network mapping and intelligent routing.
	- improves security with traffic encryption, access controls, Virtual Private Cloud origins, and uses AWS Shield Standard to defend against DDoS attacks.
	- we can customize the code at AWS Content Delivery Network (CDN) edge using serverless compute features to balance cost, performance and security.

9.  **Elastic Load Balancing** - 
	- Distribute network traffic to improve application scalability.
	- secures applications with SSL/TLS termination, integrated certificate management and client certificates authentication.
	- automatically distributes incoming application traffic across multiple targets and virtual appliances in one or more Availability Zones (AZs).
	- 3 types of Load Balancers - Application Load Balancer, Network Load Balancer or Gateway Load Balancer
	- Listeners for Application Load Balancer - HTTP or HTTPs and for Network Load Balancer - TCP or UDP

10. **Amazon Athena** - 
	- get streamlined, near instant startup of SQL or Apache Spark analytics workloads with a serverless experience
	- we can use ML models in SQL Queries or Python to simplify complex tasks like anomaly detection, customer cohort analysis and sales predictions.

11. **Amazon EMR** - easily run and scale Apache Spark, Hive, Presto and other big data workloads.

12. **Amazon Cognito**
	- implement a secure, scalable and customized sign-up and sign-in experience in minutes.
	- it's developer centric, cost-effective service that provides secure, tenant - based identity stores and federation options
	- secure and scalable Customer Identity and Access Management (CIAM)

13. **Amazon Detective**
	- Analyze and visualize security data to investigate potential security issues
	- automatically collects log data from your AWS resources and uses Machine Learning (ML), Statistical Analysis and Graph Theory to build a dataset that can be used to conduct more efficient security investigations.

14. **Amazon GuardDuty** - Protect your AWS accounts, workloads and data with intelligent threat detection.
15. **AWS WAF** - 
	- Protect your web apps from common exploits.
	- can create security rules that control bot traffic and block common attac patterns such as SQL Injection or Cross-Site Scripting (XSS).
	- can filter web requests based on conditions such as IP Addresses, HTTP Headers, body or  custom URLs.
	- monitors your applications for unauthorized access to user accounts using compromised credentials.

16. **AWS Shield** - 
	- maximizes application availability and responsiveness with managed DDoS protection
	- DDoS Attacks are common at Network Layer (Layer 3), Transport Layer (Layer 4), Presentation Layer (Layer 6), & Application Layer (Layer 7).
	- protects applications and APIs from SYN floods, UDP floods and other reflection attacks.
	- deploys mitigations like packet filtering and priority based traffic shaping to stop basic network-layer attacks.

17. **AWS Network Firewall** - 
	- deploys network firewall security across your VPCs.
	- we can create firewall rules that provides fine-grained control over network traffic and easily deploy firewall security across your VPCs.
	- Inspect Inbound Internet Traffic
	- Filter Outbound Traffic
	- Prevent Inbound Internet Traffic Intrusion
	- Secure AWS Direct Connect and VON Traffic