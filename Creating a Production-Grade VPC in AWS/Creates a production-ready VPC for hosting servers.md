<img width="753" alt="Screenshot 2025-05-04 at 8 46 04 PM" src="https://github.com/user-attachments/assets/528ac2b9-9532-45b8-aebf-4bb43bed6c69" />

***This project demonstrates how to create a VPC that you can use for servers in a production environment***

To improve resiliency, you deploy the servers in 2 Availability Zones(AZs) using an Auto Scaling group and an Application Load Balancer. For additional security, you deploy the servers in private subnets. 
The servers receive requests through the load balancer. The servers can connect to the internet by using a NAT gateway. To improve resiliency, you deploy the NAT gateway in both AZs.

### Overview -
- The VPC has public subnets and private subnets in 2 AZs.
- Each public subnet contains a NAT gateway and a load balancer node.
- The servers run in the private subnets, are launched and terminated by using an Auto Scaling group, and receive traffic from the load balancer
- The servers can connect to the internet by using the NAT gateway.

### Implement 
- Custom VPC with public and private subnets in **two Availability Zones** (for high availability).
- **EC2 instances** in private subnets with **Auto Scaling**.
- **NAT Gateway** and **Application Load Balancer** in public subnets.
- **Bastion Host** for secure SSH access.
- Traffic routing from users via **Internet Gateway** ➝ **Load Balancer** ➝ **EC2 instances**.

### 🔒 Why Use This Architecture?

- **Highly Available:** Deploying across 2 AZs ensures failover support.
- **Secure:** Private instances are inaccessible directly from the internet.
- **Scalable:** Auto Scaling Group ensures performance under load.
- **Maintainable:** Load Balancer, Bastion, and NAT Gateway simplify access and control.

### Steps
1. Create a VPC with public/private subnets across two AZs
2. Set up NAT Gateway and Internet Gateway
3. Deploy Bastion Host in Public Subnet
4. Deploy EC2 instances via Auto Scaling Group in Private Subnet
5. Configure Application Load Balancer
6. Test the traffic flow and instance connectivity


## 🧭 Architecture Diagram

> 📌 _You can refer to the architecture diagram in the `/diagrams` folder or [here](#)._  
Here’s a high-level summary of the architecture:

- **Public Subnet:**
  - Application Load Balancer
  - NAT Gateway
  - Bastion Host (Jump Server)
- **Private Subnet:**
  - Auto Scaling Group with EC2 instances
- **Traffic Flow:**  
  `Internet → Load Balancer → EC2 (Private Subnet)`

---

## 🧱 Services & Concepts Used

### ✅ VPC & Subnets
- Custom VPC with **two Availability Zones**
- Public and Private Subnets for isolation

### ✅ Auto Scaling Group (ASG)
- Ensures high availability by automatically adjusting the EC2 instance count
- Based on CPU or request metrics

### ✅ Load Balancer
- Distributes incoming traffic across multiple EC2 instances
- Supports round-robin, path-based, and host-based routing

### ✅ NAT Gateway
- Allows private instances to access the internet **without exposing public IPs**
- Mask internal IPs for outbound traffic

### ✅ Bastion Host (Jump Server)
- Located in Public Subnet
- Used for **SSH access** to private EC2 instances
- Enhances security and enables access logging

---




  




