# 🗄️ Week 3 – Day 1: Databases (AWS)

Databases are used to **store, retrieve, and manage data efficiently**. AWS provides both **relational (SQL)** and **non-relational (NoSQL)** database services, depending on data structure and application needs.

---

## 1️⃣ What is RDBMS (Relational Database)?

In **Relational Databases**, data is:

* Stored in **tables (rows & columns)**
* Structured with **fixed schema**
* Related using **keys**

### Common RDBMS Engines:

* MySQL
* PostgreSQL
* Oracle
* Microsoft SQL Server

Relational databases are best when:

* Data relationships matter
* Strong consistency is required
* Structured queries are common

---

## 2️⃣ Amazon RDS (Relational Database Service)

Amazon RDS is a **fully managed relational database service**.

### What AWS Manages for You:

* Automated patching
* Automated backups
* Redundancy
* Failover
* Disaster recovery

### Key Benefits:

* No manual DB maintenance
* High availability
* Secure and scalable

---

### Supported Engines in RDS:

* MySQL
* PostgreSQL
* MariaDB
* Oracle
* Microsoft SQL Server
* Amazon Aurora

---

## 3️⃣ Amazon Aurora (Managed RDBMS)

Aurora is AWS’s **cloud-optimized relational database**.

### Key Highlights:

* Compatible with MySQL & PostgreSQL
* Faster performance than standard RDS engines
* Replication across multiple AZs
* High availability by default

Aurora is ideal for:

* High-performance applications
* Large-scale production workloads

---

## 4️⃣ Why Choose RDS / Aurora?

* Automatic backups
* Multi-AZ replication
* Easy scaling
* Strong consistency
* Enterprise-grade reliability

---

## 5️⃣ What is NoSQL?

NoSQL databases:

* Store data in **non-relational formats**
* Have **flexible schema**
* Scale horizontally
* Designed for high speed and large-scale data

### Data Examples:

* Key-value pairs
* Documents
* JSON-like structures

---

## 6️⃣ Amazon DynamoDB (NoSQL Database)

Amazon DynamoDB is a **fully managed NoSQL key-value database**.

### Key Characteristics:

* Serverless (no infrastructure management)
* Extremely fast performance
* Flexible schema
* Automatic scaling
* Global tables supported

---

### DynamoDB Advantages:

* Add or remove attributes anytime
* No downtime during schema changes
* No patching or version upgrades
* Designed for distributed applications

---

## 7️⃣ DynamoDB Use Cases:

* Real-time applications
* Gaming leaderboards
* IoT data
* Session management
* High-traffic web apps

---

## 8️⃣ Caching Layer (Performance Optimization)

Caching reduces pressure on databases by storing **frequently accessed data** closer to applications.

### Amazon ElastiCache:

* In-memory data store
* Used with EC2 & RDS
* Reduces latency
* Improves throughput

### Supported Engines:

* Redis
* Memcached

---

### Why Use Caching?

* Faster response times
* Reduced DB load
* Better scalability
* Handles traffic spikes efficiently

---

## 9️⃣ Database Selection Logic (Quick Thinking)

* Structured data → **RDS / Aurora**
* High scale, flexible schema → **DynamoDB**
* High performance, low latency → **DynamoDB + ElastiCache**
* Read-heavy workloads → **Caching layer**

---

## 🔁 Database + Cache Flow (Concept)

Users → Application (EC2) →
• Check cache (ElastiCache)
• If miss → query DB (RDS / DynamoDB)
• Store result back in cache

---

## 🔑 Key Revision Points

* RDS = managed SQL database
* Aurora = high-performance RDS alternative
* DynamoDB = serverless NoSQL
* NoSQL = flexible schema
* Cache improves speed & scalability
* AWS manages backups & failover

---

## 🎯 Exam / Interview Ready Lines

* “RDS is a managed relational database service.”
* “Aurora provides MySQL/PostgreSQL compatibility with higher performance.”
* “DynamoDB is a serverless NoSQL database with automatic scaling.”
* “Caching reduces read pressure on primary databases.”
