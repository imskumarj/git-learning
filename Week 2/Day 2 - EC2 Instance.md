# Notes - Day 2 (EC2 Instance)

# **☁️ EC2**

### **Amazon EC2 (Elastic Compute Cloud)**

EC2 is like renting a super-flexible computer in the cloud.

- 🔄 High flexibility
- 💸 Cost-effective
- ⚡ Quick to launch

### **Multitenancy**

- Multiple virtual machines share the same underlying hardware — like roommates sharing a large apartment with separate rooms.

### **EC2 Configurations**

- 🪟 Windows
- 🐧 Linux
- 🏢 Internal business apps, etc.

### **Compute as a Service (CaaS)**

Using computing power as a pay-as-you-go service.

---

# **🖥️ Types of EC2 Instances**

Each EC2 instance belongs to an **instance family**, like categories of vehicles: cars, trucks, bikes — each built for a purpose.

### **Instance Families**

- General Purpose 🚗
- Compute Optimized 🚀
- Memory Optimized 🧠
- Accelerated Computing ⚡
- Storage Optimized 📦

---

# **🚗 General Purpose**

Balanced machines for everyday workloads:

- Balanced resources ⚖️
- Diverse workloads
- Web servers 🌐
- Code repositories 💾

---

# **🚀 Compute Optimized**

Best for raw processing power:

- Compute-intensive tasks
- Gaming servers 🎮
- High-Performance Computing (HPC)
- Scientific modelling 🔬

---

# **🧠 Memory Optimized**

Designed for huge memory needs:

- Memory-heavy workloads (analytics, big databases, caching systems)

---

# **⚡ Accelerated Computing**

Uses GPUs / specialized hardware:

- Floating-point calculations
- Graphics processing 🎨
- Data pattern matching 🔍

---

# **📦 Storage Optimized**

- High performance for locally stored data — great for large databases and data warehouses.

---

# **🛠️ AWS: Provisioning Resources**

On AWS, **everything is done via API calls** — like sending commands to a smart robot.

### **Ways to Interact with AWS**

- AWS Management Console 🖥️
- AWS CLI 💻
- AWS SDK 🧩

---

# **📀 AWS AMI**

AMI = Pre-configured OS + software template

Like a ready-made recipe to bake the same server again and again.

---

# **💰 EC2 Pricing Models**

Choose based on flexibility and cost:

- On-Demand ⏳
- Saving Plans 💸
- Reserved Instances 🔒
- Spot Instances ⚡
- Dedicated Hosts 🏢

---

# **📈 Scaling Amazon EC2**

### **Deploy EC2 across multiple AZs**

Like opening same shops in different locations for reliability.

### **Scalability**

- Ability of your system to grow over time.

### **Elasticity**

- Automatically adjusting resources based on load — like a rubber band expanding and shrinking.

### **Scale Out**

- ➕ Add more machines (horizontal scaling)

### **Scale Up**

- 🔼 Add more power to the existing machine (vertical scaling)

### **AWS Auto-Scaling**

- Adds or removes instances based on demand 📊
- Ensures efficiency and saves cost

### **Monitoring**

- Use **Amazon CloudWatch** to watch instance metrics 👀

---

# **⚖️ Traffic & Load Balancer**

### **Traffic Issues**

Uneven request load on one instance can cause delays — like everyone standing at one counter in a mall.

### **Load Balancer**

Distributes incoming traffic evenly:

- Takes the request
- Sends it to a healthy instance
- Prevents overload

### **Elastic Load Balancing (ELB)**

Manages the entire load balancing operation.

**Frontend → ELB → Backend**

---

# **📬 Messaging & Queueing**

### The Problem:

Busy servers might drop requests or get out of sync.

### The Solution:

Use a **queue** — like a waiting line where requests wait their turn.

### **Tightly Coupled Architecture**

- Direct request flow between components
- If one breaks, everything breaks

### **Loosely Coupled Architecture**

- Component A sends request to a queue
- Queue forwards to component B
- If B is down, queue stores the request
- More reliable and flexible 🔄

---

# **🛎️ AWS Messaging Services**

### **Amazon SQS (Simple Queue Service)**

- Send message
- Store message
- Receive message

### **Amazon SNS (Simple Notification Service)**

- Sends notifications 📢
- Does **not** wait for a response

### **Payload**

- The data inside the message ✉️

### **EventBridge**

- Serverless event-based communication service ⚡
- Helps connect different systems using events

# 🌟 **MODULE 3 — Containers & Serverless Computing**

---

# 🐳 **1. Containers**

### **💡 What are Containers?**

Containers package **everything your code needs**

(⚙️ configuration, 📦 dependencies, 🔧 runtime)

into one **portable unit** — like packing your whole kitchen into a single lunchbox and being able to cook anywhere.

---

### **🛠 How Containers Work**

- Containerization services manage **isolation** between applications.
- Ensures consistent behavior everywhere — laptop, server, or cloud.

---

# 🏗️ **2. Container Services in AWS**

## **1) Amazon Elastic Container Service (ECS)**

A fully managed container service.

- Handles orchestration
- Defines how containers should run
- Great for teams that want speed + simplicity

---

## **2) Amazon Elastic Kubernetes Service (EKS)**

Managed **Kubernetes** on AWS.

- 📏 Standardized container platform
- ⚙️ More control, more flexibility
- Best for enterprises using Kubernetes already

---

## **3) Amazon Elastic Container Registry (ECR)**

A fully managed **Docker container registry**.

- Store & manage container images
- Secure and scalable

---

# 🧭 **3. How to Use Containers on AWS**

### **A) Upload Container Image → ECR**

You first send your container images to ECR.

### **B) Choose Orchestration Service**

Depending on your needs:

- ECS 🟦 (fully managed)
- EKS 🟩 (Kubernetes)
- EC2 instances 🖥️ (self-managed)
- AWS Fargate 🚀 (serverless containers)

### **C) Select Compute Platform for Running Containers**

- **AWS EC2** → You manage servers
- **AWS Fargate** → No servers, AWS handles everything

Fargate = “Serverless containers” → Just run your container, no servers to manage.

---

# ✨ **4. Additional AWS Services**

## **1) AWS Elastic Beanstalk**

A **PaaS (Platform as a Service)** for deploying web applications.

- Automated deployment ⚙️
- Simplified management
- Great visibility 💡
- Control over configuration

Best for: Developers who want easy deployment without deep infra management.

---

## **2) AWS Batch**

Best for **heavy-duty batch workloads**.

- Schedules batch jobs
- Handles scaling
- Manages compute environment
- Ideal for: scientific computing, large data processing 🧪

---

# 🌀 **Intro to Serverless Computing**

### **🧩 Managed vs Unmanaged**

### **Unmanaged Services**

(You customize everything + maintain the underlying infrastructure)

Examples:

- EC2
- ELB
- SQS
- SNS

You are responsible for scaling, patches, OS, runtime, everything.

---

### **Managed Services**

AWS takes care of most parts for you.

Examples:

- DynamoDB
- Lambda
- Fargate

### **🌈 Essence of Serverless**

> “You don’t manage servers; you just run functions.”
> 

Serverless =

- No provisioning
- No scaling headaches
- You focus only on **code**, not infrastructure.

---

# ⚡ **AWS Lambda**

### **What is AWS Lambda?**

Lambda is a **serverless compute service**.

You upload your function → AWS runs it when triggered.

No servers, no scaling management, no idle cost.

```
Triggers → Lambda Function → Output
```

### **🕒 Max Execution Time**

⏳ **15 minutes per Lambda function**

---

### **Uses of Lambda**

1. Social app notifications
2. On-demand file/image processing 📸
3. Personalized content delivery 🎯
4. Real-time event handling (IoT, APIs, etc.)

---

# 🔁 **Lambda Demonstration Flow**

1. You create a function (code)
2. Upload packaged file to AWS
3. Lambda executes it whenever triggered
4. AWS handles scaling seamlessly

---

# 🚀 **Amazon Lightsail**

A simpler alternative to EC2 — a beginner-friendly VPS.

### **Lightsail Features**

- 🎯 Simple
- 💸 Cost-effective
- 🧰 Managed infrastructure
- Ideal for beginners, small apps & websites

---

# 🏢 **Amazon Outposts (Hybrid Cloud Solution)**

For organizations needing:

- Consistent environments
- Low latency
- Local data residency

Brings AWS hardware + services **on-premises**.

---

# 🎯 **Quick High-Level Summary**

### **Containers**

- Packaged applications → portable
- ECS = Simple
- EKS = Kubernetes-intensive
- ECR = Stores container images
- Fargate = Serverless containers

### **Serverless**

- Pay only when your code runs
- No servers to manage
- Lambda = Run functions without servers

### **Other Services**

- Elastic Beanstalk → Easy deployment
- AWS Batch → Heavy batch workloads
- Lightsail → Simple VPS
- Outposts → AWS hybrid on-prem