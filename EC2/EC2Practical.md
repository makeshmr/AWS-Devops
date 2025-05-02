# 🚀 Launching an EC2 Instance and Deploying Jenkins on AWS

This guide explains how to launch a **free-tier AWS EC2 instance**, connect to it via **SSH**, and deploy **Jenkins**, a leading automation server. Ideal for DevOps learners and beginners experimenting with cloud deployments.

---

## 📋 Prerequisites

- AWS account ([Sign up](https://aws.amazon.com/))
- Basic Linux terminal knowledge
- SSH client (Linux/macOS terminal, PuTTY, or MobaXterm)

---

## 1️⃣ Launch an EC2 Instance

### Step 1: Access EC2 Dashboard

1. Log in to the [AWS Console](https://console.aws.amazon.com/)
2. Navigate to **EC2** > **Instances**
3. Click **Launch Instance**

---

### Step 2: Configure Instance Details

| Setting | Value |
|--------|-------|
| **Name** | `my-first-instance` (or your choice) |
| **AMI** | Ubuntu (Free tier eligible) |
| **Instance Type** | `t2.micro` (1 vCPU, 1GB RAM — free tier) |
| **Key Pair** | Create/download a `.pem` file (used for SSH) |

> ⚠️ Store your `.pem` file securely — it cannot be downloaded again!

---

### Step 3: Network Settings

- Use the default **VPC**
- Ensure a **public IPv4 address** is assigned
- Default **security group** is fine for now (you’ll update it later)

---

### Step 4: Storage

- 8 GiB of General Purpose SSD (gp2) is default (and sufficient)

---

### Step 5: Launch the Instance

Click **Launch Instance** and wait until its status becomes **running**.

---

## 2️⃣ Connect to EC2 via SSH

### Step 1: Set File Permissions (Linux/macOS)

```bash
chmod 600 ~/Downloads/aws-login.pem

