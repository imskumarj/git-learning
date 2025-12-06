# Notes - Day 1 (AWS Introduction)

# ☁ **1. What is Cloud Computing?**

### **Simple Definition**

Cloud computing is the **on-demand delivery** of IT resources like servers, storage, databases, networking, and software **over the internet**, with **pay-as-you-go pricing**.

### **Real-World Analogy: Coffee Shop**

Think of cloud computing like running a chain of coffee shops:

- Instead of buying a huge expensive coffee machine for each shop (your own servers),
    
    you **rent a machine only when needed** from a central supplier (cloud provider).
    
- You don’t maintain or repair the machines — the supplier does it (managed service).
- You can scale: During mornings (peak), rent more machines; during evenings (low), rent fewer.

### **Key Characteristics**

- **On-demand**: Use anytime.
- **Pay-as-you-go**: Pay only for what you use.
- **Scalable**: Add/remove resources instantly.
- **Managed**: Provider handles hardware, security patches, maintenance.

---

# 🌍 **2. AWS Global Infrastructure**

AWS infrastructure is like a **global chain of coffee shops**, organized in layers.

## **a) Regions**

- A Region = **a geographical area** (e.g., Mumbai, Singapore, Ohio).
- Each region contains multiple isolated data centers.
- You choose a Region based on:
    - **Latency** (closest region gives fastest service)
    - **Compliance** (data residency laws)
    - **Cost**

☕ **Coffee Analogy**

A "Region" is like selecting a **country** where you want to open a branch of your coffee shop.

Example:

- India region → Mumbai
- US region → Northern Virginia

## **b) Availability Zones (AZs)**

- Each Region has **2–6 Availability Zones**.
- An AZ = **one or more data centers**, isolated from failures but connected with high-speed networks.
- Using multiple AZs makes your applications **fault tolerant**.

☕ **Coffee Analogy**

Inside a country (Region), you open multiple branches (AZs).

If one branch catches fire or loses electricity, the other branches continue working.

**Example:**

Mumbai Region

- AZ 1 → Shop in Andheri
- AZ 2 → Shop in Navi Mumbai
- AZ 3 → Shop in Thane

If the Andheri shop shuts down, your customers are served by Navi Mumbai or Thane.

---

# ⭐ **3. Benefits of AWS Cloud**

Using AWS is like using a well-established **franchise** instead of opening your own independent coffee shop.

### **1. Cost Savings**

No upfront investment (CAPEX).

Pay only for the cup of coffee you serve (actual usage).

### **2. Scalability**

Easily increase or decrease resources.

Like adding extra baristas during rush hour and letting them go when it's calm.

### **3. Reliability**

Multiple branches (AZs) ensure the business runs even if one fails.

### **4. Security**

AWS secures the underlying infrastructure — like having a central security team that protects all your shops.

### **5. Global Reach**

You can open a store in any country instantly by launching services in various AWS Regions.

### **6. Speed & Agility**

Deploy servers in minutes.

Like setting up a portable coffee counter instantly anywhere.

### **7. Managed Services**

AWS handles databases, storage, machine learning, backups, monitoring.

Like hiring specialists for cleaning, accounting, logistics, so you focus only on selling coffee.

---

# 🎁 **4. AWS Free Tier Overview**

AWS gives you a **free trial** to explore their services without cost.

## **Types of Free Tier**

### **1. 12-Month Free Tier (after creating account)**

- Examples:
    - **EC2 t2.micro / t3.micro**: 750 hours/month
    - **S3 Storage**: 5 GB
    - **RDS**: 750 hours of db.t2.micro

☕ Analogy

Like getting **free coffee beans & machine time** for a year to learn how to run your shop.

---

### **2. Always Free**

These services remain free even after 12 months (with limits):

- **AWS Lambda**: 1M free requests/month
- **DynamoDB**: 25GB storage
- **SNS** and **SQS**: free limits

☕ Analogy

Like having **free water** or **napkins** forever — small but essential.

---

### **3. Trial Offers**

Short-term (typically 30-day) free access to premium AWS services.

☕ Analogy

Like getting a **1-month free trial** of a new espresso machine.

---

# 🔥 **Fully Combined Coffee-Shop Example (Quick Revision)**

**Imagine you run “CloudCoffee,” a global chain.**

- Instead of buying machines for each shop, you **rent coffee machines on-demand** → *Cloud computing*
- You choose which **country** to open your shop in → *AWS Region*
- Inside the country, you choose **multiple branches** → *Availability Zones*
- If one branch shuts down, others take over → *High availability*
- AWS maintains machines, security, electricity → *Managed services*
- You only pay for each cup you sell → *Pay-as-you-go*
- AWS gives you free beans & machine time for a year to try things → *AWS Free Tier*