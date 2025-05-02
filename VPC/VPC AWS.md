
![ChatGPT Image May 2, 2025, 05_05_35 PM](https://github.com/user-attachments/assets/10ca611c-1173-4634-8c46-319c6aa327cb)


## Scenario: Hosting a Web Application on AWS Securely

Imagine **TCS** is hosting a project on AWS, and a DevOps engineer is setting up the infrastructure. Here's how it works

### 1.AWS DataCenter and VPC

- AWS owns datacenters around the world in different regions(e.g,Mumbai,Ohio,Frankfurt)
- VPC (virtual Private Cloud) is like a virtual network(just like a gated community) that isolates resources and provides security within AWS

**VPC**: A VPC is a logically isolated section of AWS where you can launch AWS resources in a virtual network that you define.

### 2.Defining the Size of a VPC
- The size is defined using an IP address range, for example:
   '172.16.0.0/16 → Provides 65,536 IP addresses'
**CIDR(classless Inter-domain routing)** - The /16 indicates how many IPs are available.

### 3.Creating Subnets
- A subnet is a smaller block inside the VPC (just like a plot inside a gated community).
- For example

Subnet 1: 172.16.1.0/24 → 256 IPs (used for payment app)
Subnet 2: 172.16.2.0/24 → 256 IPs (used for transaction app)
Subnet 3: 172.16.3.0/24 → 256 IPs (used for analytics)

**Subnet** -  A subdivision of the VPC network for organizing and isolating resources.

### 4.Public vs Private Subnets
- Public Subnet: Can connect to the internet (e.g., load balancer lives here).
- Private Subnet: Cannot directly access the internet (e.g., EC2 instances running applications are here).

### 5.Internet Gateway(IGW)
- Attached to the VPC to allow internet access.
- Only public subnets can route through the Internet Gateway.

  A **gateway** that allows communication between instances in your VPC and the internet.

### 6. Load Balancer in the Public Subnet
- The Load Balancer (LB) receives external requests and distributes traffic across EC2 instances in private subnets.
- **Load Balancer**: A service that automatically distributes incoming application traffic across multiple targets (EC2, containers, etc.).

### Route Table
- Tells AWS how traffic should flow between subnets and other networks.
- **Route Table**: set of rules(routes) that determine where network traffic is directed.

### Security Group
- Acts as a firewall. It controls who can access the EC2 instances(based on port numbers, protocols, and source IPs)
- **Security Group** - Virtual Firewall for your instance to control inbound and outbound traffic



# AWS Networking Components

| **Component**        | **Purpose**                                                |
|----------------------|------------------------------------------------------------|
| **VPC**              | Private, isolated virtual network in AWS                   |
| **Subnet**           | Smaller networks inside a VPC                             |
| **Internet Gateway** | Enables internet access for public subnets                |
| **Public Subnet**    | Subnet that can route to the internet                      |
| **Private Subnet**   | Subnet that cannot directly access the internet            |
| **Route Table**      | Routing rules for network traffic                          |
| **Load Balancer**    | Distributes incoming traffic to multiple targets           |
| **Security Group**   | Controls access to AWS resources                           |




  









