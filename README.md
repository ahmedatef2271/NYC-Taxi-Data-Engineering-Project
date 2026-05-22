# NYC-Taxi-Data-Engineering-Project
An end-to-end data engineering project designed to process large-scale NYC Taxi datasets using modern Lakehouse architecture. Built on Microsoft Azure, the pipeline implements a robust Medallion architecture (Bronze, Silver, Gold layers) using PySpark and Delta Lake.

# NYC Taxi Enterprise Data Platform

An end-to-end, production-grade Azure Data Engineering pipeline processing 
large-scale NYC Taxi datasets using an open Lakehouse architecture.

## 🛠️ Architecture & Tech Stack

| Component | Technology | Implementation Details |
| :--- | :--- | :--- |
| **Cloud Storage** | Azure Data Lake Storage (ADLS Gen2) | Multi-container environment separated by environment zones |
| **Compute & Processing** | Azure Databricks (PySpark) | Optimized distributed processing engine for heavy ETL workloads |
| **Data Architecture** | Medallion Architecture | Clean structural separation across **Bronze**, **Silver**, and **Gold** layers |
| **Storage Format** | Delta Lake | Implements ACID transactions, schema evolution, and time-travel debugging |
| **Data Modeling** | Dimensional Modeling | Slowly Changing Dimensions (**SCD Type 2**) for tracking historical records |
| **Governance** | Unity Catalog | Centralized access control, secure external storage mapping, and data lineage |
