# AWS Secure Multi-AZ Base Environment

**Author:** Mabel Omolaja (maybelomolaja@gmail.com)

**Project Type:** AWS Networking & Security Architecture

**Status:** Completed

---

# Project Overview

## AWS Secure Multi-Tier VPC Architecture (Production-Style Cloud Project)

![AWS](https://img.shields.io/badge/AWS-Cloud-orange?style=for-the-badge&logo=amazon-aws)
![VPC](https://img.shields.io/badge/Networking-VPC-blue?style=for-the-badge)
![Security](https://img.shields.io/badge/Security-IAM%20%26%20Least%20Privilege-red?style=for-the-badge)
![Architecture](https://img.shields.io/badge/Architecture-Multi--Tier-green?style=for-the-badge)

This project demonstrates how I designed and built a **secure, scalable, production-style AWS cloud environment** that simulates real-world enterprise infrastructure.

The focus was on building a **multi-tier architecture inside AWS VPC** with strong security controls, network segmentation, and high availability design principles.

### Core Skills Demonstrated

- AWS Networking & VPC Design  
- Secure Cloud Architecture Patterns  
- IAM Least-Privilege Access Control  
- Multi-Tier System Architecture  
- High Availability (Multi-AZ Deployment)  

---

## Architecture Overview

A **3-tier cloud architecture** was deployed inside a custom AWS VPC:

- **Web Tier (Public Subnets)** → Internet-facing layer  
- **Application Tier (Private Subnets)** → Business logic layer  
- **Database Tier (Private Subnets)** → Data storage layer  

✔ Deployed across **2 Availability Zones**  
✔ Designed for **fault tolerance & scalability**

---
## 🔁 System Architecture Flow

```text
Internet
   │
   ▼
Internet Gateway (IGW)
   │
   ▼
Public Subnets (Web Tier)
   │
   ▼
Web Tier 
   │
   ▼
Private Subnets (Application Tier)
   │
   ▼
Application Tier
   │
   ▼
Private Subnets (Database Tier)
   │
   ▼
Database Tier
```


---

## AWS Services Used

* Amazon VPC
* Public & Private Subnets
* Internet Gateway (IGW)
* NAT Gateway
* Route Tables
* Security Groups
* IAM (Identity and Access Management)

---

## 🌐 Network Design

### 🏛️ VPC Setup

* Created a custom VPC with a dedicated CIDR block
* Enabled DNS resolution and DNS hostnames
* Implemented a Multi-AZ architecture spanning two Availability Zones

---

### 📊 Subnet Design

| Tier     | Type    | Purpose                 |
| -------- | ------- | ----------------------- |
| Web Tier | Public  | Internet-facing layer   |
| App Tier | Private | Application logic layer |
| DB Tier  | Private | Data storage layer      |

---

### 🔀 Routing Configuration

* Public Subnets → Internet Gateway (IGW)
* Private Subnets → NAT Gateway
* No direct internet access for private workloads

---

## 🔐 Security Architecture

### Security Groups

#### Web-SG

* HTTP (80)
* HTTPS (443)
* Open to internet traffic

#### App-SG

* Port 8080
* Accessible only from Web-SG

#### DB-SG

* MySQL (3306)
* PostgreSQL (5432)
* Accessible only from App-SG

---

### 🔒 Security Principles Applied

* Principle of Least Privilege
* Tier-to-tier communication only
* No direct database exposure
* Controlled inbound and outbound traffic
* Security group-based access control

---

## 👤 IAM Configuration

### IAM Role: DevOpsStudentRole

#### Policies Attached

* AmazonEC2ReadOnlyAccess
* AmazonVPCReadOnlyAccess
* AmazonS3ReadOnlyAccess

#### Security Enhancements

* Multi-Factor Authentication (MFA) enabled
* Least-privilege access model enforced

---

## 🛠️ Implementation Steps

### 1️⃣ VPC Setup

* Created a custom VPC with a dedicated CIDR block
* Enabled DNS resolution and DNS hostnames

### 2️⃣ Subnet Design

* Created Public Subnets for the Web Tier
* Created Private Subnets for the Application Tier
* Created Private Subnets for the Database Tier
* Distributed resources across two Availability Zones for high availability

### 3️⃣ Internet Gateway (IGW)

* Created and attached an Internet Gateway to the VPC
* Enabled internet access for public-facing resources

### 4️⃣ NAT Gateway

* Deployed a NAT Gateway within a public subnet
* Assigned an Elastic IP address
* Enabled secure outbound internet access for private subnets

### 5️⃣ Route Tables

#### Public Route Table

* 0.0.0.0/0 → Internet Gateway

#### Private Route Table

* 0.0.0.0/0 → NAT Gateway

### 6️⃣ Security Groups

* Implemented tier-based network access controls
* Restricted communication between tiers using security groups
* Applied least-privilege networking principles

### 7️⃣ IAM & MFA

* Created the DevOpsStudentRole IAM role
* Attached read-only AWS managed policies
* Enabled Multi-Factor Authentication (MFA)

### 8️⃣ Architecture Validation

Validated the following traffic flow:

* Internet → Internet Gateway → Web Tier
* Web Tier → Application Tier
* Application Tier → Database Tier
* Private Subnets → NAT Gateway → Internet

---

## Architecture Diagram

<img width="1536" height="1024" alt="aws-architecture" src="https://github.com/user-attachments/assets/3cd196a0-7c57-44a7-bacd-6995ce3136ef" /> 

---

## Key Learnings

* How Amazon VPC provides network isolation within AWS
* The difference between Internet Gateways and NAT Gateways
* Designing secure multi-tier cloud architectures
* Implementing micro-segmentation using Security Groups
* Applying IAM Role-Based Access Control (RBAC)
* Enhancing cloud security through MFA and least-privilege access

---

## Future Improvements

* Deploy EC2 instances within each application tier
* Implement an Application Load Balancer (ALB)
* Configure Auto Scaling Groups
* Add CloudWatch monitoring and alerting
* Rebuild the environment using Terraform (Infrastructure as Code)
* Introduce CI/CD automation using GitHub Actions

---

## Final Note

This project demonstrates my ability to design and implement a secure, production-style AWS environment using industry-standard cloud architecture and security best practices. The solution showcases practical experience with AWS networking, security controls, access management, and infrastructure design principles commonly used in Cloud Engineer, AWS Engineer, and DevOps Engineer roles.
