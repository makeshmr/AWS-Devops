# AWS IAM (Identity & Access Management) Tutorial  
**Learn authentication, authorization, users, groups, and policies in AWS.**  

---

## 📌 Key Concepts  

### 1. **Root User vs. IAM User**  
- **Root User**:  
  - Created when setting up the AWS account.  
  - Has **full access** (avoid for daily tasks).  
- **IAM User**:  
  - Created for individuals/services with **granular permissions** (best practice).  

### 2. **Authentication & Authorization**  
- **Authentication**: Verifies identity (e.g., IAM user login).  
- **Authorization**: Defines permissions via **policies**.  

---

## 🛠️ Hands-On Steps  

### 🔹 **Create an IAM User**  
1. Log in to AWS as **root**.  
2. Navigate to **IAM → Users → Create User**.  
   - Set username (e.g., `test-user-501`).  
   - Enable **AWS Management Console access** + auto-generated password.  
3. **No permissions** initially → Test login (user can’t access services).  

### 🔹 **Attach Policies (Authorization)**  
1. Edit the IAM user → **Add permissions** → Attach `AmazonS3FullAccess`.  
2. Log in as the user → Verify access to **S3** (list/create buckets).  

### 🔹 **IAM Groups (For Scalability)**  
1. **Create a Group** (e.g., `Developers`).  
2. Attach policies (e.g., `AmazonEC2FullAccess`).  
3. Add users → All members inherit group permissions.  

---

## 📜 Policy Types  
| Type                | Description                          | Use Case                     |  
|---------------------|--------------------------------------|------------------------------|  
| **AWS Managed**     | Predefined by AWS (e.g., `AmazonS3ReadOnly`) | Quick setup for common needs |  
| **Custom Policies** | JSON-based, tailored permissions     | Fine-grained control         |  

---

## ✅ Best Practices  
- **🚫 Never use root for daily tasks** (security risk).  
- **👥 Use groups** to manage permissions at scale.  
- **🔐 Prefer IAM users for humans**, **roles for services**.  

---

## 🚀 Next Steps  
- Explore **custom policies** (JSON).  
- Learn **roles** during CI/CD integrations.  

---

## 📂 Repository Structure  
```plaintext
aws-iam-tutorial/  
├── screenshots/          # Example images  
├── policies/             # Sample custom policies (JSON)  
└── README.md             # This guide  
