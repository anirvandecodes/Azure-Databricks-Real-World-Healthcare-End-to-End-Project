# 🏥 Healthcare Data Engineering Platform

An end-to-end healthcare data engineering project built with **Azure Databricks**, **Azure Data Lake Storage (ADLS)**, **Unity Catalog**, and **GitHub**.

The project demonstrates how raw healthcare data can be ingested, transformed, modeled, and served for analytics using a modern **Medallion Architecture (Bronze → Silver → Gold)**.

---

## 📌 Project Overview

Healthcare organizations generate large volumes of data from different sources. To make this data useful for analytics and decision-making, it needs to be:

- Ingested from source systems
- Stored reliably
- Cleaned and transformed
- Integrated into analytical models
- Aggregated for business reporting
- Made accessible through dashboards and AI-powered analytics

This project implements an end-to-end data platform using Azure Databricks and follows modern data engineering practices.

---

## 🎯 Business Problem

The goal of this project is to build a healthcare data platform capable of transforming raw healthcare data into trusted analytical datasets.

The platform should allow analysts and decision-makers to answer questions such as:

- How many patients are being treated?
- What are the most common diagnoses?
- How are patient metrics changing over time?
- Which conditions have the highest occurrence?
- What trends can be identified from historical healthcare data?

---

## 🏗️ Architecture

```text
                    ┌─────────────────────┐
                    │    Raw Healthcare   │
                    │        Data         │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │   Azure Data Lake   │
                    │       Storage       │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │   Azure Databricks  │
                    │    Unity Catalog    │
                    └──────────┬──────────┘
                               │
                    ┌──────────▼──────────┐
                    │       BRONZE        │
                    │   Raw / Ingested    │
                    │       Data          │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │       SILVER        │
                    │ Cleaned & Integrated│
                    │       Data          │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │        GOLD         │
                    │ Aggregated &        │
                    │ Analytical Data     │
                    └──────────┬──────────┘
                               │
                 ┌─────────────┴─────────────┐
                 ▼                           ▼
        ┌─────────────────┐        ┌─────────────────┐
        │   AI/BI Genie   │        │   AI/BI         │
        │                 │        │   Dashboard     │
        └─────────────────┘        └─────────────────┘
````

---

# 🥉 Bronze Layer

The Bronze layer contains the raw data ingested from the source system.

The project uses **Databricks Auto Loader** to ingest incoming files into the Bronze layer.

### Responsibilities

* Ingest raw healthcare data
* Preserve the original data structure
* Handle incremental file ingestion
* Store raw data in Delta tables

---

# 🥈 Silver Layer

The Silver layer contains cleaned and integrated data.

Data from the Bronze layer is transformed and prepared for analytical use.

### Responsibilities

* Data cleaning
* Data transformation
* Data integration
* Handling duplicates
* Merge and upsert operations
* Creating trusted datasets

The project uses **MERGE / UPSERT logic** to maintain the Silver layer.

---

# 🥇 Gold Layer

The Gold layer contains business-ready datasets designed for analytics.

Transformations include:

* Window functions
* Aggregations
* Business metrics
* Analytical calculations

The Gold layer provides the datasets consumed by the analytics layer.

---

# 🗄️ Data Modeling

The project follows **Kimball dimensional modeling** principles.

A **Star Schema** is used to organize analytical data into:

```text
              ┌──────────────────┐
              │  Dimension Table │
              └────────┬─────────┘
                       │
                       │
┌──────────────────────┼──────────────────────┐
│                      │                      │
▼                      ▼                      ▼
┌─────────────┐  ┌─────────────┐  ┌────────────────┐
│ Dimension   │  │ Fact Table  │  │ Dimension      │
│             │──│             │──│                │
└─────────────┘  └─────────────┘  └────────────────┘
                       │
                       │
                       ▼
                Analytical Queries
```

This structure makes analytical queries easier to maintain and optimize.

---

# ☁️ Azure Infrastructure

The project uses the following Azure services:

### Azure Data Lake Storage Gen2

Used as the cloud storage layer for the healthcare data.

### Azure Databricks

Used for:

* Data ingestion
* Data transformation
* Spark processing
* Delta Lake tables
* Workflow orchestration
* Analytics

### Unity Catalog

Used for centralized data governance and access control.

It manages:

* Catalogs
* Schemas
* Tables
* External locations
* Storage credentials
* Permissions

### Access Connector / Managed Identity

Used to securely connect Azure Databricks to Azure Data Lake Storage without storing storage account keys directly in the notebooks.

---

# 🔐 Data Governance

Unity Catalog provides centralized governance for the data platform.

The project uses:

* Managed identities
* Storage credentials
* External locations
* Access control
* Catalog and schema permissions

This allows Databricks to securely access data stored in ADLS.

---

# 🔄 Databricks Workflows

Databricks Workflows are used to orchestrate the data pipeline.

The pipeline follows:

```text
Raw Data
   │
   ▼
Bronze Job
   │
   ▼
Silver Job
   │
   ▼
Gold Job
   │
   ▼
Analytics
```

This allows the different data processing stages to run in the correct order.

---

# 🔧 Git Integration

The project is integrated with **GitHub** for version control.

Development workflow:

```text
Databricks
     │
     ▼
Modify Notebook
     │
     ▼
Git Commit
     │
     ▼
Git Push
     │
     ▼
GitHub Repository
```

This provides:

* Version control
* Change tracking
* Collaboration
* Branch management
* Reproducibility

---

# 🚀 CI/CD

The project introduces **Databricks Asset Bundles (DABs)** and **GitHub Actions** for CI/CD.

The objective is to automate the deployment of Databricks resources and workflows.

```text
Developer
    │
    ▼
GitHub Repository
    │
    ▼
GitHub Actions
    │
    ├── Validate
    ├── Test
    └── Deploy
            │
            ▼
      Azure Databricks
```

This allows changes to be tested and deployed in a repeatable way.

---

# 📊 Analytics

The final Gold datasets are used for analytics through:

### AI/BI Genie

Allows users to interact with healthcare data using natural-language questions.

Example questions:

```text
What are the most common diagnoses?

How many patients were treated?

What are the trends over time?
```

### AI/BI Dashboards

Interactive dashboards are created to visualize the business metrics produced by the Gold layer.

The dashboards provide a business-friendly interface for exploring healthcare data.

---

# 🛠️ Technology Stack

| Technology                   | Purpose                      |
| ---------------------------- | ---------------------------- |
| Azure Data Lake Storage Gen2 | Cloud data storage           |
| Azure Databricks             | Data engineering & analytics |
| Apache Spark                 | Distributed data processing  |
| Delta Lake                   | Reliable data storage        |
| Unity Catalog                | Data governance              |
| Azure Managed Identity       | Secure authentication        |
| Databricks Auto Loader       | Incremental data ingestion   |
| Databricks Workflows         | Pipeline orchestration       |
| GitHub                       | Version control              |
| Databricks Asset Bundles     | Deployment                   |
| GitHub Actions               | CI/CD                        |
| AI/BI Genie                  | Natural-language analytics   |
| AI/BI Dashboards             | Data visualization           |

---

# 📂 Project Structure

```text
healthcare-data-engineering/
│
├── bronze/
│   └── diagnosis_raw_data_ingestion.ipynb
│
├── silver/
│   └── ...
│
├── gold/
│   └── ...
│
├── resources/
│   └── ...
│
├── tests/
│   └── ...
│
├── databricks.yml
│
└── README.md
```

> The structure may evolve as additional deployment and CI/CD components are added.

---

# 🔄 End-to-End Data Flow

```text
Healthcare Source Data
        │
        ▼
Azure Data Lake Storage
        │
        ▼
Databricks Auto Loader
        │
        ▼
     BRONZE
   Raw Data
        │
        ▼
   Transformations
        │
        ▼
      SILVER
 Cleaned Data
        │
        ▼
 Aggregations +
 Window Functions
        │
        ▼
       GOLD
 Business Data
        │
        ├───────────────┐
        ▼               ▼
   AI/BI Genie      AI/BI Dashboard
```

---

# 🎯 Key Learning Objectives

This project demonstrates practical experience with:

* Designing an end-to-end data engineering architecture
* Azure cloud services
* Azure Data Lake Storage
* Databricks
* Apache Spark
* Delta Lake
* Unity Catalog
* Managed identities
* External locations
* Medallion Architecture
* Kimball dimensional modeling
* Star schemas
* Incremental data ingestion
* MERGE / UPSERT operations
* Window functions
* Data aggregation
* Databricks Workflows
* Git and GitHub
* CI/CD
* Databricks Asset Bundles
* AI-powered analytics

---

# 📌 Future Improvements

Potential improvements include:

* Docker-based development and testing
* Automated data quality tests
* More advanced CI/CD pipelines
* Infrastructure as Code
* Monitoring and alerting
* Additional healthcare datasets
* Advanced analytics and ML models

---

# 👨‍💻 Author

**Houcine**

Data Engineering & AI

This project was built as a hands-on implementation of a real-world healthcare data engineering platform using Azure Databricks.

````

### One thing I'd change as you build it

Don't claim the **DAB, CI/CD, Docker, tests, etc.** are implemented until you actually implement them.

For your current stage, I'd keep the README sections but mark future parts honestly, e.g.:

```text
🚧 In Progress
- CI/CD with GitHub Actions
- Databricks Asset Bundles
- Data quality testing
- Docker
````

That actually looks **better for a portfolio** because someone looking at your GitHub can see the project's evolution instead of thinking you copied a finished repository.

And now that you're at **Bronze → Silver → Gold**, I'd focus on finishing the actual pipeline first, then the dashboard, and only afterward add DAB/CI/CD as an advanced layer.
