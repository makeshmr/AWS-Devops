
<img width="470" alt="Screenshot 2025-05-01 at 6 05 45 PM" src="https://github.com/user-attachments/assets/e62d8a46-b94d-4f75-af0e-8c4d6cf4e33f" />

---

#### Why Does IAM Have Four Components?

You might wonder: **if IAM is just solving authentication and authorization**, why does AWS provide four different components?

Let’s break it down with real-world reasoning from a DevOps perspective.

---

##### 1. Users – For Authentication

**What it is:**  
An IAM User is an individual identity with credentials to log into the AWS environment.

**Why it's needed:**  
When a new employee joins (say, `employee501`), they need an AWS identity to access resources. Creating a user allows **secure login and individual tracking** of actions.

---

##### 2. Policies – For Authorization

**What it is:**  
A Policy is a JSON document that defines **what actions a user/group/role can perform** on which AWS services.

**Why it's needed:**  
Creating a user lets them in the door. Policies define **what they can do once inside** (read S3, launch EC2, etc.).  
Without a policy, users can’t do anything — not even view services.

> 🛡️ Policies implement **least privilege access**.

---

##### 3. Groups – For Efficiency

**What it is:**  
Groups let you **assign permissions to multiple users at once**.

**Why it's needed:**  
Manually assigning policies to every new user is inefficient. Instead:
- Create groups like `Developers`, `QA`, `DBAdmins`
- Attach appropriate policies to each group
- Add users to the right group

Now, new users instantly inherit the correct permissions — reducing manual work and error.

---

##### 4. Roles – For Applications and Temporary Access

**What it is:**  
Roles provide **temporary access to AWS services** and are assumed by trusted entities like applications, EC2 instances, or users from another AWS account.

**Why it's needed:**  
Roles are ideal when:
- A service (like EC2 or a Lambda function) needs to access another AWS service (like S3)
- You don’t want to manage permanent credentials
- Cross-account or third-party access is needed

> 🔁 Roles are **assumed**, not permanently assigned. They are for **non-human entities or temporary access needs**.

---

## Example Use Case: IAM in Action

| Scenario | IAM Component Used | Purpose |
|---------|---------------------|---------|
| New employee joins | **User** | Give login access |
| Restrict access to only S3 read | **Policy** | Define allowed actions |
| Add user to Dev team | **Group** | Apply shared permissions |
| EC2 instance needs to read from S3 | **Role** | Temporary, non-user access |

---

## Summary

| Component | Used For | Typical Use |
|----------|----------|--------------|
| **User** | Authentication | Employees, Devs, Admins |
| **Policy** | Authorization | Permissions control |
| **Group** | Access management | Organize users efficiently |
| **Role** | Temporary/automated access | Services, apps, cross-account |

---

## Coming Up Next

- Creating IAM groups and attaching policies
- Using IAM roles with EC2
- Hands-on with least privilege principle

