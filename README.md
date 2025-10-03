# Diabetes Risk Prediction Model

## 🩺 Project Overview

This project develops a comprehensive machine learning solution for predicting diabetes risk using the CDC Diabetes Health Indicators Dataset. By analyzing lifestyle choices, physical health indicators, and demographic factors, we aim to identify individuals at high risk of developing diabetes to enable early intervention and preventive healthcare initiatives.

## 🎯 Business Question

**How do lifestyle choices and physical health indicators correlate with diabetes risk?**

Our analysis explores the relationships between various health factors and diabetes diagnosis, building predictive models to identify at-risk individuals before symptoms develop.

## 📊 Dataset Information

### Source
- **Dataset**: CDC Diabetes 012 Health Indicators BRFSS 2015
- **Source**: [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/891/cdc+diabetes+health+indicators)
- **Size**: 253,680 instances with 21 features
- **Type**: Behavioral Risk Factor Surveillance System (BRFSS) telephone survey data

### Key Features

| Category | Variables |
|----------|-----------|
| **Demographics** | Age, Gender, Race, Education, Income |
| **Health Indicators** | BMI, General Health Rating, Physical/Mental Health Days |
| **Lifestyle Factors** | Smoking, Alcohol Consumption, Physical Activity, Diet |
| **Pre-existing Conditions** | High Blood Pressure, High Cholesterol, Heart Disease, Stroke |
| **Healthcare Access** | Insurance Coverage, Doctor Visits, Healthcare Cost |
| **Target Variable** | Diabetes Diagnosis (0: No Diabetes, 1: Pre-diabetes/Diabetes) |

## 🔧 Methodology

### 1. Data Preprocessing & Quality Assessment

#### Data Cleaning Steps:
- **Missing Values**: Dataset contained no missing values
- **Duplicates**: No duplicate records found
- **Data Types**: Verified all features had appropriate data types
- **Class Imbalance**: Addressed significant imbalance (84.3% No Diabetes vs 15.7% Diabetes)

#### Key Data Quality Considerations:
- Self-reported survey data (potential recall and social desirability bias)
- Bucketed continuous variables (Age, Income) reducing granularity
- Mix of categorical and numerical features requiring appropriate encoding

### 2. Exploratory Data Analysis (EDA)

#### Key Statistical Findings:
- **BMI Distribution**: Mean 28.38 (overweight category), heavily right-skewed
- **Age Distribution**: Broad distribution across all age categories
- **Mental/Physical Health Days**: Highly skewed with most reporting 0 days

#### Correlation Analysis Highlights:
- Strongest correlations with diabetes: High BP (0.27), High Cholesterol (0.30), BMI (0.22)
- Negative correlation with physical activity (-0.12)
- Age shows strong positive correlation (0.34)

### 3. Feature Engineering & Selection

Using Sequential Feature Selection (SFS), we identified 17 most informative features:
- Health indicators: HighBP, HighChol, CholCheck, BMI
- Lifestyle: Smoker, HeartDiseaseorAttack, Fruits, Veggies, HvyAlcoholConsump
- Healthcare: AnyHealthcare, GenHlth, MentHlth, DiffWalk
- Demographics: Sex, Age, Education, Income

### 4. Predictive Modeling

#### Models Tested:
1. **Logistic Regression**
2. **Decision Tree**
3. **Random Forest**
4. **XGBoost**

#### Class Imbalance Handling:
- **Undersampling**: Randomly reducing majority class
- **SMOTE**: Synthetic Minority Over-sampling Technique

#### Best Model Performance:
**Logistic Regression with Undersampling + Forward Feature Selection**
- **F1-Score**: 0.746
- **Accuracy**: 74.1%
- **Precision**: 72.9%
- **Recall**: 76.4%

The model prioritizes slightly higher false positives over false negatives, which is preferable in healthcare screening to ensure at-risk individuals receive further testing.

### 5. Prescriptive Modeling

Based on predicted risk levels, the system provides personalized recommendations:

**Low Risk (0-33%)**:
- Maintain healthy lifestyle
- Regular check-ups
- Monitor weight

**Medium Risk (34-66%)**:
- Increase physical activity
- Dietary modifications
- A1C screening recommendation

**High Risk (67-100%)**:
- Immediate medical consultation
- Comprehensive metabolic panel
- Lifestyle intervention program enrollment

## 📈 Key Insights

### 1. Top Health & Lifestyle Risk Factors
- **Physical Health**: High blood pressure (25% increased risk), high cholesterol (25% increased risk)
- **BMI Impact**: Obesity shows highest diabetes prevalence (26% vs 8% in normal weight)
- **Lifestyle**: Physical inactivity and poor diet significantly correlate with diabetes risk

### 2. Social Determinants of Health
- **Education**: Lower education levels show 40%+ diabetes prevalence
- **Income**: Inverse relationship - lower income correlates with higher diabetes rates
- **Healthcare Access**: Those without insurance show 16% higher diabetes rates

### 3. Model Performance Limitations
- Despite various techniques, F1-score plateaus around 0.75
- Survey bias and self-reporting limitations affect model accuracy
- Feature informativeness suggests need for clinical biomarkers for better prediction

## 🛠️ Technical Requirements

### Dependencies
```python
pandas>=1.3.0
numpy>=1.21.0
scikit-learn>=0.24.0
xgboost>=1.4.0
imbalanced-learn>=0.8.0
matplotlib>=3.4.0
seaborn>=0.11.0
scipy>=1.7.0
```

## 📊 Results & Evaluation

### Model Comparison

| Model | Accuracy | Precision | Recall | F1-Score |
|-------|----------|-----------|---------|----------|
| Logistic Regression (Undersample) | 73.96% | 74.01% | 73.96% | **73.95%** |
| Random Forest (Undersample) | 73.43% | 73.57% | 73.44% | 73.40% |
| XGBoost (SMOTE) | 71.26% | 61.43% | 69.30% | 61.51% |
| **Best Model (LR + SFS)** | **74.08%** | **72.94%** | **76.37%** | **74.62%** |

### Confusion Matrix (Best Model)
```
              Predicted
              No    Yes
Actual No   8621  3399
       Yes  2848  9119
```

## 🤝 Contributors

- **Quan Pham** - Exploratory Data Analysis, Data Wrangling, Machine Learning
- **Thi Nguyet Anh Che (Andrea)** - Project Coordination, Data Visualization, Machine Learning
- **Kaveh Jalilian** - Exploratory Data Analysis, Data Wrangling, Machine Learning
- **Yi-Fang Chung** - Reporting, Documentation, Data Visualization, Machine Learning

## 📚 References

1. CDC Diabetes Health Indicators Dataset - UCI Machine Learning Repository
2. American Diabetes Association - Standards of Medical Care in Diabetes
3. National Library of Medicine - Diabetes Prevention Studies
4. CDC - National Diabetes Statistics Report

## 🔮 Future Enhancements

1. **Clinical Biomarkers Integration**: Incorporate HbA1c, fasting glucose levels
2. **Longitudinal Analysis**: Track patient progression over time
3. **Deep Learning Models**: Explore neural networks for complex pattern detection
4. **Mobile Application**: Develop user-friendly risk assessment tool
5. **Real-time Monitoring**: Integrate with wearable health devices

## 📄 License

This project is developed for educational and research purposes. Please refer to the UCI Machine Learning Repository license for dataset usage terms.

---
