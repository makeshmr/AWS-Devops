![Screenshot 2025-05-03 at 6 55 40 PM (2)](https://github.com/user-attachments/assets/d02e0ff1-5fce-432a-a50e-f57cccfc9afe)


# AWS VPC, EC2, Security Groups & NACLs Demo

This project demonstrates how to set up a **custom Virtual Private Cloud (VPC)** in AWS, launch an **EC2 instance**, and explore the behavior of **Security Groups** and **Network ACLs (NACLs)**.

---

## 📘 What You'll Learn

- Creating a custom VPC with associated components
- Launching and connecting to an EC2 instance
- Hosting a Python HTTP server
- Testing access control with Security Groups and NACLs

---

## 🔧 Prerequisites

- AWS Account
- Key pair (.pem file) for SSH access
- Basic understanding of VPC, subnets, CIDR blocks, and IP addressing
- Familiarity with terminal/CLI

---

## 🛠️ Step-by-Step Guide

### 1. Create a Custom VPC

1. Go to **VPC** service in AWS Console.
2. Click `Create VPC` → choose **VPC and more (recommended)**.
3. AWS will create:
   - Custom VPC
   - Internet Gateway (IGW)
   - Public and private subnets
   - Route tables
   - Default NACL
4. Use default CIDR block `10.0.0.0/16`.
5. Name it `demo-vpc`.
6. Click `Create VPC`.

---

### 2. Review Resource Map

- After VPC creation, click on the **Resource Map**.
- Visualize how the Internet Gateway is attached and which subnets are public/private.

---

### 3. Launch an EC2 Instance

1. Go to **EC2 → Launch Instance**.
2. Set configurations:
   - Name: `demo-instance`
   - AMI: Ubuntu
   - Type: `t2.micro`
   - Key pair: `aws-login.pem`
3. Configure networking:
   - VPC: Select `demo-vpc`
   - Subnet: Choose public subnet (e.g., `demo-public-subnet-1`)
   - Enable auto-assign public IP
4. Security Group: Create a new one or use the default
5. Click `Launch`.

---

### 4. SSH into EC2

```bash
chmod 400 aws-login.pem
ssh -i aws-login.pem ubuntu@<EC2_PUBLIC_IP>

