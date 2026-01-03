# Notes - Day 3 (Global Infrastructure, Networking and Storage)

# 🌎 **Going Global**

### **🌐 Edge Locations**

Edge locations are like **mini-storehouses** placed closer to customers.

They offer:

- ⚡ **Fast & localized delivery**
- 📦 Serving the **most frequently accessed content**
- 🧠 They cache content for quick access

Edge locations also support:

- 🚀 **AWS Global Accelerator**
- 📡 **Amazon Route 53 (DNS)**

---

# 🗺️ **Choosing an AWS Region**

Choosing a Region is like choosing the **best city** to open your headquarters.

Consider:

- 🛡️ **Compliance** → Legal + regulatory requirements
- 📍 **Proximity** → Closer region = lower latency
- 🧩 **Feature availability** → Some services are region-specific
- 💰 **Pricing** → Prices differ by region

---

# 🏛️ **AWS Global Infrastructure**

AWS runs on a massive global backbone of:

- 🌍 **Regions**
- 🏢 **Availability Zones**
- 🚀 **Edge locations**

---

# 🛡️ **Building Redundant Architectures**

Redundancy = ensuring your system **doesn’t fail**, even if something goes wrong.

Two key strategies:

1️⃣ **Deploying across discrete AZs**

- Acts as a *backup* plan within a region
    
    2️⃣ **Deploying across multiple regions**
    
- Protects you from an entire region outage

Like keeping branches of your company in different cities **and** different countries.

---

# 🚀 **Amazon CloudFront**

CloudFront = AWS’s **Content Delivery Network (CDN)**.

- Distributes content **as close to users as possible**
- Uses edge locations for speed
- Ideal for websites, videos, static content, APIs

Think of CloudFront as having **multiple mini-warehouses** placed around the world so customers get faster deliveries.

---

# 🧱 **Infrastructure as Code (IaC)**

### **💡 What is IaC?**

If your cloud architecture is like a large building,

**IaC is the blueprint** that defines how it should be constructed.

### **Why IaC?**

When you have:

- many components
- many services
- many AWS accounts
- deployments across multiple regions

…manually configuring everything becomes messy.

So we use **Automation (IaC)** to manage everything **programmatically**.

---

# 🏗️ **AWS CloudFormation**

CloudFormation is AWS’s **Infrastructure as Code** service.

- You write a template (YAML/JSON)
- AWS automatically builds the resources
- Ensures predictable, repeatable, error-free deployments

Think of CloudFormation as telling AWS:

> “Here’s the blueprint. Build everything exactly like this.”
> 

---

# 📌 **Quick Summary Sheet (Perfect for Revision)**

| Topic | Key Idea |
| --- | --- |
| Edge Locations | Fast, local content delivery via caching |
| Choosing a Region | Compliance, proximity, features, pricing |
| Redundancy | Deploy across AZs + Regions |
| CloudFront | CDN using edge locations |
| IaC | Blueprint for AWS infrastructure |
| CloudFormation | AWS tool to automate infrastructure |