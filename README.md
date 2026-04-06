# FMCG Data Pipeline | Unified Analysis Project

## Problem Statement
Atlikon (sports equipment manufacturer) acquired Sports Bar (nutrition 
startup). Both companies had incompatible data systems. Built a unified 
data pipeline to consolidate analytics across both companies.

## Architecture
Raw CSV Files → Bronze (Raw) → Silver (Cleaned) → Gold (BI Ready)

## Tech Stack
- Python, PySpark, SQL
- Databricks (Free Edition)
- Delta Lake
- Medallion Architecture (Bronze/Silver/Gold)
- Star Schema Data Modeling
- Databricks Jobs (Orchestration)
- Databricks Dashboard & Genie AI

## Pipeline Overview
1. Raw CSV ingestion into Bronze layer via Databricks Volumes
2. Data cleaning in Silver layer:
   - Deduplication
   - Null handling
   - Date normalization
   - Regex-based corrections
   - Invalid value handling
3. BI-ready consolidated Gold layer with upsert operations
4. Automated daily orchestration via Databricks Jobs
5. Interactive Dashboard + Genie AI analytics

## Data Model (Star Schema)
- Fact Table: Orders
- Dimension Tables: Customers, Products, Gross Price, Date

## Folder Structure

```text
complete_pipeline/
├── setup/
├── dimension_processing/
│   ├── customer_data_processing
│   ├── products_data_processing
│   └── gross_price_data_processing
├── fact_processing/
│   ├── fact_full_load
│   └── fact_incremental_load
└── sample_data/
```

## How to Run
1. Create free Databricks account at databricks.com
2. Create catalog: fmcg with schemas: bronze, silver, gold
3. Create Databricks Volume: /Volumes/fmcg/bronze/sports_bar_raw
4. Upload CSV files into volume subfolders
5. Run notebooks in this order:
   - setup/utilities
   - dimension_processing/customer_data_processing
   - dimension_processing/products_data_processing
   - dimension_processing/gross_price_data_processing
   - fact_processing/fact_full_load
   - fact_processing/fact_incremental_load
