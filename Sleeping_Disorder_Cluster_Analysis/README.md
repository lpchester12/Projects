# Sleep Disorder Cluster Analysis

![Sleeping Disorder Header](https://reverehealth.com/_next/image/?url=https%3A%2F%2Frevere-health.hqdemo.app%2Fwp-content%2Fuploads%2FiStock_41704022_LARGE.jpg&w=2048&q=75)

An unsupervised machine learning project analyzing patterns in sleep apnea and insomnia patients using clustering techniques to identify distinct behavioral and physiological profiles for personalized treatment strategies.

## Dataset
- **Source**: Sleep Health and Lifestyle Dataset (Kaggle)
- **URL**: https://www.kaggle.com/datasets/uom190346a/sleep-health-and-lifestyle-dataset
- **Patients**: 155 individuals with confirmed sleep disorders
- **Conditions**: Sleep Apnea (50.3%) and Insomnia (49.7%)
- **Features**: 13 variables including demographics, sleep metrics, lifestyle factors, and health indicators

## Key Variables
- **Demographics**: Age, Gender, Occupation, BMI Category
- **Sleep Metrics**: Sleep Duration, Quality of Sleep
- **Lifestyle**: Physical Activity Level, Daily Steps, Stress Level
- **Health Indicators**: Heart Rate, Blood Pressure (Systolic/Diastolic)
- **Target**: Sleep Disorder Type (Sleep Apnea vs Insomnia)

## Methodology

### Data Preprocessing
- Blood pressure feature engineering (split into Systolic/Diastolic)
- Removal of patients without confirmed sleep disorder diagnosis
- StandardScaler normalization for clustering algorithms

### Clustering Analysis
- **K-Means Clustering**: Elbow method and silhouette analysis for optimal k
- **Hierarchical Clustering**: Cophenetic correlation evaluation across distance metrics and linkage methods
- **Cluster Validation**: Silhouette scores and visual inspection

### Visualization
- **PCA**: 3-component analysis explaining 90% variance
- **t-SNE**: 2D visualization with perplexity optimization
- **Cluster Profiling**: Mean feature analysis by cluster

## Results

### Optimal Clustering: Hierarchical (k=4)
- **Method**: Euclidean distance with average linkage
- **Cophenetic Correlation**: 0.91 (excellent preservation of original distances)
- **Validation**: Superior separation in t-SNE visualization

### Cluster Profiles

**Cluster 0 - Mixed Insomnia Group** (85 patients)
- Middle-aged adults (42.3 years)
- Moderate sleep patterns (6.6 hrs, quality 6.4)
- Average activity and stress levels
- **Dominant**: Teachers and salespeople with high insomnia rates

**Cluster 1 - Healthy Sleep Apnea** (36 patients)
- Oldest group (55.8 years) with excellent sleep (8.0 hrs, quality 8.8)
- High physical activity, lowest stress (3.3)
- **Dominant**: Nurses with sleep apnea, no insomnia cases

**Cluster 2 - High-Stress Active** (30 patients)
- Adults (49.8 years) with shortest sleep (6.1 hrs)
- Highest physical activity (90.0) and stress (8.0)
- Elevated blood pressure (140.0/95.0)
- **Mixed**: Balanced sleep disorder distribution

**Cluster 3 - Young Healthy** (4 patients)
- Youngest group (33.0 years) with good sleep (7.0 hrs, quality 7.3)
- Lowest blood pressure (117.5/77.5)
- **Dominant**: Nurses with sleep apnea

### Key Findings
1. **Age Patterns**: Sleep apnea more common in older adults, insomnia in younger
2. **Occupational Clustering**: Nurses predominantly have sleep apnea; teachers/salespeople show high insomnia rates
3. **Activity Paradox**: High physical activity can coexist with sleep disorders and high stress
4. **Sleep Quality Gap**: Insomnia patients consistently report lower sleep quality and duration

## Cluster Validation Results
| Method | Metric | Score |
|--------|--------|-------|
| K-Means | Silhouette Score | 0.60 |
| Hierarchical | Cophenetic Correlation | 0.91 |
| t-SNE | Visual Separation | Excellent |

## Clinical Applications

### Personalized Treatment Strategies
- **Cluster 0**: Focus on stress management and sleep hygiene for insomnia
- **Cluster 1**: Maintain current lifestyle, monitor sleep apnea progression
- **Cluster 2**: Stress reduction despite high activity levels
- **Cluster 3**: Preventive care and lifestyle maintenance

### Healthcare Resource Allocation
- Target interventions based on occupational clustering patterns
- Develop age-specific sleep disorder screening protocols
- Design activity-appropriate treatment plans

## Dependencies
```python
pandas, numpy, scikit-learn, scipy
matplotlib, seaborn, yellowbrick
```

## Usage
1. Load and preprocess sleep health dataset
2. Apply feature scaling and clustering algorithms
3. Validate optimal cluster number using multiple metrics
4. Generate cluster profiles and visualizations
5. Interpret results for clinical decision-making

## Files
- `sleep_disorder_clustering.ipynb` - Complete analysis notebook
- `requirements.txt` - Python dependencies
- `data/` - Sleep health dataset

## Key Insights for Healthcare

### Treatment Personalization
- **Occupation-based interventions** for high-risk professions
- **Age-stratified approaches** for different sleep disorders
- **Activity-level considerations** in treatment planning

### Prevention Strategies
- Early screening for occupational risk groups
- Stress management programs for high-activity individuals
- Sleep hygiene education for younger adults

## Conclusion
This clustering analysis successfully identified four distinct patient profiles among sleep disorder patients, revealing strong patterns between occupation, age, lifestyle factors, and sleep disorder types. The 91% cophenetic correlation demonstrates excellent cluster validity, providing a robust foundation for developing targeted, personalized treatment approaches in sleep medicine.

---
*Note: This analysis is for research purposes. Clinical decisions should involve qualified sleep medicine specialists and consider individual patient circumstances.*
