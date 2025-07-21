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
- Bucket > Object > Key

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
  - Scale EC2 instances based on the demand on your system, replace unhealthy
  - Integrated with the ELB


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
