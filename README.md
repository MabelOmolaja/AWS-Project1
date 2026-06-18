# AWS Secure Multi-AZ Base Environment

**Author:** Mabel Omolaja (maybelomolaja@gmail.com)

**Project Type:** AWS Networking & Security Architecture

**Status:** Completed

---

# Project Overview

This project demonstrates the design and implementation of a secure, company-style AWS networking environment built using core AWS infrastructure services.

The goal was to create a production-inspired foundation that supports secure application deployment, controlled internet access, network segmentation, and identity management best practices.

Rather than simply deploying resources, this project focused on understanding how cloud environments are structured in real organisations, where security, scalability, and controlled access are critical.

---

# Project Objectives

The environment was designed to achieve the following goals:

* Build a custom Virtual Private Cloud (VPC)
* Implement network segmentation using public and private subnets
* Configure secure internet access using an Internet Gateway and NAT Gateway
* Create route tables to control network traffic flow
* Apply Security Group rules following the principle of least privilege
* Implement IAM access controls with MFA protection
* Produce architecture documentation and infrastructure diagrams

---

# Architecture Components

## Networking

### Virtual Private Cloud (VPC)

A dedicated VPC was created to provide complete control over networking, routing, and security boundaries.

<img width="1280" height="637" alt="VPC" src="https://github.com/user-attachments/assets/4b62b204-68c5-4a75-a142-52a39db85f09" />


### Public Subnets

Two public subnets were deployed across separate Availability Zones.

These subnets are intended for internet-facing resources such as:

* Load Balancers
* Bastion Hosts
* Public-facing web services

### Private Subnets

Two private subnets were deployed across separate Availability Zones.

These subnets are intended for internal workloads such as:

* Application servers
* Backend services
* Databases

Resources inside these subnets are not directly accessible from the internet.

---

## Internet Gateway (IGW)

<img width="1280" height="643" alt="IGW" src="https://github.com/user-attachments/assets/8af3f6d8-d314-4512-a1f1-4bf1dccd41f2" />

An Internet Gateway was attached to the VPC to provide inbound and outbound internet connectivity for resources located within public subnets.

---

## NAT Gateway

A NAT Gateway was deployed to allow resources in private subnets to initiate outbound internet connections while remaining inaccessible from the public internet.

<img width="1280" height="644" alt="NAT" src="https://github.com/user-attachments/assets/ee416938-0696-4827-a848-6b9f87ec5eea" />

This approach is commonly used for:

* Operating system updates
* Package downloads
* External API communication

without exposing private resources to inbound internet traffic.

---

## Route Tables

Separate route tables were configured to control traffic flow.

### Public Route Table (Pub-rtb)

Configured with routes to:

* Local VPC traffic
* Internet Gateway (0.0.0.0/0)

<img width="1280" height="638" alt="RT" src="https://github.com/user-attachments/assets/710e81a7-1fe2-433d-884a-4bee5c694e2a" />

### Private Route Table (Pri-rtb)

Configured with routes to:

* Local VPC traffic
* NAT Gateway for outbound internet access

This design ensures proper network isolation while maintaining required connectivity.

---

# 🔒 Security Design

## Security Groups

Security Groups were designed using a layered security approach.

<img width="1280" height="661" alt="security groups" src="https://github.com/user-attachments/assets/e7f00271-b7fe-40b9-92d5-de4186711509" />

### Web Security Group

Allows inbound HTTP/HTTPS traffic from the internet.

Purpose:

* Supports public-facing web applications.

### Application Security Group

Allows traffic only from approved web-tier resources.

Purpose:

* Protects backend application services from direct public access.

### Database Security Group

Allows traffic only from approved application-tier resources.

Purpose:

* Restricts database access to authorised internal systems.

This security model reduces the attack surface and follows industry best practices for workload isolation.

---

# 👤 Identity & Access Management (IAM)

A custom IAM role named:

**DevOpsStudentRole**

was created in accordance with the principle of least privilege.

<img width="1280" height="673" alt="readonly" src="https://github.com/user-attachments/assets/61f5159e-461e-4e6d-9b46-123e53cc225f" />


The role was configured to provide only the permissions required to perform designated tasks rather than broad administrative access.

<img width="1278" height="627" alt="DevOps MFA" src="https://github.com/user-attachments/assets/dbd7037c-c755-48d0-ac01-3b875742be94" />


Additional security controls included:

* Multi-Factor Authentication (MFA)
* Permission boundaries based on job requirements
* Reduced risk of accidental or unauthorised changes

---

# 📊 Architecture Diagram

The architecture includes:

* 1 VPC
* 2 Availability Zones
* 2 Public Subnets
* 2 Private Subnets
* Internet Gateway
* NAT Gateway
* Route Tables

<img width="1536" height="1024" alt="B233D15A-7D74-43E8-95F6-D170D5A2773B" src="https://github.com/user-attachments/assets/ae42f3d6-737b-4dfc-8b0e-f2ed3576c408" />

---

# Key Skills Demonstrated

* AWS Networking
* VPC Design
* Route Table Configuration
* Internet Gateway Implementation
* NAT Gateway Configuration
* Security Group Design
* IAM Access Control
* Least Privilege Security
* Multi-AZ Architecture
* Cloud Infrastructure Documentation

---

# What I Learned

This project strengthened my understanding of how secure AWS environments are structured in production settings.

Key lessons included:

* The difference between Internet Gateways and NAT Gateways
* How route tables control traffic flow
* Why network segmentation is important
* How Security Groups enforce layered security
* The importance of least-privilege IAM design
* How cloud networking components work together to create secure environments

---

# Outcome

By completing this project, I demonstrated the ability to build a secure AWS foundation that reflects common enterprise networking and security practices.

The environment provides a scalable starting point for deploying future applications and infrastructure while maintaining security and operational control.
