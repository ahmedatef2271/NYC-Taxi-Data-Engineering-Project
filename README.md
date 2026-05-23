## Data system Architecture 

### 🔄 End-to-End Data Pipeline Flow :

1. **Source System (NYC-TLC):** 
   * Transactional data is hosted on the official NYC Taxi & Limousine Commission public web servers.
   * **Orchestration:** **Azure Data Factory (ADF)** establishes an HTTP Linked Service connection to pull these source files programmatically.

2. **Bronze Layer (Raw Ingestion):**
   * ADF streams the raw files directly into the **Bronze Container** inside Azure Data Lake Storage (ADLS Gen2) in form of **parquet** format

3. **Silver Layer (Transformation):**
   * **Azure Databricks** mounts the data lake containers and processes the raw files.
   * Using a combination of **PySpark** and **Spark SQL**, the pipeline cleanses data types, removes structural anomalies, resolves missing values, and appends ingestion metadata.
   * The sanitized datasets are written back to the **Silver Container** in optimized **Parquet format**.

4. **Gold Layer (Business Analytics & Serving):**
   * Databricks reads the Silver data and applies dimensional modeling 
   * The final business-ready tables are materialized directly into the **Gold Container** using the advanced **Delta Table format**.
   * 
5. **Reporting & Analytics:**
   * **Power BI** establishes a direct native connection to the Gold Delta tables via Databricks SQL Warehouses (governed securely through Unity Catalog properties).
   * Business stakeholders interact with responsive executive dashboards tracking revenue trends, congestion patterns, and vehicle efficiency.
