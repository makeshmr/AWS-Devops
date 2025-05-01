# AWS-Devops
AWS Zero to Hero Course for DevOps Engineers 

#### Introduction to AWS

What is a private and public cloud? Why companies are moving to the public cloud, and what are the advantages of moving to the cloud? 
Also, you will be introduced to the basics of AWS, including the core services and their significance in DevOps practices. Finally, learn how to set up an AWS account and navigate the AWS Management Console.

#### AWS IAM(identity and Access Management)



IAM is **foundational to AWS security**. It controls **who can do what** in your AWS environment, making it one of the first services you should learn when starting your AWS journey—especially if you're aiming for a DevOps, Developer, or Cloud Engineer role.

---

##### 📚 Topics to Learn in IAM

###### 👤 IAM Users
- Create individual user accounts with **limited access**.
- ⚠️ *Avoid using the root account for daily tasks.*

###### 👥 IAM Groups
- Group users based on similar access needs.
- Attach policies to groups for easier management.

###### 🛡️ IAM Policies
- Define permissions using **JSON-based policy documents**.
- Control access to services, resources, and specific actions.

###### 🎭 IAM Roles
- Grant **temporary access** to users, applications, or AWS services.
- Often used for **cross-account access**, **EC2 instance roles**, and **federated identity**.

---

###### ✅ Best Practices

- 🔒 **Least Privilege Principle**  
  Grant only the permissions required to perform a task—nothing more.

- 🚫 **Zero Trust / Zero Access**  
  Start with no access and incrementally allow what's needed.

- 🔐 **MFA (Multi-Factor Authentication)**  
  Always enable MFA for root and privileged users.

- ⚠️ **Avoid Using Root Account**  
  Use it only for billing or account-wide settings. Lock it down with MFA.

