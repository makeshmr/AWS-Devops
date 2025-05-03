# AWS Security Model - Shared Responsibility and Network Security

## Overview

In this document, we explain the **shared responsibility model** for security in AWS, focusing on how AWS handles security and how **DevOps Engineers**, **AWS Admins**, and **Network Engineers** play an important role in securing AWS resources. We will also cover two critical components of AWS security: **Security Groups** and **Network Access Control Lists (NACLs)**.

---

## 🔒 AWS Security - Shared Responsibility

AWS follows a **shared responsibility model** when it comes to security. This means that AWS takes responsibility for securing the **cloud infrastructure**, while customers (e.g., DevOps Engineers, AWS Admins) are responsible for securing the **data** and **applications** they deploy on the cloud.

### What Does This Mean?

1. **AWS’s Responsibility**:
   - AWS ensures the security of the **underlying infrastructure**. This includes the physical hardware, network, and data centers. They protect the network, servers, storage devices, and facilities hosting your AWS services.
   - AWS provides tools such as **VPC**, **Security Groups**, **IAM**, **API Gateway**, **NACLs**, and more to help you secure your environment.

2. **Customer’s Responsibility**:
   - Customers (DevOps Engineers, AWS Admins) are responsible for configuring and managing the security controls in their **AWS environment**. This includes configuring VPCs, setting up **Security Groups**, defining **NACLs**, implementing **IAM roles**, and ensuring the security of their applications and data.
   - **You** are responsible for securing your applications, databases, and ensuring your services are set up in a secure manner (e.g., choosing appropriate instance types, setting firewalls, ensuring encryption at rest).

The fundamental takeaway: **AWS will secure the cloud, but you need to secure your data and applications within the cloud**.

---

## 🔐 Security Groups and NACLs

As a DevOps Engineer or AWS Admin, one of your most critical roles is ensuring that your security configurations are properly set up. **Security Groups** and **NACLs** (Network Access Control Lists) serve as **last-line defenses** before a user request reaches your application.

### What are Security Groups?

- **Security Groups** are stateful firewalls that control the inbound and outbound traffic for your EC2 instances.
- They act at the **instance level** and ensure that only authorized traffic is allowed to reach your applications running on EC2 instances.
- Security Groups are **stateful**, meaning that if you allow inbound traffic, the response traffic is automatically allowed, even if you don’t explicitly allow outbound traffic.

#### Example:
- **Inbound rule**: Allow HTTP (port 80) traffic from anywhere (`0.0.0.0/0`).
- **Outbound rule**: Allow all outbound traffic to any destination.

### What are NACLs?

- **Network Access Control Lists (NACLs)** are stateless firewalls that control the inbound and outbound traffic at the **subnet** level.
- Unlike Security Groups, NACLs are **stateless**, meaning that you need to define both inbound and outbound rules explicitly.
- NACLs can be used to block certain types of traffic or allow specific traffic for all instances in a subnet.

#### Example:
- **Inbound rule**: Allow traffic from the IP range `10.0.0.0/24` (an internal network).
- **Outbound rule**: Allow traffic to the internet (e.g., `0.0.0.0/0`).

---

## 🔍 Why Security Groups and NACLs are Critical

Both **Security Groups** and **NACLs** play an important role in protecting your applications, but they act at different layers:

1. **Security Groups**: Act as the **first line of defense** at the instance level. They ensure that only authorized users and applications can communicate with your EC2 instances.
2. **NACLs**: Act as the **second line of defense** at the subnet level. They can block or allow traffic at a broader level, before it reaches individual instances.

Together, they form a **layered defense** mechanism, where traffic flows through multiple layers of security controls before reaching the application. If either of these layers is misconfigured, your application may become vulnerable to attacks.

#### The Last Point of Security:
Before any user request reaches your application, it passes through several stages:
- **User Request** → **Internet Gateway** → **VPC** → **Subnets** → **Security Groups** and **NACLs**.

Here, **Security Groups** and **NACLs** act as the **last point of security**. If configured improperly, this is where the security of your application could be compromised. Hence, it is critical to configure these components correctly to prevent unauthorized access.

---

## 🧑‍💻 Role of DevOps Engineers in Security

As a **DevOps Engineer** or **AWS Admin**, you play a critical role in configuring and managing the security settings for your AWS environment. Here’s a summary of your responsibilities:
- **Configure VPCs** to segment your network into public and private subnets.
- **Set up and manage Security Groups** to define access rules for EC2 instances.
- **Configure NACLs** for subnet-level traffic control.
- **Monitor and log traffic** to detect potential security breaches or unauthorized access.
- **Implement encryption** for data at rest and in transit.
- **Define IAM roles** and permissions to ensure that only authorized users and services can access your resources.

---

In AWS, security is a shared responsibility. AWS takes care of the physical infrastructure and some security tools, but the customer (DevOps Engineers or AWS Admins) is responsible for securing their applications, data, and configurations. Below is a table that outlines the shared responsibilities of AWS and the customer:

| **Concept**                   | **AWS Responsibility**                                                         | **Customer Responsibility (DevOps/AWS Admin)**                                       | **Explanation**                                                                                                  |
|-------------------------------|---------------------------------------------------------------------------------|------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------|
| **Cloud Infrastructure**       | AWS secures the physical hardware, data centers, and network infrastructure.    | Customers do not need to secure physical infrastructure.                           | AWS ensures the physical security and management of the data centers, servers, and network hardware.             |
| **Security Groups**            | AWS provides the tool to configure security groups but does not manage them.   | Customers configure security groups to control traffic to EC2 instances.           | Security Groups are stateful firewalls that control the inbound and outbound traffic at the instance level.     |
| **NACLs (Network ACLs)**       | AWS provides the NACLs feature for controlling traffic at the subnet level.    | Customers configure NACLs to control inbound and outbound traffic for subnets.     | NACLs are stateless firewalls that provide subnet-level traffic control, allowing/blocking traffic based on rules.|
| **Data Security**              | AWS provides encryption tools for data at rest and in transit.                  | Customers are responsible for ensuring that data is properly encrypted and secure. | Customers are responsible for configuring encryption, access control, and protection of sensitive data.         |
| **IAM (Identity & Access)**   | AWS provides IAM to manage access to AWS resources.                            | Customers configure IAM roles and permissions for users and services.             | IAM ensures that only authorized users and services can access AWS resources based on their permissions.         |
| **Application Security**       | AWS provides the environment for deployment, but customers manage the apps.    | Customers configure their apps, including firewalls, encryption, and monitoring.   | Customers must secure their applications by configuring firewalls, applying patches, and ensuring secure code.    |
| **VPC (Virtual Private Cloud)**| AWS offers tools for setting up VPCs with public/private subnets and internet access. | Customers design VPCs with appropriate subnets and routing for application isolation. | VPC allows customers to isolate their applications within private subnets and control traffic with security tools.|
| **Monitoring & Logging**       | AWS provides tools like CloudWatch and CloudTrail for monitoring and logging.  | Customers configure CloudWatch to monitor security-related events and logs.        | Customers are responsible for setting up monitoring and taking corrective actions when security issues arise.     |

---

## 📑 Conclusion

AWS’s shared responsibility model means that **AWS secures the cloud infrastructure**, but **you** are responsible for securing your data, applications, and services within the cloud. By properly configuring **Security Groups** and **NACLs**, you ensure that your AWS resources are protected from unauthorized access and potential threats.

**Key Takeaways**:
- Security Groups are stateful and protect individual EC2 instances.
- NACLs are stateless and control traffic at the subnet level.
- Both act as critical security layers in your AWS environment.
- As a DevOps Engineer, you are responsible for configuring and managing these security measures effectively.
