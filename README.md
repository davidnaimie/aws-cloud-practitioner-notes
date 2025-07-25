# aws-cloud-practitioner-notes
Notes and key concepts from my AWS Cloud Practitioner study journey
# AWS Cloud Practitioner Notes

📘 This repo contains my personal notes and summaries as I study for the AWS Certified Cloud Practitioner exam.

---

## 🔐 IAM (Identity and Access Management)
- IAM is global (not region-specific)
- Allows managing users, groups, and permissions
- Principle of Least Privilege = best practice
- + SHARED RESONSIBILITY 
---

## ☁️ Core Services
### EC2
- Elastic Compute Cloud = virtual servers
- Security groups
- firewall attached to EC2 instance 
- You choose instance type, OS, region
- ON-demand, spot, Reserved (standard + Convertable) dedecated host, dedected instance
- + SHARED RESONSIBILITY

## Amazon FSx for Lustre
- A fully managed high performance, scalable file storage for High performance computing (HPC)
- The name Lustre is derived from 'Lenux' and 'Cluster'
- Machine learning. analytics, video processing, finacial modeling
- scale up to 100's GB/s, millions of IOP's

## FSx for Windows file server
- Fully managed, highly reliable, and scalable windows native shared file system
- Built for windows file server
- suports SMB protocol and windows NTFS
- intagrated with Microsoft Active Directory
- Can be accessed from AWS or your on premis infrastructure 

## Why Use a Load Balancer
- Spreads load across multiple downstream inastances
- expose a single point of access (DNS) to your application
- seamlessly handle failures of downsteam instances
- Does regular health checks on your instances
- You can use across AZones
- Provide SSL termination (HTTP) for your wesites
  ## ELB & ASG Summery
  - High Availability means you have your application across multiple AZ
  - vertical scaling is increasing the size of the instance
  - Horizontal scaling is increasing the number of instances
  - ELasticity is the ability to scale up and down based on the demand
  - Agility is ablity to work faster to deleate and make rescourses very fast
    
## ELB's (Elastic Load Balancing)
- Its a managed load balancer
- AWS guartees it works, upgrades, maintenance, hight availabilty , provides a few config knobs
- setting up your own is cheaper but not worth it for the effort you will need to do on your side
- # 4 Types of LB (Load Balancer)
  - Application  LB (HTTP/ HTTPS ONLY) - Layer 7
  - Networ LB (UNTRA HIGH PERFORMANCE, ALLOWS FOR TCP) - LAYER 4 _ can handle millions of request per second
  - Gateway LB - Layer 3
  - Classic is no longer used
 
  # Auto Scaling groups (ASG)
  - Implament Elasticity for your application, across multiple AZ
  - Scale EC2 instances Based On The Demand, replace unhealthy
  - Integrated with the ELB
 
  # ASG stratigies include
  - Manual scaling
  - Dynamic Scaling
  - (simple/step Scaling, Targwet tracking scaling, Scedule scaling)
  - Predictibve scaling


### S3
- Simple Storage Service = object storage
- Highly durable and scalable
- Disaster and recovery
- Archive
- Hybrid Cloud storage
- Application hosting
- Media Hosting
- DAta lakes and big date analytics
- Software delivery
- static website
# Bucket > Object > Key (S3 Buckets need to be unique and are created at a regional level)
    - NO UPPERCASE
    - 3-63 characters
    - Not an IP
    - Must start with lowercase letter or number
    - must not start with prefix xn--
    - Must not end with the suffix -s3alias
- Objects (files) >
    - Max object size is 5TB
    - if uploading more than 5GB must use multi-part upload
    - Matadata ( list of text key / value pair - up to 10) - useful for security lifecycle
    - Version ID (if versioning is enabled) 
- Key is the full path of the file:
    - s3://my=bucket/my_file.txt
    - s3://my-bucket/my_folder1/another_folder/my_my_file.txt
- The KEY is composed of the prefix + object name
- No concept of directories with Buckets just keys with really long names  
# Amazon s3 - Security
- User-Based
    - IAM Policies- which user API calls should be allowed for a soecific user from IAM
- Resource-Based
    - Bucket Policies - bucket wide rules from the s3 console - allows cross account
      + JSON based policeis
    - Object access COntrol List (ACL) - finer grain (can be disabled)
    - Bucket access Control List (ACL) - less common
- Note: an IAM principle can access a s3 if..
      - the user IAM permissions ALLOW it OR the resource policy ALLOWS it
      - AND thes no exsplicit DENY
- Encryption: encrypt objects in Amazon s3 using encryption keys
# S3 - Static website
- S3 can host static webites and have them accessible on the internet
- The websote URL will depend on the region
      They look very similar example(website-aws-region  or  wesite.aws-region)
- If you get a 403 Forbidden error; make sure the bucket polict allows public reads
# S3 - Versioning
- You can version youjr files ini Amazon S3
- It is enabled at the bucket level
- Its best to practice to version your buckets
    - protectds against unintended deletes(ablwe to restore)
    - easy to roll back to [revios version
- Notes:
    - Any file that is not versioned prior to enabling versioning will have version "null"
    - Suspending versioning does not delete the previous versions
 
# S3 - Replication (CRR & SRR)
    cross region replication and Same region replication
    - Must enable Versioning in source and destination buckets
    - Buckets can be in differnt AWS accounts
    - Copying is asynchronous
    - Must give proper permissions to S3

- Use cases:
      - CRR - compliance, lower latecyaccess, replication across accounts
      - SRR - log aggregation, live replication between production and test accounts
  ## S3-Storage Classes
  - Can move between classes manually or using S# Lifecycle configurations.
  # Standard-general purpose= 99.99% Availability
- Frequently used data-Low latency and high throughput-Sustains 2 concurrent facility failures
- Use cases: Big Data analytics, mobile & gmaing apps, content distribution
  # Infrequent Access:
  - For data that is lessfrequently but requires rapid access whe needed with lower cost
  # Standard-infrequent access (IA)= 99.99% Availability
- use cases are Disaster Recovery;backups
  # OneZone-infrequent access= 99.5% Availability
- High durability 99.999999% in a single AZ, data lost when AZ is destroyed
- Storing seconmdary back-up copies of on-premise data, or data yopu can recreate
# Glacier Storage Classes
- Low-cost object storage meant for archiving/backup
- price for storage and object retrieval cost
  # Glacier Instant Retrieval
  - milisecond retrieval, great for data accessed once a quarter
  - minimum storage 90 days
  # Glacier Flexible Retrieval
  - Expedited (1-5 minutes), Standard(3-5 hours), Bulk(5-12 hours) free
  - min storage 90 days
  # Glacier Deep Archive
  - Standard (12hours) Bulk(48 hours)
  - min storage duration of 180 days
  # Intelligent Tiering
  - Small monthly monitoring and auto tiering fee
  - moves objects automatically between access tiers based on usage
  - there no retrieval charge for Intelligent tiering
# S3 Encryption
- server side encryption is always on by default '
- Client side Encryption is done by the user before it comes to the server
# S3 Access Analyzer
- Ensures that the permissions and people have the accesses that you set
- Evaluate S3 Buckets, S3 ACL's S3 Acccess Point Policies
- Powered by IAM Access Analyzer

# AWS Snow Family 
- helps with Edge computing and thats areas with not so good Internet
  - Pricing
    You pay for device usage and data transfer out of AWS
    Data transfer into AWS is free
    # ON-DEMAND
    15 days usage for the 210TB
    shipping days are not included ion the 15 days
    pay-per day any additional days
    # Committed-Upfront
    Pay in advanced for monthkly, 1 year, and 3-years of usage (Edge Computing)
    Up to 62% discounted pricing

    # DATABASE */   
# Amazon RDS Relatable Database service (RDS)-CANT SSH INTO YOUR INSTANCE
- RDS is a managed database
- Included in the free tier
# Amazon Aurora
- Is "AWS cloiud optimized" and claims 5x performance improvement over MYSQL on RDS, over 3x the performance of Postgres on RDS
- grows automatically of 10GB up to 128TB
- cost more than RDS (20%) but more efficient
- NOT INCLUDED in free tier
# Amazon Aurora SERVERLESS
- PAY PER SECOND
- Unpredictable workloads
- least mangment overhead
- No capacity planning
- Automated database instantiation and auto scaling based on actual usage
- PostSQL and MySQL are both supported

# ElastiCashe Overview
- Relational to Database like RDS
- is to get managed Redis or Memcached
- Cashes are in-memory databases with high performances, low latency
- Helps reduce load off database for read intensive workloads
- AWS takes care of all the OS maintnence/ patching optimizations, setups, configurations, monitoring, failure recovery and backups
    
# Dynamo DB
- Standard & Infrequent Access (IA)
- # DynamoDB - Global Tables
- Can set up to use in multiple Regions
# Redshift Overview
- Redshift is based on PostSQL, but its not used for OLTP = Online Transaction Proccessing
- It is OLAP = Online Analytical Proccessing (analytics and data warehousing)
- Its stored in columnar insteads of row based
- BI = Business Intellagence tool if youj want to create dashboards
  # Redshift Serverless now available
  - pay for only what you use
  - run analytic workloads
# EMR (Elastic MapReduce)
- Helps creating Hadoop cluster (Big Data) to analyse and process vast amount of data
- you can make a cluster of 100's of EC2 instances
- SUPPORTS Apache Spark, HBase, Presto, Fink
- Takes care of all provisions and config
  - Use cases: data processing, machine learning, web indexing, big data...
 
# Amazon Athena
- Serverless query service to - perform analytics against S# objects
- Uses standard SQL language to query the files
- Supports CSV,JSON,AVRO,and Parquet (built in Presto engine)

- - pricing $5 per TB of data
  - use compressed or columnar data for cost-savings (less scan)
 
  - Use cases best when you see: Buisness Intelligence BI/ analytics/ reporting, analyze & query VPC Flows Logs, ELB Logs, CLoudTrails, etc.. 
- Exam Tip: analyze data in S3 using serverless SQL, use Athena

# QuickSight- is the go-to tool for the "eye" in AWS
- Creates dashboards on my databases that visually represents the data and show the users the insights thier looking for
- cool graphs and charts
- embedded with per session pricing
- USE CASES:
  - business analytics
  - Building visualizations
  - perform ad-hoc analysis
  - Get business insights using data
- Integrated with RDS, Aurora, Athena, Redshift, S3

# DocumentDB

# Neptune (think graph databases)
- fully managed graph database
- a popular graph dataset would be a social network
  - users have friends
  - posts have comments
  - comments have likes from users
  - users share and like post
- highly availablew across 3 AZ, with up to 15 read replicas
- Build and run applications working with highly connected datasets- optimized for these complex and hard queries
- Great for knowlege graphs
# Timestream (think time series data)
- fully manged, fast, scalable, serverless time series database
- Automatically scales up/down to adjust capacity
- stores and analyzes trillions of events per day
- 1000,s time faster & 1/10th the cost of relational databases
- Built-in time series analytics functions (helps you identify patterns in your data in near real-time)
# Managed Blockchain
- Blockchain makes it possible to build applications where multiple parties can execute trsnsactions without the need for a trusted, central authority
- Its a managed service to :
  - Join public blockchain networks
  - Or create your own scalable private network
  - Compatible with the framework Hyperledger Fabric & Ethereum
# Glue
- Managed extract, transform, and (ETL) service
- fully serverless service
# DMS - Database Migration Service
- migrate databases to AWS,
- Supports:
  - Homogeneous: ex oracle to Oracle
  - Heterogenous migrations: ex Microsoft SQL Server to Aurora
  - 
# Databases & Analytics Summary in AWS
- Relational Databases- OLTP:RDS & Aurora (SQL)
- Differences between Multi-AZ, Read Replicas, Multi-Region
- In-memory Database: ElastiCache
- Key/Value Database: DynamoDB (serverless) & DAX (cache for DynamoDB)
- Warehouse - OLAP: Redshift (SQL)MR service
- Athena
- Hadoop CLuster: EMR service
- Athena: quere data on Amazon S3 (serverless & SQL)
- QuickSight: dashboards on your data (serverless)
- DocumentDB: think, "Aurora for MongoDB" (JSON- No SQL database)
- Amazon QLDB: central database for Finacial Transactions Ledger (immune journal, cryptographically verifiable)
- Amazon Managed Blockchain: de-centralized Managed Hyperledger Fabric & Ethereum blockchains
- Glue: Managed extract, transform, and (ETL) service  fully serverless service
- Database Migration: DMS
- Neptune: graph database
- Timestream: time-series database
  
# Docker
- Is a software developemnet platform to deploy apps
- Apps ar packaged into containers and can be run on any OS
- Apps run the same regaurdless of where the are run. NO capability issues, less work, easier to maintain and deploy, works with any language
- Scale containers up and down in seconds
# ECS Elastic Container Service
- Launches the docker containers on AWS
- You must provision and maintain the infrastructure
- AWS takes care of stopping and starting the containers
- HAs intergrations with the Application Load Balancer
# Fargate
- Also launches containers on AWS
- You dont provision the infrastructure (NO instances to manage) MOre Simpler
- Serverless
- AWS just runs containers for you based on the CPU/RAM you need
# ECR Elastic COntainer Service
- Private Docker Registry on AWS
- This is where you store Docker images so they can be run by ECS or Fargate
# EKS Elastic Kubernetes Service
- Is the service that allows you to launch Kubernetes clusters on AWS
- Its an open source system
- Its Cloud Agnostic (can be used on any cloud - Azure,GCP...

# AWS Lambda
- Virtual functions- no sservers to manage
- limited by time and short extentions
- Scaling is automated and it Runs - on - demand
  - # Lambda Benefits
  - pay per request and compute time
  - free tier of 1,000,000 Lambda request and 400k GBs of compute time
  - integrated with the whole AWS suite of services
  - Event-Driven: functions get invoked by AWS when needed
  - integrated with many program langauges: Node.js, Python, Java, c# (NET Core)/ PowerShell, Ruby, Custom Runtime API
  - Easy monitoring through Cloud Watch
  - Increasing RAM will improve CPU and network and its easy to get more resources per functions up to 10GB of RAM
  - Lambda Container Image : ECS / Fargate is preferred for running arbitrary Dockers images

- # Docker
- Is a software developemnet platform to deploy apps
- Apps ar packaged into containers and can be run on any OS
- Apps run the same regaurdless of where the are run. NO capability issues, less work, easier to maintain and deploy, works with any language
- Scale containers up and down in seconds
# ECS Elastic Container Service
- Launches the docker containers on AWS
- You must provision and maintain the infrastructure
- AWS takes care of stopping and starting the containers
- HAs intergrations with the Application Load Balancer
# Fargate
- Also launches containers on AWS
- You dont provision the infrastructure (NO instances to manage) MOre Simpler
- Serverless
- AWS just runs containers for you based on the CPU/RAM you need
# ECR Elastic COntainer Service
- Private Docker Registry on AWS
- This is where you store Docker images so they can be run by ECS or Fargate
# EKS Elastic Kubernetes Service
- Is the service that allows you to launch Kubernetes clusters on AWS
- Its an open source system
- Its Cloud Agnostic (can be used on any cloud - Azure,GCP...
# AWS Lambda
- Virtual functions- no sservers to manage
- limited by time and short extentions
- Scaling is automated and it Runs - on - demand
  - # Lambda Benefits
  - pay per request and compute time
  - free tier of 1,000,000 Lambda request and 400k GBs of compute time
  - integrated with the whole AWS suite of services
  - Event-Driven: functions get invoked by AWS when needed
  - integrated with many program langauges: Node.js, Python, Java, c# (NET Core)/ PowerShell, Ruby, Custom Runtime API
  - Easy monitoring through Cloud Watch
  - Increasing RAM will improve CPU and network and its easy to get more resources per functions up to 10GB of RAM
  - Lambda Container Image : ECS / Fargate is preferred for running arbitrary Dockers images

# API Gateway
- Use a REST API to API Gateway for the Client to have access to your Lamba or DynamoDB serverless And the API will Proxy the request
- Fully managed service for developers to easiely create, publish, maintain, monitor, and secure API,s
- serveless and scalable
- Supports RESTful APIs and Websockets APIs
- support for security, user authentuication, API throttling, API keys and monitoring...
# Batch
- Fully managed batch proccessing at any scale
- runs 100,000s of computing batch jobs on AWS
- A Batch job is a job with a start and a end
- provisions ther right amount of CPU and RAM
- Schedule the Batvh job and AWS does the rest
- THey are define as Docker images and run on ECS
- Helpful for cost optimazations and focusing less on the infrastructure

# Batrch VS Lambda
- # Lambda:
  - time limit
  - Limitied runtimes'
  - Limited temp disk space
  - Serverless
- # Batch:
- No time limit
- any runtime aslong as you package as a Docker image
- Rely on EBS / instance store for disc space
- Relies on EC2 ( Can be managewd by AWS)

# Amazon Lightsail
- For people with no or little cloud experience with low and predictable pricing
- simple web apps and it provides templates
- Dev test enviroment
- NO auto scaling and limited AWS configuring

## Other Compute - Summary
- Dockers: COntainer technology to run applications
- ECS: run Docker Containers on EC2 instances
- Farget: serverless, Run docker containers without provisioning and infrastructure (No EC2 instances)
- ECR: Private Docker Image repository
- Batch: Run Batvh jobs on AWS across EC2 instances (runs ontop of the ECS service)
- Lightsail: predictable and low pricing for simple app and DB stack
## Lambda Summary - serverless service, Fuction as a service, seamless scaling, reactive
- Lambda billing is by the run time * By the RAM provisions & by the nuimber of invocations
- Many Langauges except arbitrary Dockers
- Invocation time upto 15 minutes
- USE CASES:
  - Create Thumbnails for images uploaded into S3
  - Run a serverless Cron job
- API Gateway: expose Lambda function as a HTTP API

# What is CloudFormation
- Is a declarative way of outlining your AWS Infrastructure for any resources
- example with CloudFormation template:
  - I want a ssecurityu group
  - I want 2 EC2 instances
  - I want 3 S3 buckets
  - I want a Load Balancer ELB in front of these machines
- Then CLoudFormation creates those for you in the right order with exact config that you specify
  # Benefits of AWS CloudFormation 1/2
  - Infrastructure as code, repeat a architecture in differnt Regions, differnt AWS accounts or enviroments
    - No resources are manually created
    - changes to the infrastructure are reviewed through code
  # COST
    - Each resources within the stack is tagged with an identifier so you can easily see kow much the stack cost you
    - estamate the cost using the template
    - Savings strategy: In Dev, you could automation deletion of templates at 5pm and recreate at 8am safely
  # Benefits 2/2
  - Productivity
    - Ability to destroy and re-create infrastructure on the fly
    - Automated generation of Diagrams for your templates
      - Leverage existing Templates on the web
      - Leverage the documantation
    - Supports almost all AWS resources
      - Everthing we see in this course is supported
      - You can use custom resources for resources not supported
  # Cloud Development Kit (CDK)
  - A way to enter your preferred language and the code is compiled into CloudFormation template JSON/YAML
  - Therefor you can deploy intrastructure and application runtime code together
    - Great for Lambda functions
    - Great for Dockers containers in ECS/EKS
  # Elastic Beastalk Overview
  - its a Developer centric view of depoying a app on AWS
  - Its uses all the components we saw before: EC2, ASG, ELB, RDS, etc
  - Its a all-in-one view thats easy to make sense of
  - # Beanstalk= Paas Platform as a Service
  - its free but you pay for the underlining services
  # Elastic Beanstalk is a manged service
  - Instance config/ OS is handled by Beanstalk
  - Deployment stratagy is configurable but performed by EB
  - Capacity provisioning
  - LB and Auto scaling
  - App health-monitoring and responsiveness
# Just the application code is the resposibility of the developer
- Three architecture models:
  - Single instance deployment: good for dev
  - LB + ASG: Great for production and pre-production web applications
  - ASG only: Great for none web apps in production (workers,etc...)
# Beanstalk has a full Health Monitoring managering 

# Lecture 127 Beanstalk Hands on !!!!
# AWS CodeDeploy
- We want to deploy our application automatically
- Hybrid service, Works with EC2 Instances, Works with On-Premisis Servers

- Servers/ Instances must be provisioned and configured ahead of time with the CodeDeploy Agent

# Systems Manager (SSM)
- helps to mangage your EC2 and On-Premises system at scale
- Another Hybrid AWS service
- Get operational insights about the state of your infrastructure
- Suites of 10+ products
- Most Important Features
  - Patching automation for enhanced compliance
  - Run commands across entire fleets of service
  - Store parameter configuration with the SSM Parameter store
- WOrks for Linux, Windows, MacOS, and Rasberry Pi OS (Rasbian)
# SSM - EXAM HINT: Anytime you want to patch your fleet of EC2 instances or on premisis servers or a command consistantly across all yourt servers.

# System Manager SSM Session Manager
- used for patching systems at scale, gives you visibility and control of your infrastructure
- Allows you to start a secure shell on your EC2 and On-premises servers
- No SSH access, bastion host, or SSH keys needed
- No port 22 needed (better security)`
# System Manager Parameter Store
- secure storage for configuration and secrets
- SErverless, scalable, durable, easy, SDK
- Control access permissions using IAM
- Version tracking & encryptions (optional)

# Deployment - Summary
- CLoudFormation: (AWS only)
  - Inffastructure as code and works with almost all AWS services
  - Repeat across regions and accounts
- Beanstalk: AWS Only
  - PaaS Platform as a service, limited to ceertain or Docker
  - Deploy code consistntly with a known architecture ex: ALB+EC2+RDS
- CodeDeploy (hybrid): Deploy & upgrade any application onto servers
- Systems Manager (Hybrid): Patch, configure and run commands at scale

# Developer Services - Summary
- CodeCommit: stores code in a private git repository
- CodeBuild: build and test code in AWS
- CodeDeploy: Deploy code onto servers
- CodePipeline: Orchestration of pipeline
- CodeArtifact: Store software packages/ dependencies on AWS
- AWS CDK: Define your cloud infrastructure using a programming language
