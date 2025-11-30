# databricks-portfolio
This repo stores all the code related to Databricks project
# Insurance Claim Fraud Detection
## Overview
This project uses Databricks to ingest, process, and analyze insurance claim data to predict fraudulent claims.  
It implements a **medallion architecture** (Bronze → Silver → Gold) and includes ML model training, evaluation, and deployment using MLflow.

## Business Problem
Fraudulent claims cost insurers billions annually. Identifying high-risk claims early reduces financial losses and improves claim processing efficiency.

## Architecture
1. **Ingestion (Bronze Layer):**  
   - Raw claim data ingested from cloud storage (DBFS) via **Databricks AutoLoader**.  
   - Stored in **Bronze tables** for minimal transformations.

2. **Transformation (Silver Layer):**  
   - Data cleaning: handle missing values, standardize dates and text.  
   - Feature engineering: claim-to-coverage ratio, claim frequency, reporting delay.  
   - Stored in **Silver tables** for downstream ML and analytics.

3. **Modeling:**  
   - Train **XGBoost classifier** using curated Silver features.  
   - Track experiments, parameters, metrics, and models using **MLflow**.  
   - Model stored in **MLflow Model Registry**.

4. **Evaluation:**  
   - Evaluate model using **ROC, precision, recall, F1-score**.  
   - Predictions on validation/test sets stored in Silver for monitoring.

5. **Serving:**  
   - Deploy model via **Databricks Model Serving** for real-time scoring.  
   - Real-time predictions logged back into Silver tables.

6. **Gold Layer (Curated Analytics Layer):** 
   - High-quality curated tables ready for business use:  
     - `gold.insurance_fraud_features` → cleaned, engineered features for analytics  
     - `gold.insurance_fraud_predictions` → final fraud predictions with probability and timestamp  
   - Used for **dashboards, BI reports, and management analytics**



   

