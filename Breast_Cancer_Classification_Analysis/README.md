# Breast Cancer Survival Prediction (SEER Dataset)

This project applies machine learning and deep learning techniques to predict survival outcomes in breast cancer patients. Using real-world clinical data from the SEER registry, the study identifies key predictors of survival and develops interpretable, high-performing models suitable for healthcare decision-making.

![Breast Cancer Header](https://www.sysmex.co.uk/fileadmin/_processed_/a/9/csm_LifeScience_StageImage_BreastCancer_1500x600-01_2498abd1e0.jpg)

---

## Problem Statement

Breast cancer is the most commonly diagnosed cancer among women. Predicting patient survival is critical for treatment planning and resource allocation. This study uses data from 4,024 patients diagnosed with infiltrating duct and lobular carcinoma (2006–2010) to:

- Identify clinical and demographic predictors of survival
- Build and evaluate multiple classification models
- Interpret model performances to select the best model

---

## Dataset Overview

- **Source**: [SEER Breast Cancer Dataset – IEEE DataPort](https://ieee-dataport.org/open-access/seer-breast-cancer-data)  
- **Observations**: 4,024 patients  
- **Features**: 15 clinical and demographic variables (excluding Unnamed: 3)
- **Target**: Survival status (Alive / Dead)  

---

## Exploratory Data Analysis and Hypothesis Testing

- Comprehensive univariate and bivariate analysis (histograms, boxplots, stacked bar plots)
- Hypothesis testing:
  - Mann–Whitney U test for numerical variables
  - Chi-square test for categorical variables
- All the variables except for Regional Node Examined show statistically significant differences (p < 0.05) between survival/dead groups

---

## Preprocessing Steps

- **Encoding**:
  - OrdinalEncoder for ordered categories (T Stage, N Stage, 6th Stage, Grade)
  - OneHotEncoder for nominal variables
- **Scaling**:
  - StandardScaler for numeric features
- **Class Imbalance Handling**:
  - Class weights
  - Weighted base estimators (for Bagging and AdaBoost)
  - Scale position weight (for XGBoost)

---

## Models Evaluated

| Model                  |
|------------------------|
| Logistic Regression    |
| Support Vector Machine |
| Decision Tree          |
| Random Forest          |
| Extra Trees            |
| AdaBoost               |
| Bagging Classifier     |
| HistGradient Boosting  |
| XGBoost                |
| Stacking Classifier    |
| MLP Classifier         |
| Keras Neural Network   |

---

## Model Optimization Techniques
- Cross-validation (Stratified 5-Fold)
- Hyperparameter tuning using RandomizedSearchCV and KerasTuner
- Threshold tuning using Precision-Recall
- Feature selection

---

## Model Performance (Test Set)

| Model                  | Accuracy | Precision | Recall | F1 Score |
|------------------------|----------|-----------|--------|----------|
| Random Forest          | 0.893    | 0.905     | 0.977  | 0.939    |
| Bagging                | 0.896    | 0.905     | 0.979  | 0.941    |
| HistGradient Boosting  | 0.907    | 0.916     | 0.979  | 0.947    |
| XGBoost                | 0.903    | 0.911     | 0.981  | 0.945    |
| Stacking               | 0.892    | 0.908     | 0.971  | 0.938    |
| MLP Classifier         | 0.896    | 0.906     | 0.978  | 0.941    |
| Keras                  | 0.899    | 0.911     | 0.977  | 0.943    |

---

**Final Model**: HistGradient Boosting  
Selected for its strong recall, balanced precision, interpretability (SHAP), and computational efficiency.

---

## Key Findings

- **Top Predictive Features** (based on SHAP values):
  - Survival Months
  - Age
  - Regional Node Positive
  - Grade

---

## Confusion Matrix (Test Set)

|                  | Predicted: Dead | Predicted: Alive |
|------------------|------------------|-----------------|
| Actual: Dead     | 62 (7.70%)        | 61 (7.58%)     |
| Actual: Alive    | 15 (1.86%)        | 667 (82.86%)   |

- **Recall**: 97.9 percent  
- **Precision**: 91.6 percent
- **True Positive Rate**: 82.86 percent (667/805)
- **False Negative Rate**: 1.86 percent (15/805)
- **Precision-Recall AUC**: 96.97 percent
  

---

## Tools and Libraries

- Python: pandas, numpy, scikit-learn, matplotlib, seaborn
- Modeling: XGBoost, HistGradientBoosting, BaggingClassifier, MLPClassifier
- Deep Learning: Keras, TensorFlow
- Interpretation: SHAP

---

## Conclusion

This project demonstrates the effective application of machine learning and deep learning to clinical survival prediction. The final model, HistGradient Boosting, showed a 97.9 percent recall with low false negative rates (1.86 percent), making it well-suited for clinical use where high sensitivity is essential. This model could assist clinicians in early intervention strategies with prioritizing the resources.
