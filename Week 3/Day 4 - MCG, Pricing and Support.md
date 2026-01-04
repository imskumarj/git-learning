# 📊 Week 3 · Day 4

## Monitoring, Compliance & Governance in AWS Cloud

--- 

# 🧠 Big Picture First

Think of AWS like a **large organization**:

* **Monitoring** → Are systems healthy right now?
* **Compliance** → Are we following rules & regulations?
* **Governance** → Are we managing everything in a controlled, standardized way?

Together they ensure:

> **Visibility → Control → Trust**

---

## 🔍 PART 1: Monitoring (Module 10 – MCG)

### What is Monitoring?

Monitoring means:

* Observing systems
* Collecting metrics & logs
* Using data to make **informed decisions**

🧠 Analogy:
A **hospital ICU dashboard** showing heartbeat, oxygen & alerts.

---

## ☁️ Amazon CloudWatch (Core Monitoring Service)

### What CloudWatch Does

* Central monitoring service for AWS
* Tracks health of resources & applications

### CloudWatch Components

#### 1️⃣ CloudWatch Metrics

* Tracks performance numbers:

  * CPU usage
  * Memory
  * Network traffic
* Metrics are **numeric values over time**

🧠 Example:
CPU usage = 75%

---

#### 2️⃣ CloudWatch Alarms

* Trigger alerts when thresholds are crossed
* Can notify via SNS or auto-scale resources

🧠 Example:
“Alert me if CPU > 80% for 5 minutes”

---

#### 3️⃣ CloudWatch Dashboards

* Visual panels showing metrics
* Single view of system health

🧠 Analogy:
A **car dashboard** with speed, fuel & warning lights.

---

#### 4️⃣ CloudWatch Logs

* Collects & stores logs from:

  * EC2
  * Lambda
  * Applications
* Used for:

  * Monitoring
  * Debugging
  * Analysis

---

### Benefits of CloudWatch

* Centralized metrics
* Faster troubleshooting
* Improved MTTR (Mean Time To Recovery)
* Cost & performance optimization
* Better application insights

---

## 🪵 Amazon CloudTrail (Auditing Service)

### What CloudTrail Does

* Logs **every AWS API call**
* Tracks:

  * Who did what
  * From where
  * When

🧠 Analogy:
CCTV camera for your AWS account 🎥

---

### Key Features

* Records management & data events
* Provides **audit trails**
* Ensures integrity of logs
* Detects unauthorized activity

---

### Benefits of CloudTrail

* Save logs indefinitely
* Store logs securely in S3
* Tamper-proof evidence
* Essential for compliance & investigations

---

## 🧾 PART 2: Compliance (Following the Rules)

### What is Compliance?

Compliance ensures AWS resources follow:

* Legal rules
* Industry standards
* Internal company policies

🧠 Analogy:
Government inspections for a factory.

---

### Why Compliance Matters

* Healthcare → HIPAA
* European customers → GDPR
* Financial services → strict audits

Failure = legal + trust issues 🚨

---

## 🏛️ AWS Compliance Center

### What It Provides

* Access to:

  * Compliance reports
  * Audit documentation
* Shows how AWS meets global standards

🧠 Think of it as:
AWS’s **compliance document library**

---

## 🔍 AWS Artifact

### What is AWS Artifact?

* Self-service portal
* Provides:

  * Compliance reports
  * Audit reports
* Used by:

  * 3rd-party auditors
  * Internal compliance teams

🧠 Analogy:
Downloading official certificates from a government portal.

---

## ⚙️ AWS Config (Configuration Compliance)

### What AWS Config Does

* Continuously monitors AWS resources
* Records:

  * Resource configurations
  * Configuration changes
* Evaluates resources against rules

---

### AWS Config Key Capabilities

* Track changes over time
* Detect non-compliant resources
* Generate compliance reports
* Audit historical configurations

🧠 Analogy:
A **security inspector** checking if rules are followed at all times.

---

## 📜 AWS Audit Manager

### What Audit Manager Does

* Automatically collects audit evidence
* Reduces manual audit effort
* Helps prepare for audits faster

### Features

* Access policies
* Managed services integration
* Pre-built compliance frameworks
* Automated evidence collection

🧠 Analogy:
An **assistant** that prepares audit files for you.

---

## 🏢 PART 3: Governance (Managing at Scale)

### What is Governance?

Governance ensures:

* Controlled usage of AWS
* Standardized processes
* Centralized management

🧠 Analogy:
Company rules + hierarchy + approvals.

---

## 🧩 AWS Organizations

### What AWS Organizations Does

* Manage **multiple AWS accounts**
* Centralized billing
* Policy enforcement across accounts

---

### Key Components

#### 🔹 Management Account

* Root of the organization
* Controls policies

#### 🔹 Member Accounts

* Individual AWS accounts
* Used by teams/projects

---

### Benefits

* Centralized control
* Better security
* Simplified billing
* Scalable governance

---

## 🛡️ Service Control Policies (SCPs)

### What are SCPs?

* Organization-level policies
* Define **maximum permissions**
* Apply to:

  * OUs
  * Accounts

🧠 Important:
SCPs do NOT grant access
They only **limit what’s possible**

---

## 🏢 Organizational Units (OU)

* Logical grouping of AWS accounts
* Policies applied to entire OU

🧠 Analogy:
Departments inside a company (HR, Tech, Finance)

---

## 🧭 PART 4: Governance & Compliance Flow (Mental Model)

```
Monitoring → Auditing → Compliance → Governance
```

Or simply:

* CloudWatch → Health
* CloudTrail → Activity
* AWS Config → Configuration
* Audit Manager → Evidence
* Organizations + SCPs → Control

---

## 🧠 One-Page Revision Summary

* **CloudWatch** → Metrics, alarms, logs, dashboards
* **CloudTrail** → API call auditing
* **Compliance Center** → Standards & reports
* **AWS Artifact** → Audit documents
* **AWS Config** → Config tracking & compliance checks
* **Audit Manager** → Automated audit evidence
* **AWS Organizations** → Multi-account governance
* **SCPs** → Permission boundaries
* **OUs** → Account grouping

---

## 🎯 Final Analogy (Easy Recall)

AWS Account = City

* CloudWatch = Traffic cameras
* CloudTrail = Police records
* AWS Config = Building inspector
* Audit Manager = Audit assistant
* Organizations = City administration
* SCPs = City laws

---

## AWS Pricing, Marketplace, Partners & Cost Optimization

---

## 🧾 AWS Pricing – Core Model

### 🔹 Pay-As-You-Go

* Pay only for what you **use**
* No upfront investment
* No long-term contracts

🧠 **Analogy**:
Like a taxi meter — pay for distance travelled, not for owning the car.

---

### 🔹 Save When You Commit

* Committing to usage → **lower cost**
* Used via Reserved/Savings plans

---

## 🧮 Main Drivers of AWS Pricing

AWS cost mainly depends on:

### 🖥️ Compute

* EC2
* Lambda
* Containers

### 💾 Storage

* S3
* EBS
* EFS

### 🌐 Outbound Data Transfer

* Data going **out of AWS**
* Inbound data usually free

🧠 **Analogy**:
Incoming calls free, outgoing calls charged.

---

## 🧾 AWS Billing Models

### 🔹 Single Account Billing

* All services billed under **one AWS account**

---

### 🔹 Consolidated Billing (AWS Organizations)

* One **management account**
* Multiple **member accounts**
* Single combined bill

🧠 **Benefits**:

* Centralized cost tracking
* Volume discounts
* Easier financial control

🧠 **Analogy**:
Family mobile plan with one bill.

---

## 📊 AWS Budgets

### What AWS Budgets Does

* Track spending & usage
* Create **custom budgets**
* Alerts before overspending

🧠 Example:

> Alert me if monthly spend crosses ₹10,000

🧠 **Analogy**:
Expense tracking app with spending alerts.

---

# 🏪 AWS Marketplace 

### What is AWS Marketplace?

* **Curated digital catalog**
* Find, test, buy, deploy & manage **3rd-party software**
* Software runs directly in your AWS infrastructure

### What You Can Find:

* Security tools
* Databases
* Monitoring tools
* DevOps software

🧠 **Analogy**:
Play Store / App Store — but for AWS infrastructure software.

---

# 🤝 AWS Partner Network (APN) 

### What is APN?

* Global partner program
* Businesses that:

  * Use AWS
  * Build solutions
  * Provide services to customers

### APN Partners Help With:

* Architecture design
* Migration
* Optimization
* Consulting

🧠 **Analogy**:
Authorized service centers for AWS cloud.

---

# 📉 Cost Optimization 

Cost optimization = **reducing AWS bill without affecting performance**

---

## 🔹 Rightsizing

* Analyze & adjust resources to match workload
* Avoid over-provisioning

### Tool:

* **AWS Compute Optimizer**

  * Identifies over-provisioned EC2 instances

🧠 **Analogy**:
Buying shoes of correct size instead of oversized ones.

---

## 🔹 Spot Instances

* Use spare AWS capacity
* **Up to 90% discount**
* Best for:

  * Batch jobs
  * Non-critical workloads

🧠 **Trade-off**:
Can be interrupted by AWS.

---

## 🔹 Auto Scaling

* Automatically scale resources up/down
* Prevent over-usage & under-usage

🧠 **Analogy**:
Automatic water tank motor — runs only when needed.

---

## 🔹 Lifecycle Policies

* Automatically move data between storage tiers
* Example:
  S3 → Standard → IA → Glacier

🧠 **Analogy**:
Moving old files from cupboard to storage room.

---

## 🔹 Data Compression

* Reduce data size
* Less storage cost
* Faster data transfer

---

## 🔹 VPC Endpoints

* Access AWS services **without internet**
* Reduces:

  * Data transfer cost
  * Security risk

🧠 **Analogy**:
Private road instead of public highway.

---

# 🆘 AWS Support Plans

---

## 🟢 Basic Support (Free)

* Available to all users
* Documentation
* Whitepapers
* Forums
* No technical support

---

## 🔵 Developer Support

* For developers
* Access to AWS engineers
* Faster response than Basic

---

## 🟠 Business Support

* For production workloads
* Email support
* Faster response times
* Guidance during system impairment

---

## 🔴 Enterprise Support

* Mission-critical workloads
* 24/7 phone & chat
* Dedicated **Technical Account Manager (TAM)**

🧠 **Analogy**:
Personal doctor + emergency hotline.

---

# 🧠 One-Glance Memory Map

* **Pricing** → Pay for usage
* **Marketplace** → Buy ready software
* **APN** → AWS solution partners
* **Cost Optimization** → Spend smart
* **Support Plans** → Reduce operational risk

---

## ✅ Final Confirmation

✔ AWS Marketplace — covered
✔ AWS Partner Network — covered
✔ Cost Optimization — fully covered
✔ Pricing, Billing, Budgets, Support — intact
✔ Nothing missed from notes

