## 🌐 Week 2 – Day 4: AWS Networking

### 🧩 Amazon Virtual Private Cloud (VPC)

An **Amazon VPC** allows us to provision a **logically isolated section of the AWS Cloud** where we can launch AWS resources in a network we control.

Think of a VPC as your **private office space inside AWS** — isolated from others but fully customizable.

Inside a VPC, we can host:

* **Public resources** → have internet access
* **Private resources** → no direct internet access

---

### ☕ Coffee Shop Analogy (VPC)

* **Customer** → Internet user
* **Cashier** → Public resource (accessible from outside)
* **Barista** → Private resource (internal only)

Flow:
Customer → Cashier (Public VPC) → Barista (Private VPC)

This keeps internal services secure while still serving users.

---

## 🧱 Subnets

Subnets are used to **organize resources inside a VPC**.

Important points:

* Each subnet belongs to **one Availability Zone**
* Subnets can be:

  * **Public subnet** (internet-facing)
  * **Private subnet** (internal only)

---

### 🌍 Public Subnet

* Connected to an **Internet Gateway**
* Used for:

  * Web servers (EC2)
  * Load balancers

### 🔒 Private Subnet

* No direct internet access
* Used for:

  * Databases
  * Backend services

---

### 🗺️ VPC Architecture (Conceptual)

* Region

  * VPC

    * AZ-A

      * Public Subnet → EC2
      * Private Subnet → DB
    * AZ-B

      * Public Subnet → EC2
      * Private Subnet → DB

Internet traffic flows through an **Internet Gateway** to public subnets, while private subnets remain protected.

---

## 🔐 VPN (Virtual Private Network)

VPN is used when **secure communication is required**.

Key benefits:

* Secure connection 🔐
* Flexible
* Remote access
* Cost-effective compared to dedicated connections

VPN creates a **secure tunnel** between your local environment and AWS.

---

## 🔗 AWS Direct Connect

AWS Direct Connect establishes a **dedicated private connection** between your on-premises data center and AWS.

Used when:

* High bandwidth is needed
* Low latency is critical
* Large or frequent data transfers occur

Benefits:

* High performance 🚀
* Low latency
* Secure & reliable
* Consistent network behavior

---

### 🌉 Ways to Connect to AWS Cloud

1. AWS Client VPN
2. AWS Site-to-Site VPN
3. AWS Direct Connect
4. Private peering / networking options

---

## 🌍 Global Networking

### 🌐 Amazon Route 53 (DNS)

Route 53 is AWS’s **DNS service** used for traffic routing.

Routing policies include:

* Latency-based routing
* Geolocation routing
* Weighted routing
* Simple round-robin routing

Route 53 decides **where user requests should go**.

---

### 🚀 Amazon CloudFront (CDN)

CloudFront is AWS’s **Content Delivery Network**.

Key points:

* Uses **edge locations**
* Caches frequently accessed content
* Reduces latency
* Improves global performance

Flow:
User → Route 53 → CloudFront (Edge) → AWS Region

---

## 🧠 Global Architecture Components

### Edge Locations

* Store cached content closer to users
* Enable faster content delivery

### AWS Global Accelerator

* Improves availability
* Routes traffic through AWS’s global network

---

## 🛡️ Network Security

### Network ACL (NACL)

* Works at **subnet level**
* Stateless
* Controls inbound and outbound traffic

### Security Groups

* Works at **instance level**
* Stateful
* Acts like a firewall for EC2 instances

Easy way to remember:

* **NACL** → Subnet gatekeeper
* **Security Group** → Instance bodyguard

---

## 🗺️ End-to-End Traffic Flow (High Level)

Client
→ Route 53 (DNS)
→ CloudFront (Edge location)
→ Internet Gateway
→ Public Subnet (EC2)
→ Private Subnet (Database)

---

## 📌 Quick Revision Summary

* VPC provides network isolation in AWS
* Subnets divide a VPC by AZ and accessibility
* Public subnets face the internet
* Private subnets protect internal resources
* VPN enables secure tunneling
* Direct Connect offers high-performance private connectivity
* Route 53 manages traffic routing
* CloudFront accelerates global content delivery

---

## 🎯 Exam / Interview One-Liners

* “A VPC is a logically isolated network in AWS.”
* “Subnets are AZ-specific.”
* “Security Groups are stateful; NACLs are stateless.”
* “CloudFront reduces latency using edge caching.”
* “Direct Connect provides predictable network performance.”
