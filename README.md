# churn-prediction-business-insights
# Customer Churn Prediction (Telecom) | Data Science Project

## Overview
This project focuses on predicting **customer churn** in a telecom business using customer demographics, subscription patterns, and service usage information.  
The goal is not only to build an accurate churn prediction model but also to generate **actionable business insights** that can help reduce churn via targeted retention strategies.

---

## Problem Statement
Customer churn directly impacts revenue and growth in subscription-based businesses.  
This project aims to:
- Predict whether a customer will churn (**Yes/No**)
- Identify key churn drivers
- Create a churn-risk scoring list for retention targeting
- Recommend business strategies to minimize churn

---

## Dataset
- Records: **5,043 customers**
- Features: **22 columns**
- Target variable: **Churn**

### Key columns
- Customer profile: `gender`, `SeniorCitizen`, `Partner`, `Dependents`
- Customer relationship: `tenure`
- Services: `InternetService`, `OnlineSecurity`, `TechSupport`, `StreamingTV`, etc.
- Billing: `MonthlyCharges`, `TotalCharges`, `PaymentMethod`
- Target: `Churn`

---

## Data Preprocessing & Cleaning
Key data preparation steps:
- Removed non-informative identifiers (`customerID`)
- Standardized target variable:
  - Converted mixed values such as `Yes/No/True/False` into a consistent churn label
- Converted `TotalCharges` to numeric:
  - Used `to_numeric(errors="coerce")` and handled null values
- Handled missing values across categorical features (e.g., `MultipleLines`, `OnlineSecurity`, `StreamingTV`, etc.)

---

## Exploratory Data Analysis (EDA)
EDA was performed to understand churn patterns and customer behavior.

### Key EDA insights
- **Senior citizens** exhibit higher churn tendency
- Customers who are **single (no partner)** churn more often
- Customers with **no dependents** (independent users) show higher churn risk
- Customers with **low/no Online Security** show significantly higher churn

These insights indicate churn is influenced by both customer segment patterns and perceived service protection (security/support add-ons).

---

## Modeling Approach
A robust machine learning pipeline was built using:
- `ColumnTransformer` for column-wise preprocessing
- `OneHotEncoder` for categorical variables
- Train-test split with stratification to preserve class distribution

### Models trained
1. **Logistic Regression (Baseline)**
2. **Random Forest (Improved Model)**

### Evaluation Metrics
Models were evaluated using:
- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- Confusion Matrix + ROC Curve

---

## Explainability (Feature Importance)
Feature importance analysis was performed to interpret churn drivers.  
Top churn drivers were aligned with EDA findings (contract type, security/support services, and customer relationship indicators like tenure).

---

## Business Layer (Actionable Output)
To make the project business-ready, the model output was converted into operational retention actions:

### 1) Churn Risk Scoring
Each customer was assigned a **Churn Probability Score**, enabling ranking of customers based on churn risk.

### 2) Retention Target List
Generated a list of **Top high-risk churn customers** for retention teams (campaign prioritization).

### 3) Retention Playbook (Recommended Actions)
Based on churn insights, recommended strategies include:
- Offer **contract upgrade discounts** to high-risk month-to-month customers
- Bundle/add **Online Security** at discounted/free trial for customers without security
- Provide proactive support strategies for **senior citizens** and low-tenure customers

### 4) Business Impact Estimation (ARPU-based)
Estimated revenue impact using:
- ARPU (Average Revenue Per User) derived from monthly charges
- retention save-rate assumption for targeted high-risk customers

This converts the ML model into a measurable business value pipeline.

---

## Project Structure
``` bash
│
├── notebooks/
│ ├── EDA.ipynb
│ └── Model.ipynb
│
├── outputs/
│ ├── model_metrics.csv
│ ├── top_200_churn_risk.csv
│ └── top_features.csv
│
├── requirements.txt
└── README.md
```
