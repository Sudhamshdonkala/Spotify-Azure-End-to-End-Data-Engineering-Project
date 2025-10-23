# Spotify Azure End-to-End Data Engineering Project

This project demonstrates how to build a **complete Azure data pipeline** without relying on any external API calls. Instead of using Spotify’s API for raw data extraction, this project begins with **pre-existing structured Spotify data stored in Azure SQL Database** and applies Azure-native data engineering principles for downstream transformation, curation, and reporting.

## Project Overview

The goal is to create an **end-to-end ETL/ELT workflow** that efficiently moves and transforms data from SQL to the data lake, manages it through layers of processing, and serves it for analytics. The project follows a **Medallion Architecture** (Bronze, Silver, Gold) approach to optimize maintainability, scalability, and data quality.

### Key Objectives

- Implement a **metadata-driven pipeline** using Azure Data Factory.
- Enable **incremental ingestion** from SQL source tables into the data lake.
- Apply **PySpark transformations** in Azure Databricks for cleansing, joining, and aggregating datasets.
- Store curated datasets in **Azure SQL Database** for Power BI reporting.
- Automate orchestration of all workflows using **ADF triggers and pipelines**.

***

## Azure Architecture

| Layer | Purpose | Technology |
|--------|----------|------------|
| **Bronze** | Ingest structured SQL datasets into the Data Lake (in Parquet/Delta format). | Azure Data Factory (Copy Activity) |
| **Silver** | Transform and clean the data for analysis. | Azure Databricks (PySpark) |
| **Gold** | Model data for reporting, build star schema tables. | Azure SQL Database |

***

## Tools and Services Used

- **Azure SQL Database** – Source of structured Spotify data (artists, albums, tracks, etc.).
- **Azure Data Factory (ADF)** – Orchestrates data pipeline automation and incremental ingestion.
- **Azure Data Lake Storage Gen2 (ADLS)** – Serves as the data lake, storing raw and processed data.
- **Azure Databricks** – Performs transformation using PySpark with Delta format for optimization.
- **Power BI** – Builds dashboards for analytics and visualization.

***

## Setup Guide

### 1. Clone the Repository
```
git clone https://github.com/Sudhamshdonkala/Spotify-Azure-End-to-End-Data-Engineering-Project.git
cd Spotify-Azure-End-to-End-Data-Engineering-Project
```

### 2. Configure Azure Environment
Create the following resources:
- Azure Data Lake Storage Gen2
- Azure Data Factory
- Azure Databricks workspace
- Azure SQL Database (already contains structured data)

### 3. Ingest Data from SQL
- Use Azure Data Factory’s **Copy Data** activity to extract tables (e.g., `Artists`, `Albums`, `Tracks`) from Azure SQL into **Bronze** (raw) layer in the data lake.
- Store files as **Parquet** or **Delta**.

### 4. Data Transformation (Silver Layer)
- Use Databricks notebooks with **PySpark** to perform transformations such as:
  - Data cleanup and normalization
  - Duplicate removal
  - Joining fact and dimension tables
  - Data validation and type casting

### 5. Data Modeling (Gold Layer)
- Load final analytical datasets (fact and dimension tables) into Azure SQL Database.
- Maintain a **star schema** for Power BI consumption.

Example tables:
- `Dim_Artists`
- `Dim_Albums`
- `Fact_Streams`

### 6. Visualization (Optional)
- Connect **Power BI** to Azure SQL Database.
- Build dashboards to display trends, artist popularity, or streaming metrics.

***

## Data Flow Summary

1. **Source**: Structured Spotify data already in SQL.
2. **ADF Ingestion** → Exports SQL tables to ADLS.
3. **Databricks Processing** → Cleans, transforms, and standardizes data.
4. **ADF Load Activity** → Writes transformed data to Azure SQL (Gold Layer).
5. **BI Reporting** → Power BI uses Azure SQL for visualization.

***

## Key Highlights

- No dependency on Spotify API; project works entirely on Azure services.
- Suitable for real-world enterprise scenarios involving **on-premises or Azure SQL databases**.
- Scalable architecture for both **batch and incremental** loads.
- Implements **parameterized pipelines** and **modular Databricks notebooks**.

***
