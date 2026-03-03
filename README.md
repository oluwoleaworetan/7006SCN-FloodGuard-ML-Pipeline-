# 🌊 FloodGuard Insurance Analytics
### Scalable ML Pipeline for Flood Claim Prediction using PySpark on Databricks

**Module:** 7006SCN — Machine Learning and Big Data
**University:** Coventry University | MSc Data Science
**Student:** [YOUR NAME] ([YOUR SID])
**Date:** March 2026

---

## 📋 Project Overview

This project implements an end-to-end distributed machine learning pipeline
for predicting flood insurance claim severity using PySpark on Databricks.
The pipeline follows the **Medallion Architecture** (Bronze → Silver → Gold)
and trains **14 ML algorithms** across regression, classification, and
clustering tasks.

### Key Results
| Task | Best Model | Metric | Score |
|------|-----------|--------|-------|
| Regression | Random Forest | RMSE | $31,400 |
| Classification | GBT | AUC-ROC | 0.897 |
| Clustering | PCA + K-Means | Silhouette | 0.445 |

---

## 📊 Dataset

- **Source:** FEMA NFIP Redacted Claims v2 (Data.gov)
- **URL:** https://www.fema.gov/openfema-data-page/fima-nfip-redacted-claims-v2
- **Size:** 1.5+ GB | 2.7M+ rows | 39 columns
- **Licence:** U.S. Public Domain

---

## 🏗️ Architecture: Medallion Pattern

```
Bronze Layer          Silver Layer           Gold Layer
(Raw Ingestion)       (Feature Engineering)  (ML Training)
     │                      │                     │
sc.textFile()    →    Type casting      →    14 ML models
header=rdd.first()    Broadcast join         MLflow tracking
map(clean_row)        11 new features        CrossValidator
toDF()                StandardScaler         LIME / SHAP
save Parquet          persist()              Tableau CSV export
```

---

## 📁 Repository Structure

```
project/
├── notebooks/                    # 7 Databricks notebooks
│   ├── 1_bronze_ingestion.ipynb    # RDD ingestion → Parquet
│   ├── 2_Silver_Cleaning_EDA.ipynb — Cleaning, feature engineering, scaling
│   ├── 3_gold_regression.ipynb     # 5 regression algorithms
│   ├── 4_Gold_Classification_&_Clustering.ipynb — 5 classification & clustering algorithms + MLflow
│   ├── 5_Evaluation_LIME_SHAP.ipynb — Confusion matrix, ROC, LIME, SHAP
│   ├── 66_Gold_Layer_Tableau.ipynb — sklearn comparison, scaling, Tableau CSV export
│
├── tableau/
│   └── README_tableau.md           # Tableau dashboard guide
├── scripts/
│   ├── setup_environment.sh
│   └── run_pipeline.py
├── config/
│   ├── spark_config.yaml
│   └── tableau_config.json
├── data/
│   ├── schemas/
│   └── samples/
├── tests/
│   └── test_pipeline.py
├── .gitignore
├── environment.yml
├── Dockerfile
└── README.md
```

---

## 🚀 How to Run

### Prerequisites
- Databricks Community Edition account
- Classic cluster (NOT Serverless) with PySpark 3.5+

### Steps
1. Clone or download this repository
2. Upload the 7 notebooks to your Databricks Workspace
3. Attach a Classic cluster to each notebook
4. Run notebooks **in order** (1 → 2 → 3 → 4 → 5 → 6 → 7)
5. Download Gold CSV outputs and upload to Tableau Public

---

## 📈 Tableau Dashboards

**Tableau Public Link:** [INSERT YOUR TABLEAU PUBLIC URL HERE]

| Dashboard | Purpose |
|-----------|---------|
| Dashboard 1 | Data Quality & Pipeline Monitoring |
| Dashboard 2 | Model Performance & Feature Importance |
| Dashboard 3 | Business Insights & Recommendations |
| Dashboard 4 | Scalability & Cost Analysis |

---

## 🔬 Algorithms Implemented (14 Total)

### Regression (5)
1. Linear Regression
2. Decision Tree Regressor
3. Random Forest Regressor
4. Gradient Boosted Trees (GBT)
5. Elastic Net

### Classification (5)
1. Logistic Regression
2. Decision Tree Classifier
3. Random Forest Classifier
4. GBT Classifier
5. Linear SVC

### Clustering (4)
1. K-Means
2. Bisecting K-Means
3. Gaussian Mixture Model (GMM)
4. PCA + K-Means

---

## 🛠️ Technical Features
- ✅ RDD-based parallel data ingestion
- ✅ Parquet columnar storage (3x compression)
- ✅ Broadcast join (8-row lookup → 2.7M-row table)
- ✅ Custom Transformer (FloodRiskScorer)
- ✅ MLflow experiment tracking for all 14 models
- ✅ CrossValidator with 3-fold CV and parallelism=4
- ✅ LIME-like and SHAP-like Spark-only explainability
- ✅ sklearn single-node baseline comparison
- ✅ Weak scaling analysis (10% → 100%)
- ✅ GPU scalability hooks (Enterprise Edition only)

---

## 📚 References

See the report for full APA 7th edition references.

---

## 📄 Licence

This project is submitted as coursework for 7006SCN at Coventry University.
The FEMA dataset is released under U.S. Public Domain.
