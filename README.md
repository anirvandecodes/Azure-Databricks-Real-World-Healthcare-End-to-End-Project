# 🏥 Healthcare Data Engineering Project

## 📌 Project Overview

This project implements an end-to-end healthcare data engineering solution using **Azure Databricks, Azure Data Lake Storage Gen2, Unity Catalog, Delta Lake, and Power BI**.

The project demonstrates how raw healthcare data can be ingested, transformed, cleaned, modeled, and prepared for analytics through a **Medallion Architecture (Bronze → Silver → Gold)**.

The final Gold-layer data is connected to **Power BI** to create an interactive healthcare analytics dashboard.

---

## 🎯 Business Problem

Healthcare organizations generate large amounts of data from hospitals, patients, visits, and diagnoses.

The objective of this project is to build a scalable data platform that can:

- Ingest raw healthcare data
- Store and manage data using Azure Data Lake Storage
- Process data using Apache Spark and Databricks
- Clean and transform healthcare records
- Implement incremental processing and upsert logic
- Build analytical Gold-layer datasets
- Provide business insights through Power BI

---

## 🏗️ Project Architecture

```text
                    Azure Data Lake Storage Gen2
                              │
                              ▼
                       Raw / Staging Data
                              │
                              ▼
                    ┌───────────────────┐
                    │   BRONZE LAYER    │
                    │   Raw ingestion    │
                    │   Auto Loader      │
                    └─────────┬─────────┘
                              │
                              ▼
                    ┌───────────────────┐
                    │   SILVER LAYER    │
                    │ Cleaning &         │
                    │ transformations    │
                    │ Merge / Upsert     │
                    └─────────┬─────────┘
                              │
                              ▼
                    ┌───────────────────┐
                    │    GOLD LAYER     │
                    │ Aggregations &     │
                    │ analytical models  │
                    └─────────┬─────────┘
                              │
                              ▼
                         Power BI
                       Dashboard
````

---

## 🛠️ Technologies Used

* **Azure Data Lake Storage Gen2**
* **Azure Databricks**
* **Unity Catalog**
* **Apache Spark / PySpark**
* **Delta Lake**
* **Auto Loader**
* **GitHub**
* **Databricks Workflows**
* **Power BI**
* **Python**
* **SQL**

---

## 📂 Data Sources

The project uses four raw healthcare datasets:

| Dataset         | Description              |
| --------------- | ------------------------ |
| `patient_raw`   | Patient information      |
| `visit_raw`     | Patient hospital visits  |
| `hospital_raw`  | Hospital information     |
| `diagnosis_raw` | Diagnosis reference data |

To make the project more representative of a real-world data engineering workload, the original datasets were expanded with additional synthetic records while preserving the relationships between the datasets.

### Expanded Dataset

| Dataset   | Records |
| --------- | ------: |
| Patients  |     500 |
| Visits    |   5,000 |
| Hospitals |      30 |
| Diagnoses |      40 |

The expanded data introduces greater volume and variety while maintaining valid relationships between patients, visits, hospitals, and diagnoses.

---

## 🥉 Bronze Layer

The Bronze layer contains the raw ingested healthcare data.

The project uses **Databricks Auto Loader** to ingest files from Azure Data Lake Storage.

The main objectives of the Bronze layer are:

* Ingest raw data
* Preserve the source data
* Support incremental file ingestion
* Store data in Delta format
* Provide a reliable foundation for downstream transformations

---

## 🥈 Silver Layer

The Silver layer contains cleaned and transformed healthcare data.

Transformations include:

* Data cleaning
* Data type standardization
* Handling missing values
* Removing duplicates
* Data validation
* Merge and upsert logic
* Preparing data for analytical processing

---

## 🥇 Gold Layer

The Gold layer contains business-ready datasets designed for analytics.

Transformations include:

* Aggregations
* Window functions
* Business calculations
* Analytical metrics
* Dimensional modeling

The Gold layer provides the datasets required for the final reporting and visualization stage.

---

## 📊 Power BI Dashboard

Instead of using the Databricks built-in dashboard from the original tutorial, this implementation uses **Microsoft Power BI** as the final visualization and analytics layer.

The Power BI dashboard connects to the Gold-layer data and provides an interactive view of healthcare performance and patient-related metrics.

The dashboard allows users to analyze areas such as:

* Hospital performance
* Patient activity
* Diagnosis distribution
* Visit trends
* Healthcare costs
* Key performance indicators

---

## 🔄 Data Pipeline

The complete pipeline follows:

```text
Raw CSV Files
     │
     ▼
Azure Data Lake Storage
     │
     ▼
Databricks Auto Loader
     │
     ▼
Bronze Delta Tables
     │
     ▼
Data Cleaning & Transformation
     │
     ▼
Silver Delta Tables
     │
     ▼
Aggregations & Business Logic
     │
     ▼
Gold Delta Tables
     │
     ▼
Power BI
     │
     ▼
Healthcare Analytics Dashboard
```

---

## ⚙️ Orchestration

Databricks Workflows are used to orchestrate the different stages of the data pipeline.

The workflow coordinates:

1. Bronze ingestion
2. Silver transformations
3. Gold transformations
4. Downstream processing

This allows the pipeline to run as an automated data engineering workflow rather than executing each notebook manually.

---

## 🔐 Data Governance

The project uses **Unity Catalog** for centralized data governance and access management.

Key components include:

* Metastore
* Storage Credentials
* External Locations
* Access Connector
* Catalogs
* Schemas
* Table permissions

This provides controlled access to the underlying Azure Data Lake Storage resources.

---

## 🔗 Git Integration

The Databricks workspace is integrated with **GitHub** to provide version control for the project.

This allows:

* Version tracking
* Commit history
* Collaboration
* Reproducibility
* Project source-code management

---

## 🚀 Future Improvements

Potential improvements include:

* Increasing dataset volume further
* Adding more healthcare entities
* Implementing data quality checks
* Adding CI/CD with GitHub Actions
* Implementing Databricks Asset Bundles
* Adding automated testing
* Improving Spark performance
* Adding incremental data ingestion scenarios
* Implementing monitoring and alerting

---

## 📚 Key Concepts Demonstrated

This project demonstrates practical experience with:

* Data Lake Architecture
* Medallion Architecture
* ETL / ELT
* Apache Spark
* PySpark
* Delta Lake
* Auto Loader
* Incremental Data Processing
* Merge / Upsert
* Dimensional Modeling
* Star Schema
* Window Functions
* Data Governance
* Unity Catalog
* Databricks Workflows
* Git & GitHub
* Power BI
* Data Visualization

---

## 👨‍💻 Author

**Houcine Aberhache**

Data Engineering & AI Student

Interested in Data Engineering, Cloud, Big Data and AI.

---

## ⭐ Project

If you found this project useful, feel free to explore the repository and follow the development of the project.

```
