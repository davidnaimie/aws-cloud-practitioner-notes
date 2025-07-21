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
- Bucket > Object > Key (S3 Buckets need to be unique and are created at a regional level)
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
## Billing & Pricing 
- pay as you go

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
 
  + ASG stratigies include
  - Manual scaling
  - Dynamic Scaling
  - (simple/step Scaling, Targwet tracking scaling, Scedule scaling)
  - Predictibve scaling


## Watched the AWS summit in NYC with Swami Sivasunramian
- breakthrough on agent AI
- 1 hour 22 min
- learning Agent Bedrock
- expanding on building frameworks 
- JUST RELEASED Strands Agent v1.0  building multi agent system 
- Amazon Bedrock AgentCore
  
## 🧠 Other Concepts Coming Soon
- Billing & Pricing
- Global Infrastructure
- Shared Responsibility Model
- 
