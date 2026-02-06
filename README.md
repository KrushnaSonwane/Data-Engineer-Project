# Azure End-to-End Data Engineering Project

This repository contains an end-to-end data engineering pipeline implemented using Azure services.  
The project demonstrates ingestion, transformation, and analytics using a layered data lake architecture.

---

## Project Description

The pipeline ingests raw data into Azure Data Lake Storage using Azure Data Factory.  
Data is transformed using PySpark in Azure Databricks and stored in structured layers.  
Curated data is loaded into Azure Synapse Analytics for analytical querying and reporting.

---

## Architecture Overview

Source Data  
→ Azure Data Factory (Ingestion)  
→ Azure Data Lake Storage Gen2  
→ Databricks (PySpark Transformations)  
→ Azure Synapse Analytics  
→ Power BI (Reporting)

The project follows the Medallion Architecture:

- **Bronze Layer**: Raw ingested data  
- **Silver Layer**: Cleaned and transformed data  
- **Gold Layer**: Aggregated and analytics-ready data  

---

## Technologies Used

- Azure Data Factory  
- Azure Data Lake Storage Gen2  
- Azure Databricks  
- PySpark  
- Azure Synapse Analytics  
- Power BI  
- Azure Managed Identity / Service Principal  

---

## Data Flow

1. Azure Data Factory pipelines ingest source data into the **Bronze** container.
2. Databricks notebooks read Bronze data and apply transformations.
3. Transformed data is written to the **Silver** layer.
4. Aggregations and business logic are applied to create **Gold** layer datasets.
5. Gold data is loaded into Azure Synapse Analytics.
6. Power BI connects to Synapse for reporting.

---

## Repository Structure

