# 🔐 AWS Security Group vs Network ACL (NACL)

## 🛡️ What is a Security Group?

A **Security Group (SG)** is a virtual firewall that operates at the **instance level** (e.g., EC2). It controls both **inbound** and **outbound** traffic to and from your EC2 instance.

---

### ✅ Use Case Example

1. Created an AWS account.
2. Used the **default VPC** (automatically provided by AWS).
3. Launched an **EC2 instance** inside that VPC.
4. Deployed a **Jenkins application** on the EC2 instance.
5. Tried accessing Jenkins via a browser, but failed.

This happened because **Security Groups by default deny all inbound traffic**. We resolved it by allowing traffic on: port 8080


> ⚠️ If too many ports are opened (e.g., 9000, 10000, etc.), it increases security risks. Always allow only required traffic.

---

## 🔁 Inbound vs Outbound in SG

- **Inbound**: Traffic coming *into* the EC2 instance.
- **Outbound**: Traffic going *out of* the EC2 instance.

### 🔒 Default AWS Behavior

| Traffic Direction | Default Behavior |
|------------------|------------------|
| Inbound          | **Deny all**     |
| Outbound         | **Allow all** (except **Port 25**) |

> 📨 **Port 25** (SMTP for emails) is blocked by default to prevent spam activities.

---

## 📋 Security Group Highlights

- Works at the **EC2 instance level**
- **Stateful**: If an inbound rule allows traffic, response traffic is automatically allowed
- Can only **allow** traffic, **not deny**
- Useful for **fine-grained** instance-level access control

---

## 🔒 What is a NACL?

A **Network Access Control List (NACL)** is a firewall at the **subnet level**. It allows or denies traffic to **all instances** within a subnet.

---

### ✅ Use Case Example

Imagine Development Team 1 is given a subnet. They deploy EC2 instances and open **all traffic** via SG for convenience.

To prevent security issues:
- Apply a **NACL** at the subnet level to **deny all traffic**, and only **allow required ports/IPs**.

This overrides poorly configured SGs.

---

## 🧾 NACL Highlights

- Works at the **subnet level**
- **Stateless**: Return traffic must be explicitly allowed
- Supports both **Allow** and **Deny** rules
- Rules are evaluated **in order** (with rule numbers)
- Useful for **centralized security control** and **bulk automation**

---

## 📊 Security Group vs NACL Comparison

| Feature                | Security Group (SG)           | Network ACL (NACL)              |
|------------------------|-------------------------------|---------------------------------|
| Scope                  | EC2 Instance Level            | Subnet Level                    |
| Rule Type              | Allow only                    | Allow and Deny                  |
| Stateful/Stateless     | Stateful                      | Stateless                       |
| Rule Evaluation        | All rules applied             | Rules evaluated in order        |
| Inbound Default        | Deny all                      | Allow all                       |
| Outbound Default       | Allow all (except Port 25)    | Allow all                       |
| Automation             | Instance-level only           | Applies to entire subnet        |

---

## 🤝 When to Use What?

- Use **Security Groups** for instance-specific, application-level control.
- Use **NACLs** for subnet-wide traffic filtering and an extra security layer.
- Use both **together** for maximum protection (defense-in-depth).

---

## 📦 Summary

- **Security Groups** protect EC2 instances, are stateful, and only allow rules.
- **NACLs** protect subnets, are stateless, and allow/deny traffic.
- Combine both for robust AWS network security.


