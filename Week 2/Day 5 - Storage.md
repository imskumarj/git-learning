# 📦 Week 2 – Day 5: AWS Storage

AWS provides multiple storage services, each designed for different performance, scalability, durability, and access requirements. Choosing the right storage type is critical for building efficient cloud architectures.

---

## 1️⃣ AWS Storage Categories

AWS storage is broadly divided into:

* **Block Storage**
* **Object Storage**
* **File Storage**
* **Hybrid Storage**

Each category serves a different purpose based on how applications access data.

---

## 2️⃣ Block Storage

Block storage divides data into fixed-size blocks and stores them as separate pieces.
It is best suited for applications that require **frequent read/write operations**.

### Key Characteristics:

* High performance
* Low latency
* Direct access to data blocks
* Suitable for databases and operating systems

---

## 3️⃣ Amazon Elastic Block Store (EBS)

Amazon EBS provides **persistent block storage volumes** for EC2 instances.

### Important Points:

* EBS volumes attach to EC2 instances
* They are **Availability Zone–specific**
* Data persists even after EC2 is stopped or terminated (if not deleted)

### Features:

* Independent of EC2 lifecycle
* Volume size and type can be configured
* Ideal for boot volumes and database storage

---

### EBS Performance & Lifecycle

* Designed for **IOPS-intensive workloads**
* Supports **snapshots** for backups
* Snapshots are:

  * Point-in-time
  * Incremental
  * Stored in Amazon S3
* Snapshot policies can be automated for backup and recovery

---

## 4️⃣ Object Storage

Object storage stores data as objects instead of blocks.

Each object consists of:

* Data
* Unique ID
* Metadata

It is ideal for storing **large, unstructured data**.

---

## 5️⃣ Amazon Simple Storage Service (S3)

Amazon S3 is a **globally scalable object storage service**.

### Key Characteristics:

* Virtually unlimited storage
* Data stored inside **buckets**
* Each object can be up to **5 TB**
* Extremely high durability (11 nines)

### Use Cases:

* Static website hosting
* Data lakes
* Backups and archives
* Media storage

---

### S3 Security

S3 supports multiple security mechanisms:

* IAM policies
* Bucket policies
* Access Control Lists (ACLs)
* Pre-signed URLs
* Access logging

---

## 6️⃣ S3 Storage Classes

S3 provides different storage classes for cost optimization:

* **S3 Standard** – Frequently accessed data
* **S3 Intelligent-Tiering** – Unknown access patterns
* **S3 Standard-IA** – Infrequently accessed data
* **S3 Glacier Instant Retrieval**
* **S3 Glacier Flexible Retrieval**
* **S3 Glacier Deep Archive** – Long-term archival

### Intelligent-Tiering:

* Automatically moves data between tiers
* No performance impact
* Optimizes storage cost over time

---

## 7️⃣ S3 Lifecycle Policies

Lifecycle policies help:

* Transition objects between storage classes
* Delete data automatically when no longer required
* Reduce long-term storage costs

---

## 8️⃣ File Storage

File storage uses a hierarchical file structure and allows shared access to data.

It is suitable for applications that require:

* Shared file systems
* POSIX-compliant access
* Directory-based structure

---

## 9️⃣ Amazon Elastic File System (EFS)

EFS is a **fully managed file storage service** for Linux-based workloads.

### Features:

* Automatically scales storage
* Supports multiple EC2 instances simultaneously
* Uses NFS protocol
* Highly available across AZs

---

## 🔟 Amazon FSx

Amazon FSx provides **high-performance file systems** for specialized workloads.

### Variants:

* FSx for Windows File Server
* FSx for Lustre
* FSx for NetApp ONTAP
* FSx for OpenZFS

Used when advanced file system features or high throughput is required.

---

## 1️⃣1️⃣ AWS Storage Gateway

AWS Storage Gateway is a **hybrid storage service** that connects on-premises environments with AWS.

### Types:

* File Gateway
* Volume Gateway
* Tape Gateway

Used for seamless integration between on-prem infrastructure and cloud storage.

---

## 1️⃣2️⃣ AWS Elastic Disaster Recovery (DRS)

AWS Elastic Disaster Recovery helps:

* Replicate workloads to AWS
* Recover systems quickly during failures
* Ensure business continuity

---

## 🔁 Quick Comparison

* **EBS** → Block storage, AZ-level, databases
* **S3** → Object storage, global, scalable
* **EFS** → File storage, shared access
* **FSx** → High-performance file systems
* **Storage Gateway** → Hybrid cloud storage

---

## ✅ Key Takeaways (Revision)

* EBS is block storage for EC2
* S3 is global object storage
* EFS is shared file storage
* FSx is for performance-heavy workloads
* Lifecycle policies help reduce cost
* Storage choice depends on access pattern
