# Topics to be covered
- What is Cloud?

  About 10–20 years ago, companies used to buy physical servers to run their applications. Just like how you install software on your laptop, 
  companies would install applications on these servers. They’d buy the servers from companies like IBM or HP, set them up in one place called a   data center, and connect everything with proper wiring, networking, and cooling systems.
  But there was a problem. These servers were expensive and powerful — for example, a server might have 100 GB of RAM and 100 CPUs. If you only     needed 1 GB of RAM and 1 CPU for an application, the rest of the resources would go to waste.

  To fix this, the concept of virtualization was introduced.
  Virtualization means creating virtual servers on top of a physical server. Instead of using one server for one application, 
  you can create multiple virtual machines (VMs) on the same physical server and run different applications on each one. 
  This saves cost and makes better use of server resources.

  How Does This Lead to Cloud?

  Once virtualization became popular, it was possible to create virtual servers remotely. For example, if a developer in India requests a       
  server, a system administrator in the U.S. can create  a virtual machine and share access — the developer doesn’t need to know where the   
  server physically exists.
  
  This idea of accessing servers and resources over the internet, without worrying about where they are, is called Cloud.

When companies build and manage their own virtualized setup internally, it’s called a Private Cloud.

- Public vs Private Cloud
A private cloud is when a company builds and manages its cloud setup within the organization. This means:
* Only people within that company can access the servers.
* No other company or outsider can request resources from this setup.
* Everything — servers, storage, networking — is owned and controlled by the organization.
  
Companies that handle sensitive data, like banks or government agencies, often prefer private cloud for security and control.
* What is the public Cloud?
  Big tech companies like Amazon (AWS), Microsoft (Azure), and Google (GCP) saw an opportunity. Instead of every company building its own data center, these cloud providers:

* Bought and maintained servers in multiple locations worldwide.
* Made these resources available to anyone with an account.
* Allow users to create virtual machines, storage, and other services on demand.

This is called a public cloud because anyone (from any organization) can use it. You can choose where you want your virtual server (e.g., in the US or India), but you don't manage the hardware — the cloud provider does.

### Key Differences Between Private Cloud and Public Cloud

| **Feature**     | **Private Cloud**                                 | **Public Cloud**                                      |
|-----------------|---------------------------------------------------|-------------------------------------------------------|
| **Ownership**   | Managed by your organization                      | Managed by cloud providers like AWS, Azure            |
| **Accessibility** | Only for internal use                             | Anyone with an account can access                     |
| **Setup Cost**  | High (buying servers, setup, staff)               | Low (pay-as-you-go)                                   |
| **Control**     | Full control over everything                      | Limited control (provider manages hardware)           |
| **Examples**    | Using VMware, OpenStack internally                | Using AWS EC2, Azure VM, GCP Compute Engine           |



- Why is the public cloud so popular?
- Why AWS?
- What are the trends of people moving back to the private cloud?
- Create an AWS account and get started
