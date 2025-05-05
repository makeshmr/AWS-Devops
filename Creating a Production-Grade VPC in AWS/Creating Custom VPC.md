## 🎯 Objective

We'll create a **custom VPC** using the **"VPC and more"** wizard to deploy a secure and highly available infrastructure across **two Availability Zones**.

---

## 🛠️ Step-by-Step: Creating the VPC

### 🔍 1. Navigate to VPC Service
- Go to your **AWS Console**
- In the **Search Bar**, type `VPC` and click on **“Your VPCs”** under *Isolated Cloud Resources*

---

### 🧱 2. Create VPC using “VPC and More”
- Click **Create VPC**
- Choose the **“VPC and more”** option (recommended)
  - ✅ Automatically creates:
    - Public & Private subnets in **two Availability Zones**
    - Internet Gateway
    - Route tables
    - NAT Gateway (if selected)

<img width="470" alt="Screenshot 2025-05-05 at 7 51 37 AM" src="https://github.com/user-attachments/assets/9b68b98f-aebd-446e-b2a3-de68c974859f" />


    

---

### 🧭 3. Architecture Overview

The wizard creates:

| Component             | Quantity | Availability Zones |
|----------------------|----------|--------------------|
| Public Subnets       | 2        | 1A, 1B             |
| Private Subnets      | 2        | 1A, 1B             |
| Internet Gateway     | 1        | Shared             |
| NAT Gateway          | 1 or 2   | As selected        |
| Route Tables         | 4        | Linked accordingly |
| Bastion Host (Later) | Manual   | Public Subnet      |

> 📌 _Reference Architecture_: Search "AWS Public Private Subnet Architecture" for a visual overview.  
> 💡 AWS also provides sample blog diagrams — but we’ll build this with deeper understanding.

---

### ⚙️ 4. Configuration Options

Fill out the form as follows:

| Field                        | Value                     |
|-----------------------------|---------------------------|
| **VPC Name**                | `aws-prod-example`        |
| **IPv4 CIDR**               | Default (e.g., `10.0.0.0/16`) |
| **IPv6 CIDR**               | None                      |
| **Availability Zones**      | `2`                       |
| **Public Subnets**          | `2`                       |
| **Private Subnets**         | `2`                       |
| **NAT Gateway**             | `1 per AZ` (Recommended)  |
| **VPC Endpoint for S3**     | `None` (Uncheck it)       |

✅ Confirm the preview diagram updates to reflect your settings.

---

### ⚡ 5. Create the VPC

- Click **Create VPC**
- AWS will now provision all components
- Review all resources created (subnets, route tables, NAT gateway, etc.)

---

## 🧠 Behind the Scenes: Key Concepts

### 🌐 Internet Gateway & Route Tables
- Public Subnets are attached to route tables that **route traffic to the Internet Gateway**
- Private Subnets are isolated from direct internet access

### 🔁 NAT Gateway
- Allows instances in **private subnets** to **access the internet securely**
- Requires an **Elastic IP**

### 📌 Elastic IP Address (EIP)
- A **static IP** that does not change across restarts
- Used for **NAT Gateways** or other static endpoints

> If you run into EIP limit issues:
> - Go to **EC2 > Elastic IPs**
> - Release unused EIPs
> - Retry the VPC creation

---

## 🧪 Verification

After the creation completes:
1. Navigate to **VPC Dashboard**
2. Confirm:
   - 1 VPC created
   - 2 Public + 2 Private Subnets
   - Internet Gateway attached
   - NAT Gateway created and linked
   - Route tables configured correctly

<img width="470" alt="Screenshot 2025-05-05 at 7 55 11 AM" src="https://github.com/user-attachments/assets/89c9a09a-ae57-4709-ad29-55c0bec17230" />



---

## 📌 Notes & Troubleshooting

- VPC creation can take 1–2 minutes to reflect across all tabs.
- Be patient if the VPC doesn’t appear immediately.
- If Elastic IPs are exhausted, release old ones from **EC2 > Network & Security > Elastic IPs**.

---
