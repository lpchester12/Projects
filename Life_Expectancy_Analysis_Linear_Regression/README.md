# Life Expectancy Prediction using Linear Regression

This project investigates the factors influencing life expectancy using a dataset from kaggle provided by the World Health Organization (WHO). 
The analysis focuses on understanding various factors that infliences life expectancy across 193 countries between 2000 ~ 2015.

![Life Expectancy Header](https://c02.purpledshub.com/uploads/sites/41/2023/11/countries-in-the-world.jpg?w=1200)

---

## Problem Statement

To build an interpretable linear regression model that identifies the most significant predictors of life expectancy and provides insights that can help 
guide public health and policy decisions, especially in developing countries.

---

## Dataset Overview

- **Source**: [Kaggle – Life Expectancy (WHO) Dataset](https://www.kaggle.com/datasets/kumarajarshi/life-expectancy-who)
- **Observations**: 2,938 rows from 193 countries over multiple years (2000–2015)
- **Target**: Life Expectancy
- **Features**: The dataset contains 22 clinical, behavioral, and socioeconomic variables

---

## Data Cleaning
   - Imputed missing values using median (based on skewed distributions)
   - Removed high-leverage outliers using Cook's distance

---

## Exploratory Data Analysis (EDA)
   - Univariate and bivariate analysis
   - Distribution plots, correlation matrix, and scatterplots

---

## Feature Engineering
   - Log transformation of skewed numeric variables
   - Dummy encoding of categorical variables

---

## Model Building
   - Multiple linear regression using statsmodels
   - Feature elimination based on VIF and p-values
   - Assumption testing (all satisfied):
     - Linearity and independence (residuals vs. fitted)
     - Multicollinearity (VIF)
     - Normality (QQ plot, Shapiro-Wilk)
     - Homoscedasticity (Goldfeld-Quandt test)
---

## Model Evaluation**
   - Train-test split (70:30)
   - Performance metrics: RMSE, MAE, R-squared, Adjusted R-squared, MAPE

---

## Model Performance

| Dataset       | R-squared | Adjusted R-squared | RMSE    | MAE     | MAPE    |
|---------------|-----------|--------------------|---------|---------|---------|
| Training Set  | 0.84964   | 0.84846            | 0.05128 | 0.03929 | 0.93005 |
| Test Set      | 0.87241   | 0.87005            | 0.04759 | 0.03625 | 0.85934 |

- Final model explains approximately 85% of the variance in life expectancy (R-squared = 0.85)

---

## Tools and Libraries

- Python (Pandas, NumPy)
- Matplotlib, Seaborn
- Statsmodels
- Scikit-learn
- Scipy

---

## Conclusions & Insights

- HIV/AIDS prevalence has the strongest negative impact on life expectancy.
- Higher income composition, schooling, GDP, and vaccination rates are strongly associated with increased life expectancy.
- Public health investments and educational attainment are criticalc for improving population health.
- Improving these areas, especially in developing countries, can improve general public health.
