# Customer Churn Prediction

End-to-end machine learning project to predict which telecom customers are likely to leave, with exploratory analysis, model comparison, explainability (SHAP) and a dashboard.

## Business problem
Acquiring a new customer costs far more than keeping an existing one. About 26.5% of customers in this dataset churn. The goal is to identify at-risk customers early so the company can act (offers, calls, service fixes).

## Dataset
- **Source:** Telco Customer Churn (IBM sample data, Kaggle)
- **Size:** 7,043 customers, 21 columns
- **Target:** `Churn` (Yes/No)
- **Features:** demographics, services subscribed, contract type, billing, tenure
- **Note:** the dataset is not included in this repository. Download it from Kaggle and place it in `data/`.

## Project structure
```
churn-prediction/
├── data/          # raw dataset (not versioned)
├── notebooks/     # 01_eda, 02_modeling, ...
├── src/           # reusable code
├── models/        # saved models (not versioned)
├── reports/       # figures and results
└── README.md
```

## Methodology
1. Exploratory data analysis (distributions, churn by segment, correlations)
2. Data cleaning (`TotalCharges` converted to numeric, 11 missing values filled with 0)
3. Encoding and stratified train/test split (80/20)
4. Model training: Logistic Regression, Random Forest, XGBoost
5. Class imbalance handling (class weights)
6. Evaluation with recall, F1-score and ROC-AUC
7. Explainability with SHAP
8. Dashboard with Streamlit

## Key insights from the EDA
- The target is moderately imbalanced (about 2.8:1), so accuracy alone is misleading.
- **Contract type** is the strongest factor: month-to-month customers churn at 42.7% versus 2.8% for two-year contracts.
- **New customers** are the most at risk: churn is highest in the first months.
- Fiber optic, electronic check payment, and no tech support or online security are associated with higher churn.
- Higher monthly charges are associated with more churn.
- `TotalCharges` is strongly correlated with `tenure` (0.83), so it carries overlapping
