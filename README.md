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

## Steps to run project

1. You must have azure free trial account to run this project
2. First create Data Lake Storage Gen2
  Go to azure portal -> Serach for storage account -> While creating do NOT forget to tick hierarchical namespace for storing sturcture data(Azure Data Lake) as shown below


  <img width="975" height="357" alt="image" src="https://github.com/user-attachments/assets/24777791-818e-42fd-9965-4e198580d081" />

  
  then create three conatinaers called: Bronze, Silver and Gold 

  
  <img width="975" height="433" alt="image" src="https://github.com/user-attachments/assets/21c1284a-b694-404d-a25a-93243f6d3b0e" />


3. Now we want to pull data from Github repository to Azure data lake storgae for that need to create azure data **pipeline**
  Go to portal -> serach for **Azure data factory** and create one
4. We need to create link between git repository to ADF to pull the data from same and create a link between ADF to Data Lake to store data into refer to below snip.
   First launch your ADF
   
<img width="975" height="455" alt="image" src="https://github.com/user-attachments/assets/e3ec67b1-b24a-47a2-93f1-e7cc1a528768" />

<img width="975" height="462" alt="image" src="https://github.com/user-attachments/assets/fec79495-afaa-4a0e-9ae6-361f975c6025" />


5. Create a pipeline with Copy activity to copy the data from Github repository to Data Lake


<img width="975" height="515" alt="image" src="https://github.com/user-attachments/assets/79241608-a09b-4b07-bd9d-3a6fba965543" />


6. Select copy activity and in the source attached your created linked service of Github to ADF, and provide URL of your data set(Link of Github row data) and


  <img width="975" height="464" alt="image" src="https://github.com/user-attachments/assets/d65b1e51-13bf-4606-bb12-96a42b420829" />


7. in the sink(destination) option attach linked service of ADF to Data Lake and provide the destination to store data as show below snips


<img width="975" height="811" alt="image" src="https://github.com/user-attachments/assets/213c9bad-365e-4e64-829c-a9878d865b2c" />


8. Now run your pipeline(and it will copy the data file from Github to Azure data lake)
  you can create separate copy activity to pull each data set from Github or else you can create foreach activity to pull all at once



<img width="975" height="531" alt="image" src="https://github.com/user-attachments/assets/9dec8b07-9b7c-4211-bff8-c8fb1abb2e9a" />



9. Create a Azure Databricks for Data transformation and launch the same


<img width="975" height="460" alt="image" src="https://github.com/user-attachments/assets/ce8cf3ce-3905-4bc6-93da-6f6d751001fe" />


10. Create one clustore to run your transpformation with below confirgaration from CLuster Tab


<img width="975" height="463" alt="image" src="https://github.com/user-attachments/assets/12581b60-be39-41c4-810f-1573ec911886" />




Next steps will be update soon.....
