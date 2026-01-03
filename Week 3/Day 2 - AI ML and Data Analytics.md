# 🧠 Week 3 · Day 2

## AI / ML & Data Analytics on AWS

---

## 1️⃣ Artificial Intelligence (AI)

### 🔹 What is AI?

Artificial Intelligence is a **broad field** focused on building systems that can perform **human-like tasks** such as:

* Understanding language
* Recognizing images
* Making decisions
* Learning from experience

🧠 **Analogy**:
AI is like a **smart assistant** that can see, hear, understand, and respond — similar to how humans do.

---

## 2️⃣ Machine Learning (ML)

### 🔹 What is ML?

Machine Learning is a **subset of AI** where machines:

* Learn from **data**
* Identify **patterns**
* Improve over time
  👉 **without being explicitly programmed**

### 🔁 ML Lifecycle (as in your notes)

```
Training on Data
        ↓
Identifying Patterns
        ↓
ML Model Created
```

### 🔄 Inference Phase

When **new data** comes in:

```
New Data → ML Model → Inference → Response
```

✔ No hard-coded rules
✔ Model decides based on learned patterns

🎯 **Common ML Use Cases**

* Recommendations (Netflix, Amazon)
* Personalization
* Fraud detection
* Forecasting

---

## 3️⃣ AWS AI / ML Stack (Big Picture)

Think of AWS AI/ML stack like **layers of a cake** 🍰:

### 🧩 Layer 1: AI Services (Pre-built)

👉 For developers who want **ready-to-use intelligence**

Examples:

* **Amazon Polly** – Text → Speech
* **Amazon Comprehend** – Text analysis
* **Amazon Transcribe** – Speech → Text
* **Amazon Translate** – Language translation
* **Amazon Rekognition** – Image & video analysis
* **Amazon Textract** – Extract text from documents

🧠 Analogy:
Like ordering **ready-made food** instead of cooking yourself.

---

### 🧩 Layer 2: ML Services (Custom Models)

👉 For building **custom ML models**

* **Amazon SageMaker**

  * Build
  * Train
  * Deploy
  * Monitor ML models
  * Fully managed

🎯 Ideal for data scientists & ML engineers

---

### 🧩 Layer 3: ML Frameworks & Infrastructure

👉 For **maximum control**

Frameworks:

* TensorFlow
* PyTorch
* Apache MXNet

Infrastructure:

* EC2
* ECS
* EMR

🧠 Analogy:
Cooking from scratch with your **own ingredients and kitchen**.

---

## 4️⃣ Generative AI (GenAI)

### 🔹 What is GenAI?

A **type of Deep Learning** that can **create new content**, such as:

* Conversations
* Images
* Stories
* Music
* Code

### 🧠 How it works

* Uses **Deep Neural Networks (ANNs)**
* Trained on **huge datasets**
* Powered by **Foundation Models (FMs)**

```
ML
 └── Deep Learning
      └── Generative AI
```

---

## 5️⃣ GenAI Services on AWS

### ⭐ Amazon SageMaker JumpStart

* Pre-trained Foundation Models
* Deploy in a few clicks
* Customize with your own data

### ⭐ Amazon Bedrock

* Fully managed GenAI service
* Access FMs from AWS & partners
* Single API for multiple models
* Secure & scalable

### ⭐ Amazon Q

* Business-focused GenAI assistant
* Helps with:

  * Queries
  * Documentation
  * Decision-making
* Versions:

  * Amazon Q Business
  * Amazon Q Developer

---

## 6️⃣ Data Analytics (DA)

### 🔹 What is Data Analytics?

Data Analytics is the process of:

* Transforming **raw historical data**
* Into **meaningful insights & trends**
* For better decision-making

🧠 Analogy:
Raw data is **crude oil** → analytics is **refined fuel**.

---

## 7️⃣ Data Lakes vs Data Warehouses

### 🟦 Data Lake

* Stores **all types of data**
* Structured + Unstructured
* Example: **Amazon S3**

### 🟩 Data Warehouse

* Stores **processed & structured data**
* Optimized for analytics
* Example: **Amazon Redshift**

---

## 8️⃣ ETL & Data Pipelines

### 🔹 Why ETL?

Having all data in one place isn’t enough.
Data must be in a **usable format** for analytics.

### 🔁 ETL Flow

```
Extract → Transform → Load
```

* Extract: from multiple sources
* Transform: clean & format
* Load: into warehouse / analytics system

⚠ Sometimes **ELT** is used
⚠ Sometimes ETL is **not required**

---

## 9️⃣ Data Pipelines on AWS (End-to-End View)

### 🔄 Pipeline Flow

```
Data → Collect → Process → Analyze → Answers
```

### 🔹 Ingestion (Collect)

* **Amazon Kinesis** – real-time streaming
* **Amazon Firehose** – near real-time delivery
* **AWS Glue Data Catalog**

  * Metadata management
  * Auto data discovery

### 🔹 Processing (Clean & Transform)

* **AWS Glue**

  * Managed ETL
  * Visual jobs
  * Code-free processing
* **Amazon EMR**

  * Large-scale processing
  * Apache Spark
  * More flexibility & control

### 🔹 Storage

* **Amazon S3** – Data lake (unstructured)
* **Amazon Redshift** – Warehouse (structured)

### 🔹 Visualization

* **Amazon QuickSight**

  * Business Intelligence
  * Dashboards
  * Scales to thousands of users

---

## 🔟 Real-World Analogy (E-Commerce)

🛒 **E-commerce App**

* User clicks → DynamoDB
* Events → Kinesis
* Stream → Firehose
* Store → S3
* Catalog → Glue
* Query → Athena
* Visualize → QuickSight
* ML → SageMaker
* Recommendations → GenAI

🎯 End result: **Real-time insights + personalization**

---

## ✅ Final Summary (Revision Gold 🥇)

* AI → broad intelligence
* ML → learning from data
* GenAI → creating new content
* AWS provides:

  * Prebuilt AI services
  * Custom ML with SageMaker
  * GenAI with Bedrock & Q
* Data Analytics turns raw data into insights
* ETL + pipelines automate the data journey
* S3 + Redshift + Glue + EMR + QuickSight = analytics backbone
