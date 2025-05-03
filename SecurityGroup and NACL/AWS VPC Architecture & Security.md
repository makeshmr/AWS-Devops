# AWS VPC Architecture & Security - Hands-on Guide

## Overview

In this guide, we explore the key components and security mechanisms of an **AWS Virtual Private Cloud (VPC)**. This architecture is used to securely deploy applications and resources in AWS while controlling network access at multiple levels. 

---

## 🧑‍💻 What is a VPC?

A **VPC (Virtual Private Cloud)** is a logically isolated network within AWS. You can define the IP address range, create subnets, configure route tables, and set up network gateways, all within a secure environment that mimics a traditional network setup.

### Key Terms:
- **VPC**: Your virtual network on AWS.
- **CIDR Block**: The IP address range of the VPC (e.g., `10.1.0.0/16`).
- **Subnet**: A subdivision of the VPC for better organization.
- **Internet Gateway (IGW)**: A gateway that connects your VPC to the internet.

---

## 🌐 VPC Architecture Explained

### Subnets in VPC
- **Public Subnet**: A subnet that has direct access to the internet through the Internet Gateway.
- **Private Subnet**: A subnet that does not have direct internet access. It is used for internal resources such as application servers and databases.

#### Example:
When you create a VPC, you define its **CIDR block** (e.g., `10.1.0.0/16`), which allows you to assign up to **65,536 IP addresses**. 

Within the VPC, you can create:
- **Public Subnets**: These subnets can be accessed from the internet.
- **Private Subnets**: These subnets are isolated and cannot be accessed directly from the internet.

For example, you may define:
- **Public Subnet** with IP range `10.1.1.0/24`
- **Private Subnet** with IP range `10.1.2.0/24`

#### Traffic Flow Example:
1. A **user** requests an application via a **public IP** (Internet Gateway).
2. The request is routed to a **Load Balancer** placed in the **public subnet**.
3. The Load Balancer forwards the request to an **EC2 instance** in the **private subnet**.
4. **Security Groups** and **NACLs** enforce security rules.

---

## 🛡️ Security Mechanisms in AWS VPC

### 1. **Security Groups (SG)**

- **Instance-Level Security**: Security Groups act as **virtual firewalls** for EC2 instances.
- **Stateful**: If you allow inbound traffic, the response traffic is automatically allowed.

#### Example Security Group Setup:
- **Allow HTTP (port 80)** traffic from anywhere (`0.0.0.0/0`).
- **Allow SSH (port 22)** traffic only from a specific IP address (`your-IP/32`).
  
Security Groups are used to control traffic to your EC2 instances and are applied **per instance**.

### 2. **Network Access Control Lists (NACLs)**

- **Subnet-Level Security**: NACLs control traffic entering or leaving a subnet.
- **Stateless**: You must define both inbound and outbound rules. 

#### Example NACL Setup:
- **Inbound**: Allow traffic on TCP port 80 from any IP address.
- **Outbound**: Allow traffic on TCP port 443 to the internet.

NACLs are applied at the **subnet** level and can be used to block specific traffic, such as from known malicious IP addresses.

---

## 🔄 Real-World Scenario

### Scenario: Web Application Hosting

Let’s say we are building a **ticket booking platform**. The architecture could look like this:
1. **Public Subnet**:
   - Contains a **Load Balancer** for incoming traffic.
2. **Private Subnet**:
   - Contains **EC2 instances** that run the application logic (not exposed directly to the internet).

In this case:
- The **Load Balancer** in the public subnet routes requests to **EC2 instances** in the private subnet.
- **Security Groups** are configured to allow only the Load Balancer to access the EC2 instances, while blocking direct public access.

### Security Measures:
1. **Security Groups** ensure only specific traffic reaches the EC2 instances.
2. **NACLs** can restrict traffic at the subnet level, such as blocking certain IPs or only allowing traffic from specific regions.

---

## 💡 Why Security is Crucial in AWS

Before migrating to the cloud, organizations prioritize **security**. Here’s why:
1. **Data Protection**: The public cloud hosts critical data, such as databases, user credentials, and more.
2. **Access Control**: You need to restrict unauthorized access at multiple layers (subnet, EC2, application).
3. **Compliance**: Many industries have stringent compliance standards (e.g., HIPAA, GDPR) that require strong security practices.

AWS provides **multiple security layers**, including:
- **IAM (Identity and Access Management)** for user access.
- **VPC** with **subnets**, **Internet Gateway**, and **NACLs** for traffic control.
- **Security Groups** for fine-grained EC2 instance access.
