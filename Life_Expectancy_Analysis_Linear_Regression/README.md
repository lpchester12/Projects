# Life Expectancy Regression Analysis

![Life Expectancy Header](https://c02.purpledshub.com/uploads/sites/41/2023/11/countries-in-the-world.jpg?w=1200)

A comprehensive machine learning project for predicting global life expectancy using World Health Organization data, with a focus on identifying key factors influencing public health outcomes across developed and developing countries.

## Dataset
- **Source**: World Health Organization (WHO) Global Health Observatory (from Kaggle)
- **URL**: https://www.kaggle.com/datasets/kumarajarshi/life-expectancy-who/data
- **Coverage**: 2000-2015 data from 193 countries
- **Features**: 22 variables including health indicators, economic factors, immunization coverage, and social determinants
- **Target**: Life expectancy in years

## Key Variables
- **Health Indicators**: Adult mortality, infant deaths, HIV/AIDS prevalence
- **Economic Factors**: GDP, health expenditure percentage
- **Immunization**: Hepatitis B, Polio, Diphtheria coverage
- **Social Determinants**: Schooling, income composition, BMI
- **Nutrition**: Thinness prevalence in children/adolescents

## Methodology

### Data Preprocessing
- Missing value imputation using median/mean strategies
- Outlier analysis with Cook's Distance for influential point removal
- Log transformation for highly skewed features
- Feature scaling for neural network models

### Statistical Analysis
- Comprehensive EDA with univariate and bivariate analysis
- Statistical hypothesis testing (Kruskal-Wallis test)
- t-SNE visualization for country status clustering
- Linear regression with assumption validation (VIF, normality, homoscedasticity)

### Model Development
- **Linear Models**: OLS Regression, Ridge, Lasso, ElasticNet
- **Tree-Based**: Random Forest, Gradient Boosting, XGBoost
- **Advanced Boosting**: LightGBM, CatBoost, HistGradientBoosting
- **Neural Networks**: Multi-layer Perceptron (MLP)
- **Ensemble**: Stacking Regressor with multiple base learners

## Results

### Best Model: LightGBM Regressor
- **Test R²**: 96.76%
- **Test RMSE**: 1.24 years
- **Test MAE**: 0.89 years
- **Test MAPE**: 1.54%

### Key Findings (SHAP Analysis)
1. **HIV/AIDS prevalence** - Strongest negative predictor
2. **Income composition** - Most influential positive factor
3. **Adult mortality** - Major negative impact
4. **Schooling** - Strong positive correlation
5. **Under-five deaths** - Significant negative predictor

### Statistical Model Insights
Linear regression revealed statistically significant relationships:
- **Negative factors**: Adult mortality (-1.39%), HIV/AIDS (-8.80%), infant deaths (-1.0%)
- **Positive factors**: Income composition (+14.70%), schooling (+0.80%), GDP (+0.27%)
- **Developing countries** showed consistently lower life expectancy (-1.19%)

## Model Performance Comparison
### Model Performance Comparison (Life Expectancy Prediction)

| Model                     | R-Squared | Adj R-Squared |   RMSE   |   MAE    |  MAPE   |
|--------------------------|-----------|----------------|----------|----------|---------|
| HistGradientBoosting     | 0.95545   | 0.95388        | 1.96241  | 1.26477  | 1.91175 |
| CatBoost Regressor       | 0.95851   | 0.95705        | 1.89381  | 1.24544  | 1.86052 |
| LightGBM Regressor       | 0.96423   | 0.96297        | 1.75845  |1.11792   | 1.67555 |
| MLP Regressor            | 0.94123   | 0.93916        | 2.25399  | 1.58401  | 2.36880 |
| Stacking Regressor       | 0.95900   | 0.95755        | 1.88272  | 1.22631  | 1.84376 |


## Key Insights for Policy

### High-Impact Interventions
- **HIV/AIDS prevention and treatment** programs
- **Education system** improvements (schooling years)
- **Income inequality** reduction initiatives
- **Healthcare infrastructure** development

### Country-Specific Strategies
- **Developed countries**: Focus on lifestyle factors and healthcare quality
- **Developing countries**: Prioritize basic healthcare, education, and economic development

## Dependencies
```python
pandas, numpy, scikit-learn, statsmodels, scipy
lightgbm, xgboost, catboost, shap
matplotlib, seaborn, plotly
```

## Usage
1. Load and preprocess WHO health data
2. Apply statistical analysis and visualization
3. Train ensemble of regression models
4. Generate predictions with confidence intervals
5. Interpret results using SHAP values

## Conclusion
This analysis successfully identifies the most critical factors influencing global life expectancy, providing actionable insights for improving public health outcomes. The high model accuracy (96.76% R²) demonstrates strong predictive capability for policy simulation and healthcare planning.

---
*Note: This model is for research and policy guidance. Health decisions should involve qualified public health professionals and consider local context.*
