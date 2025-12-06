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