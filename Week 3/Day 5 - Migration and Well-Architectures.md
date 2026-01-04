# 📅 Week 3 · Day 5

## 🚚 AWS Migration & 🏗️ Well-Architected Solutions

---

## 🔹 Module 12: AWS Migration

---

## 🧭 Migration Phases

### 1️⃣ **Assess Phase**

* Assess company’s **readiness** for cloud adoption
* Identify:

  * Business aims
  * Goals
  * Technical & operational needs

---

### 2️⃣ **Mobilize Phase**

* Create a **migration plan**
* Address **gaps in readiness**
* Evaluate and finalize **migration strategy**

---

### 3️⃣ **Migrate & Modernize Phase**

* Applications are:

  * Migrated
  * Architected
  * Validated
* Continuous optimization after migration

---

## ☁️ AWS Cloud Adoption Framework (CAF)

* CAF provides **structured guidance** for:

  * Fast
  * Smooth
  * Low-risk migration to AWS

### 🔹 Perspectives of CAF

#### 🏢 Business Capability Focus

* **Business**
* **People**
* **Governance**

#### 🛠️ Technical Capability Focus

* **Platform**
* **Security**
* **Operations**

➡️ All CAF perspectives together form the **AWS CAF Action Plan**

---

## 🔁 7 R’s of Migration

1️⃣ **Rehost (Lift & Shift)**

* Minimal changes
* ~30% cost optimization
* Example: Move VMs *as-is*

---

2️⃣ **Relocate**

* Change location only
* On-premise VMs → Cloud
* No architectural changes

---

3️⃣ **Replatform (Lift-Tinker-Shift)**

* Small optimizations
* No code rewrite
* Example:

  * MySQL → Amazon RDS / Aurora

---

4️⃣ **Refactor / Re-architect**

* Major code changes
* Cloud-native design
* High effort, high benefit

---

5️⃣ **Repurchase**

* Drop & shop
* Change software vendor
* Start fresh on cloud (SaaS)

---

6️⃣ **Retain**

* Keep application as-is
* May be deprecated later, but **not now**

---

7️⃣ **Retire**

* End-of-life
* Remove unused architectures

---

## 🧰 AWS Services for Migration

### 🔹 AWS Application Discovery Service

* Explores existing IT setup
* Collects system data
* Helps plan migration to AWS

---

### 🔹 AWS Application Migration Service (MGN)

* Lift & shift workloads to AWS
* Replicates servers using VM-based replication
* Requires only small adjustments
* Enables **quick migration**

---

### 🔹 Migration Evaluator

* Analyzes current IT environment
* Provides:

  * Detailed cost estimates
  * Potential savings
  * Budget planning insights

---

## 📊 AWS Migration Hub

* Unified view of:

  * Migration tasks
  * Progress tracking
* Centralized dashboard for all migrations

---

## 🗄️ Database Migration

### 🔹 AWS Database Migration Service (DMS)

* Migrates databases to AWS
* Supports:

  * Homogeneous migration
  * Heterogeneous migration (DB → different engine)
* Uses VM-based replication
* Minimal downtime

---

### 🔹 AWS Schema Conversion Tool (SCT)

* Converts:

  * Source DB schema
  * To target DB schema format
* Used before DMS in heterogeneous migrations

---

## 📡 Data Transfer Methods

### 🔹 Online Data Transfer

#### ▪ AWS DataSync

* Automates & accelerates large-scale data transfers

#### ▪ AWS Transfer Family

* Managed data transfer using:

  * FTP
  * SFTP
  * FTPS

#### ▪ AWS Direct Connect

* Dedicated private network connection
* Between on-prem network & AWS VPC

---

### 🔹 Offline Data Transfer

#### ▪ AWS Snowball Edge

* Physical storage devices
* Used when internet connectivity is limited or unavailable

---

# 🏗️ Well-Architected Solutions

---

## ⭐ AWS Well-Architected Framework (WAF)

* Evaluates architectures
* Ensures alignment with **AWS best practices**
* Self-service evaluation tool

---

## 🏛️ WAF Pillars (ALL INCLUDED)

1️⃣ Operational Excellence
2️⃣ Security
3️⃣ Reliability
4️⃣ Performance Efficiency
5️⃣ Cost Optimization
6️⃣ Sustainability

---

## 🧑‍💻 Services for Development

* **AWS CodePipeline** – build, test, deploy
* **AWS X-Ray** – monitoring & debugging
* **AWS AppSync** – GraphQL APIs
* **AWS Amplify** – frontend & backend app development

---

## 🏢 Services for Business Applications

* **Amazon Connect** – AI-powered contact center
* **Amazon SES (Simple Email Service)** – email service

---

## 🖥️ Services for End-User Computing

* **Amazon AppStream 2.0** – application streaming
* **Amazon WorkSpaces** – fully managed virtual desktops
* **Amazon WorkSpaces Web** – lightweight secure browser

---

## 🌐 IoT Services

* **AWS IoT Core** – IoT device communication & management

---

## ⚙️ Backend Architecture (Serverless)

**Flow:**

```
Traffic → Amazon API Gateway → AWS Lambda → Amazon DynamoDB
```

* **AWS X-Ray**

  * Helps in request tracing
  * Debugging
  * Troubleshooting for developers

---

## 📩 Contact-Us Architecture (Serverless Example)

**Flow:**

```
Website (Amazon S3)
→ Contact Form
→ API Gateway
→ AWS Lambda
→ Amazon SES
→ Email to Owner
```

---

## 🎯 Key Takeaways

* Migration follows **Assess → Mobilize → Migrate & Modernize**
* CAF gives **structured decision-making**
* 7 R’s define **migration strategy**
* AWS provides tools for **apps, databases & data**
* WAF ensures **secure, scalable & cost-efficient architectures**

