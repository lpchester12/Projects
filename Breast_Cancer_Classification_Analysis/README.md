# Breast Cancer Survival Prediction (SEER Dataset)

This project analyzes breast cancer patient data from the SEER registry to predict survival outcomes using traditional machine learning and deep learning models. It includes thorough EDA, statistical validation, class imbalance handling, model comparison, and performance interpretation with clinical relevance.

![Breast Cancer Header](https://www.sysmex.co.uk/fileadmin/_processed_/a/9/csm_LifeScience_StageImage_BreastCancer_1500x600-01_2498abd1e0.jpg)

---

## Problem Statement

Breast cancer is the most frequently diagnosed cancer among women. Understanding survival factors is crucial for improving treatment strategies. This project explores data from 4,024 patients with infiltrating duct and lobular carcinoma from SEER (2006–2010) to identify key predictors of survival.

---

## Dataset

* **Source**: [SEER Breast Cancer Dataset - IEEE DataPort](https://ieee-dataport.org/open-access/seer-breast-cancer-data)
* **Features**: 15 clinical and demographic variables
* **Target**: Survival status (Alive / Dead)

---

## Exploratory Data Analysis

* Univariate and bivariate plots (histograms, boxplots, stacked barplots)
* Data type optimization (e.g., categorical conversion)
* Hypothesis Testing:

  * Mann–Whitney U test for numeric variables
  * Chi-Square test for categorical variables

---

## Preprocessing

* **Encoding**:

  * OrdinalEncoder for ordered categorical variables (e.g., tumor stage, grade)
  * OneHotEncoder for nominal variables
* **Scaling**: StandardScaler for numerical features
* **Imbalance Handling**:

  * Class weights for Group 1 models
  * Sample weights for boosting models

---

## Initail Models Compared

| Model               |
| ------------------- |
| Logistic Regression |
| SVM                 |
| Random Forest       |
| Extra Trees         |
| Decision Tree       |
| Bagging             |
| AdaBoost            |
| Gradient Boosting   |
| XGBoost             |
| Stacking Ensemble   |
| MLP Classifier      |
| Keras DNN           |

---

## Performance (Test Set)

| Model             | Accuracy | Precision | Recall | F1 Score |
| ----------------- | -------- | --------- | ------ | -------- |
| Random Forest     | 0.906    | 0.916     | 0.978  | 0.946    |
| Bagging           | 0.908    | 0.916     | 0.981  | 0.948    |
| Gradient Boosting | 0.908    | 0.909     | 0.991  | 0.948    |
| XGBoost           | 0.899    | 0.904     | 0.985  | 0.943    |
| Stacking Ensemble | 0.907    | 0.919     | 0.977  | 0.947    |
| MLP (Sklearn)     | 0.893    | 0.909     | 0.971  | 0.939    |
| Keras DNN         | 0.891    | 0.900     | 0.979  | 0.938    |

Final Model: **Random Forest with threshold tuning**

---

## Key Findings

* **Most important features**:

* Survival Months, Age, Regional Node Positive, Tumor Size
* **ER/PR-negative status**, **Grade IV**, and **Stage IIIC/IV** strongly correlate with higher mortality
* **Threshold tuning** greatly improved recall and balanced F1 score

---

## Confusion Matrix (Test Set)

|       | Pred: Alive | Pred: Dead |
| ----- | ----------- | ---------- |
| Alive | 667         | 15         |
| Dead  | 61          | 62         |

* **Recall**: 97.8% (excellent sensitivity)
* **Precision**: 91.6%
* **False Negative Rate**: Only 15 patients misclassified as deceased

---

## Tools Used

* Python (pandas, numpy, scikit-learn, seaborn, matplotlib)
* XGBoost
* Keras & TensorFlow
* Keras Tuner

___

## Conclusion 

This project demonstrates how clinical data can be used effectively to predict patient outcomes using advanced machine learning and deep learning models. Through careful data preprocessing, statistical validation, and model tuning, we achieved a recall of 97.8% with Random Forest, making it highly suitable for medical applications where minimizing false negatives is critical.
