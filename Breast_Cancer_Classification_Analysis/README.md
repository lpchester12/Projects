# Breast Cancer Survival Risk Socre Prediction (SEER Dataset)

![Breast Cancer Header](https://www.sysmex.co.uk/fileadmin/_processed_/a/9/csm_LifeScience_StageImage_BreastCancer_1500x600-01_2498abd1e0.jpg)

A machine learning project for predicting breast cancer survival outcomes using the SEER dataset, with a focus on developing a clinical risk scoring system.

## Dataset
- **Source**: SEER Program (Surveillance, Epidemiology, and End Results) - National Cancer Institute
- **Patients**: 4,024 female patients diagnosed with infiltrating duct and lobular carcinoma (2006-2010)
- **Features**: 16 variables including tumor characteristics, staging, demographics, and survival data

## Methodology

### Data Analysis
- Comprehensive EDA with univariate and bivariate analysis
- Statistical hypothesis testing (Mann-Whitney U, Chi-square tests)
- Data visualization using t-SNE and UMAP for cluster analysis

### Feature Engineering
- **Node_Positive_Ratio**: Ratio of positive to examined lymph nodes
- **Tumor_Severity**: Tumor size weighted by grade
- **Risk Thresholds**: Age >55, Node Positive ≥5, Tumor Size >40

### Model Development
- **Algorithms Tested**: 7 ML models (Random Forest, CatBoost, AdaBoost, XGBoost, etc.)
- **Resampling**: 8 techniques including SMOTE-NC, ENN, Tomek Links
- **Hyperparameter Tuning**: RandomizedSearchCV with 50 iterations and 5 folds

## Results

### Best Model: CatBoost + ENN Resampling
- **ROC-AUC**: 87.41%
- **Mean Risk Scores**: 
  - Alive patients: 12.67 (Low risk)
  - Dead patients: 62.91 (Moderate-high risk)

### Risk Categories
- **Low Risk** (0 ~ 25): Standard monitoring
- **Low-Moderate Risk** (26 ~ 50): Regular follow-ups
- **Moderate-High Risk** (51 ~ 75): Enhanced monitoring
- **High Risk** (75+): Immediate intervention

## Key Features (SHAP Analysis)
1. **Survival Months** - Most important predictor
2. **Node_Positive_Ratio** - Engineered feature showing lymph node involvement
3. **Grade** - Tumor differentiation level
4. **Age** - Patient age at diagnosis
5. **N Stage** - Nodal staging

## Clinical Application
The model provides risk scores that can guide:
- Treatment intensity decisions
- Personalize treatment
- Better resource allocation
- Patient monitoring frequency

## Dependencies
```python
pandas, numpy, scikit-learn, catboost, xgboost, lightgbm
imblearn, shap, matplotlib, seaborn, scipy, umap-learn
```

## Usage
1. Load and preprocess the SEER breast cancer dataset
2. Apply feature engineering transformations
3. Train the CatBoost + ENN pipeline
4. Generate risk scores for new patients using `calculate_risk_score()`

## Conclusion
This analysis successfully develops a clinically-relevant risk scoring system with 87.41% ROC-AUC performance, enabling healthcare providers to make data-driven decisions for breast cancer patient management.

---
*Note: This model is for research purposes. Clinical decisions should always involve qualified healthcare professionals.*
