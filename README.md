# End-to-End NYC Taxi Data Pipeline on Databricks

An enterprise-grade, batch data engineering pipeline built using **Databricks**, **PySpark**, **Delta Lake**, and the **Medallion Architecture**.

## 🚀 Project Overview
This project processes millions of New York City Yellow Taxi records to track daily revenue trends, trip distances, and borough-level performance. It demonstrates production-ready data engineering practices including schema enforcement, data quality filtering, ACID transactions via Delta Lake, and workflow orchestration.

## 🏗️ Architecture & Data Flow
The pipeline follows the Medallion Architecture pattern:
1. **Bronze Layer (Raw Ingestion):** Ingests raw CSV.GZ files directly from DBFS into append-only Delta tables with added audit metadata (`ingestion_timestamp`, `source_file`).
2. **Silver Layer (Cleaning & Typing):** Casts data types, removes anomalous records (e.g., negative fares, zero distances, invalid timestamps), and deduplicates rows.
3. **Gold Layer (Business Aggregations):** Enriches clean data with taxi zone lookup tables and aggregates metrics into optimized reporting tables (`daily_trip_metrics`, `borough_daily_metrics`).

## 🛠️ Tech Stack
* **Compute & Processing:** Databricks, Apache Spark, PySpark
* **Storage & Governance:** Delta Lake, Unity Catalog
* **Orchestration:** Databricks Workflows (Jobs)
* **Version Control:** Git & GitHub

## 📂 Repository Structure
```text
nyc-taxi-databricks-medallion/
├── config/
│   └── nyc_taxi-medallion_pipeline.yml
├── notebooks/
│   ├── 01_bronze_ingestion.py
│   ├── 02_silver_transformation.py
│   └── 03_gold_aggregation.py
└── README.md
