# Telco Customer Churn Prediction

## Overview

This project was completed as part of the Week 3 Data Science
Internship assignment on Feature Engineering, Model Building, and
Feature Scaling.

The objective is to predict customer churn using the IBM Telco
Customer Churn dataset and compare multiple machine learning
classification algorithms.

## Dataset

The project uses the IBM Telco Customer Churn dataset containing
customer demographic information, account details, subscribed
services, charges, and churn status.

Original records: 7,043  
Records after cleaning: 7,032

## Project Workflow

The project includes:

- Data inspection and preprocessing
- TotalCharges data-quality correction
- Removal of non-predictive identifiers
- Target class analysis
- Feature engineering
- Categorical encoding
- StandardScaler and MinMaxScaler
- Stratified train/test splitting
- Multiple classification algorithms
- 5-fold stratified cross-validation
- Model evaluation and comparison

## Engineered Features

Four additional features were created:

- AvgMonthlySpend
- ContractCommitment
- ServiceCount
- ChargeCommitmentInteraction

## Machine Learning Models

Five classification algorithms were evaluated:

1. Logistic Regression
2. K-Nearest Neighbors
3. Support Vector Machine
4. Decision Tree
5. Random Forest

## Evaluation Metrics

Models were evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- 5-fold Cross-Validation F1-score

## Results

| Model | Accuracy | Precision | Recall | F1 | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| Logistic Regression | 0.8038 | 0.6503 | 0.5668 | 0.6057 | 0.8363 |
| Random Forest | 0.7854 | 0.6169 | 0.5080 | 0.5572 | 0.8224 |
| Support Vector Machine | 0.7974 | 0.6540 | 0.5053 | 0.5701 | 0.7827 |
| K-Nearest Neighbors | 0.7633 | 0.5553 | 0.5508 | 0.5530 | 0.7798 |
| Decision Tree | 0.7122 | 0.4608 | 0.4866 | 0.4733 | 0.6400 |

## Best Model

Logistic Regression achieved the strongest overall performance with:

- Accuracy: 80.38%
- Precision: 65.03%
- Recall: 56.68%
- F1-score: 60.57%
- ROC-AUC: 83.63%
- Mean Cross-Validation F1: 59.31%

Based on the experimental results and characteristics of the dataset,
Logistic Regression was selected as the preferred model.

## Repository Files

- `Telco_Customer_Churn_Week3.ipynb` - Complete analysis and modeling notebook
- `Telco_Customer_Churn_Week3_Report.pdf` - Written assignment report
- `WA_Fn-UseC_-Telco-Customer-Churn.csv` - Dataset
- `README.md` - Project documentation

## Tools and Libraries

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn

## Author

Data Science Internship Program - Week 3 Assignment
