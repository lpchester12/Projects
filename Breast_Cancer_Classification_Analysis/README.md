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
| Random Forest          | 0.896    | 0.915     | 0.966  | 0.940    |
| Bagging                | 0.893    | 0.922     | 0.955  | 0.948    |
| HistGradient Boosting  | 0.908    | 0.910     | 0.990  | 0.947    |
| XGBoost                | 0.896    | 0.913     | 0.969  | 0.940    |
| Stacking               | 0.897    | 0.903     | 0.984  | 0.942    |
| MLP Classifier         | 0.893    | 0.903     | 0.979  | 0.940    |
| Keras                  | 0.896    | 0.915     | 0.966  | 0.940    |

---

**Final Model**: HistGradient Boosting  
Selected for its highest recall, balanced precision, interpretability (SHAP), and computational efficiency.

---

## Key Findings

- **Top Predictive Features** (based on SHAP values):
  - Survival Months
  - Regional Node Positive
  - Age
  - Regional Node Examined
  - Tumor Size
  - Grade
  - 6th Stage

---

## Confusion Matrix (Test Set)

|                  | Predicted: Dead | Predicted: Alive |
|------------------|------------------|-----------------|
| Actual: Dead     | 56 (6.96%)        | 67 (8.32%)     |
| Actual: Alive    |  7 (0.87%)        | 675 (83.85%)   |

- **Recall**: 99.0 percent  
- **Precision**: 91.0 percent
- **True Positive Rate**: 83.85 percent (675/805)
- **False Negative Rate**: 0.87 percent (7/805)
- **Precision-Recall AUC**: 96.67 percent
  
---

## Major Tools and Libraries

- Python: pandas, numpy, scikit-learn, matplotlib, seaborn
- Modeling: XGBoost, HistGradientBoosting, BaggingClassifier, MLPClassifier
- Deep Learning: Keras, TensorFlow

---

## Conclusion

This project demonstrates the effective application of machine learning and deep learning to clinical survival prediction. The final model, HistGradient Boosting, showed almost perfect score of 99.0 percent recall with low false negative rates (0.87 percent), making it well-suited for clinical use where high sensitivity is essential. This model could assist clinicians in early intervention strategies with prioritizing the resources.
