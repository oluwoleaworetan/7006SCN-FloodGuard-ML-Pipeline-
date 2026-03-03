This folder contains the 6 Databricks notebooks for the FloodGuard ML Pipeline.

## Execution Order
1. `1_bronze_ingestion.ipynb` — RDD-based data ingestion → Parquet
2. `2_Silver_Cleaning_EDA.ipynb` — Cleaning, feature engineering, scaling
3. `3_Gold_Regression.ipynb` — 5 regression algorithms + MLflow
4. `4_Gold_Classification_&_Clustering.ipynb` — 5 classification & clustering algorithms + MLflow
5. `5_Evaluation_LIME_SHAP.ipynb` — Confusion matrix, ROC, LIME, SHAP
6. `6_Gold_Layer_Tableau.ipynb` — sklearn comparison, scaling, Tableau CSV export

## Requirements
- Databricks Community Edition (Classic cluster, NOT Serverless)
- PySpark 3.5+
- MLflow (pre-installed on Databricks)
