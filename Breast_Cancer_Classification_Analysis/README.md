# Breast Cancer Survival Prediction (SEER Dataset)

This project applies machine learning and deep learning techniques to predict survival outcomes in breast cancer patients. Using real-world clinical data from the SEER registry, the study identifies key predictors of survival and develops interpretable, high-performing models suitable for healthcare applications.

![Breast Cancer Header](https://www.sysmex.co.uk/fileadmin/_processed_/a/9/csm_LifeScience_StageImage_BreastCancer_1500x600-01_2498abd1e0.jpg)

---

## Problem Statement

Breast cancer is the most commonly diagnosed cancer among women. Predicting patient survival is critical for treatment planning and resource allocation. This study uses data from 4,024 patients diagnosed with infiltrating duct and lobular carcinoma (2006–2010) to:

- Identify clinical and demographic predictors of survival
- Build and evaluate multiple classification models
- Interpret model performance in a clinically meaningful way

---

## Dataset Overview

- **Source**: [SEER Breast Cancer Dataset – IEEE DataPort](https://ieee-dataport.org/open-access/seer-breast-cancer-data)  
- **Observations**: 4,024 patients  
- **Features**: 15 clinical and demographic variables  
- **Target**: Survival status (Alive / Dead)  

---

## Exploratory Data Analysis and Hypothesis Testing

- Comprehensive univariate and bivariate analysis (histograms, boxplots, stacked bar plots)
- Hypothesis testing:
  - Mann–Whitney U test for numerical variables
  - Chi-square test for categorical variables
- Key variables such as tumor size, hormone receptor status, and cancer stage show statistically significant differences between survival groups

---

## Preprocessing Steps

- **Encoding**:
  - OrdinalEncoder for ordered categories (e.g., T Stage, Grade)
  - OneHotEncoder for nominal variables
- **Scaling**:
  - StandardScaler for numeric features
- **Class Imbalance Handling**:
  - Class weights
  - Scale position weight (for XGBoost)
  - Weighted base estimators (for Bagging and AdaBoost)

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
| MLP Classifier         |
| Keras Neural Network   |
| Stacking Ensemble      |

---

## Model Performance (Test Set)

| Model                  | Accuracy | Precision | Recall | F1 Score |
|------------------------|----------|-----------|--------|----------|
| Random Forest          | 0.893    | 0.905     | 0.977  | 0.939    |
| Bagging                | 0.896    | 0.905     | 0.979  | 0.941    |
| HistGradient Boosting  | 0.907    | 0.916     | 0.979  | 0.947    |
| XGBoost                | 0.903    | 0.910     | 0.982  | 0.945    |
| Stacking               | 0.901    | 0.908     | 0.982  | 0.944    |
| MLP Classifier         | 0.896    | 0.906     | 0.978  | 0.941    |
| Keras DNN              | 0.893    | 0.901     | 0.982  | 0.940    |

**Final Model**: HistGradient Boosting  
Selected for its strong recall, balanced precision, interpretability (SHAP), and computational efficiency.

---

## Key Findings

- **Top Predictive Features** (based on SHAP values):
  - Survival Months
  - Age
  - Regional Node Positive
  - Tumor Size
- Mortality is strongly associated with:
  - ER/PR-negative status
  - High-grade tumors (Grade IV)
  - Advanced stages (Stage IIIC and IV)
- Threshold adjustment significantly improved recall and reduced false negatives

---

## Confusion Matrix (Test Set)

|                  | Predicted: Alive | Predicted: Dead |
|------------------|------------------|------------------|
| Actual: Alive    | 667              | 15               |
| Actual: Dead     | 61               | 62               |

- **Recall**: 97.9 percent  
- **Precision**: 91.6 percent  
- **False Negative Rate**: 1.86 percent

---

## Tools and Libraries

- Python: `pandas`, `numpy`, `scikit-learn`, `matplotlib`, `seaborn`
- Modeling: `XGBoost`, `HistGradientBoosting`, `BaggingClassifier`, `MLPClassifier`
- Deep Learning: `Keras`, `TensorFlow`
- Interpretation: `SHAP`

---

## Conclusion

This project demonstrates the effective application of machine learning and deep learning to clinical survival prediction. The final model, HistGradient Boosting, achieved a recall of 97.9 percent with low false negative rates—making it well-suited for clinical use where high sensitivity is essential. The model's interpretability using SHAP values also enhances trust and applicability in medical settings.
