# Predicting-Customer-Retention-in-Banking-Using-Multimodal-Analytics
## Overview

Customer retention is a major challenge in the banking industry. Identifying customers who are likely to churn allows financial institutions to proactively intervene and improve long-term customer value.

This project builds machine learning models to predict customer churn using behavioral transaction data and applies clustering techniques to segment customers based on engagement patterns. The analysis combines supervised learning for churn prediction and unsupervised learning for behavioral segmentation. 

The project uses the MBD-mini dataset (a subset of the Million Business Dataset) containing anonymized client transaction and interaction data.

## Project Objectives:

Predict customer churn using transaction and behavioral data

Identify important behavioral indicators driving churn

Segment customers into behavioral groups using clustering techniques

Provide actionable insights for customer retention strategies

## Dataset:

The project uses the MBD-mini dataset from Hugging Face, which contains anonymized banking activity data. 

BA890 Project Paper

## Data Sources:

1. detail/

Timestamped interaction logs

event_type

event_subtype

src_type

amount

2. targets/

Client churn labels

target_1 – target_4 indicators

Data was merged on:

client_id
month

## Methodology - 
1. Data Preparation

Extracted behavioral activity features from event logs

Aggregated data to client-month level

Generated behavioral metrics such as:

transaction count

active days

days since last transaction

Merged with churn labels

2. Feature Engineering

Key engineered features included:

Number of transactions per month

Days since last transaction

Number of active days

Transaction frequency metrics

Numerical variables were standardized and missing values handled appropriately. 

Machine Learning Models
Baseline Models

Two baseline models were initially tested: Logistic Regression & Random Forest

Baseline performance:

F1 Score: ~0.68 – 0.73
Recall: ~0.74
Gradient Boosting Models

More advanced models were implemented:

LightGBM

XGBoost

Hyperparameter tuning was performed using GridSearchCV.

Best Model Performance (LightGBM)
F1 Score: 0.97
Recall: 0.94
ROC-AUC: 0.974

LightGBM also maintained strong performance using only the top 15 most important features, making it more efficient for deployment. 

Customer Segmentation (Clustering)

To better understand customer behavior patterns, clustering techniques were applied.

K-Means Clustering

PCA used for dimensionality reduction

Optimal clusters selected using Elbow Method

Optimal Clusters: 4
Silhouette Score: 0.22

Customer segments identified different engagement patterns such as: high activity users, moderate engagement users, dormant or low activity users. 

Additional Clustering Methods
DBSCAN / HDBSCAN

Tested for density-based clustering but performed poorly due to high-dimensional sparse data.

Agglomerative Clustering

Hierarchical clustering produced similar segmentation results and provided additional interpretability through dendrogram analysis. 

## Exploratory Data Analysis - 

Key insights from the analysis:

Transaction activity increased steadily over time, indicating growing engagement.

Certain clusters showed significantly higher transaction volumes.

Customer segments showed different propensities for triggering churn targets.

These insights help characterize customer groups for targeted retention strategies. 

## Key Findings: 

Strong Churn Prediction

LightGBM achieved high predictive performance:

ROC AUC: 0.974
Recall: 0.94
Key Drivers of Churn

Important predictors included:

Transaction frequency

Recency of transactions

Spending patterns

Meaningful Customer Segmentation

Clustering revealed four distinct behavioral segments with varying engagement and churn risk profiles. 

## Business Impact - 

Banks can use this framework to:

Identify at-risk customers early

Implement targeted retention campaigns

Improve customer engagement strategies

Optimize marketing resource allocation

## Future Improvements - 

Potential extensions for this project include:

Time-series modeling of transaction behavior

Linking clusters directly with churn probabilities

Implementing A/B testing for retention strategies

Deploying the churn prediction model into production pipelines. 

## Technologies Used - 

Python

Pandas

NumPy

Scikit-Learn

LightGBM

XGBoost

Matplotlib / Seaborn

PCA for dimensionality reduction

## Notebook - 

Colab notebooks used for this project:

https://colab.research.google.com/drive/1Qk59xEzFJLXxXcY4UCPqqZwYZA3tFxrN

https://colab.research.google.com/drive/1EJLoAoORahIL0C3EXudZJd2nDC77GqCG

## References

Bank Customer Churn Prediction Research Papers

Analytics Vidhya – Churn Prediction using ML

Academic literature on churn modeling and customer segmentation.
