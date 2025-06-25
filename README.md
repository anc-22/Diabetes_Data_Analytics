# Diabetes_Data_Analytics
Project Scope: An analysis of factors correlated with diabetes risk, along with predictive and prescriptive models to identify individuals who are at high risk of developing diabetes


Business Question
We aim to explore the relationship between lifestyle choices, physical health indicators, and the risk of diabetes. In particular, we will analyze factors such as physical activity, smoking, alcohol consumption, BMI, and other health indicators correlate with diabetes risk. Beside that, we will consider building a predictive model to identify individuals who are at high risk of developing diabetes based on these health indicators.

Diabetes is a significant public health concern, and early detection of risk factors can help preventative healthcare initiatives. Therefore, we hope that our findings could help public health organizations and medical professionals to reduce diabetes risk.

Data Source
We will be using the Diabetes 012 Health Indicators BRFSS 2015 dataset which is publicly available and was sourced from a reliable health survey.

The dataset provides the following factors:
•	Demographic variables (age, gender, race)
•	Physical health indicators (BMI, general health rating, physical activity levels)
•	Lifestyle factors (smoking, alcohol consumption, sleep patterns)
•	Pre-existing conditions (high blood pressure, cholesterol levels)
•	Diabetes diagnosis (target variable) 

The link to the dataset:
https://archive.ics.uci.edu/dataset/891/cdc+diabetes+health+indicators

Data Quality Concerns
 
The CDC Diabetes Health Indicators Dataset is a structured and publicly available dataset that includes 253,680 instances and 21 features covering demographic, lifestyle, and health-related factors. While this dataset is sourced from a reliable public health survey, there are still some potential data quality concerns that must be considered:
1. Categorical vs. Numerical Data Handling
The dataset includes a mix of categorical (e.g. Smoker, PhysActivity, Sex) and numerical (e.g. BMI, Mental Health Days) features.
Potential Issue: Some machine learning models perform better with numerical data, meaning categorical variables need to be encoded.
Solution:
·	Convert binary categorical features using label encoding (e.g. 0 = No, 1 = Yes).
·	Convert ordinal categorical variables (e.g. Education Level, Income, General Health Rating) to preserve ranking.
2. Class Imbalance in Diabetes Labels
The dataset classifies individuals into three categories: Healthy, Pre-diabetes, Diabetes
Potential Issue: There may be significantly fewer Pre-diabetes or Diabetes cases compared to Healthy individuals, leading to imbalanced classes, which can affect model accuracy.
Solution:
·	Use class-weight adjustments in models to prevent bias toward the majority class.
3. Survey Bias & Self-Reported Data
This dataset is based on self-reported survey responses for lifestyle habits (Smoking, Alcohol Consumption, Physical Activity).
Potential Issue: Responses may not be fully accurate due to recall bias or social desirability bias (people may underreport unhealthy behaviors).
Solution:
·	Acknowledge this as a limitation in our analysis.
·	Cross-reference with related health variables (e.g. BMI, blood pressure) to validate responses 
4. Bucketing of Continuous Variables (Age, Income)
The dataset buckets Age and Income into groups rather than providing continuous values.
Potential Issue: This reduces granularity and may limit the ability to detect subtle trends in different age or income levels.
Solution:
·	We can consider re-grouping categories into broader or more meaningful segments for analysis.
5. Outliers in BMI and Mental Health Indicators
Variables such as BMI, Mental Health Days, and Physical Health Days could contain extreme values.
Potential Issue: Outliers can skew regression and classification models.
Solution:
·	Detect outliers using boxplots and z-score analysis.
·	Transform data if necessary to improve model performance.

Methods
To analyze the relationship between lifestyle choices, physical health indicators, and diabetes risk, we will follow a structured analytical approach, including data preprocessing, exploratory data analysis (EDA), feature selection, and predictive modeling
1, Data preprocessing
-	Data cleaning: Address inconsistencies, duplicates and outliers using statistical techniques
-	Data transformation: Convert categorical variables into numerical representations and normalize continuous variables if necessary
2, Exploratory Data Analysis (EDA)
-	Perform descriptive statistics and visualizations to understand feature distributions and relationships
-	Identify correlations between health indicators and diabetes diagnosis
3, Feature Selection
-	Utilize correlation analysis, mutual information, and statistical tests to identify the most relevant predictors
-	Apply dimensionality reduction techniques if needed to enhance model efficiency
4, Predictive Modeling
-	Train machine learning models, such as logistic regression, decision trees, random forests, and neural networks, to predict diabetes risk
-	Use cross-validation to assess model performance and prevent overfitting
-	Evaluate models using accuracy, precision, recall, and F1-score metric

Challenges
Since our dataset is derived from the Behavioral Risk Factor Surveillance System (BRFSS) health-related telephone surveys, it may contain inconsistencies that require thorough data cleaning before performing any analysis or building predictive models. Additionally, with the large number of features in the dataset (including BMI, activity levels, and diet preferences), we will need to conduct comprehensive feature selection to identify the most relevant predictors for diabetes forecasting. Furthermore, it is important to address potential multicollinearity, as several features may exhibit similar correlations with prediabetic and diabetic diagnoses, which could affect the accuracy and interpretability of our models.

Team member contributions:

•	Quan Pham – Exploratory Data Analysis, Data Wrangling, Data Modeling/Machine Learning, Presenter.

•	Thi Nguyet Anh Che (Andrea) – Project Coordination, Data Wrangling, Data Visualization, Exploratory Data Analysis, Data Modeling/Machine Learning, Presenter.

•	Kaveh Jalilian – Exploratory Data Analysis, Data Wrangling, Data Visualization, Data Modeling/Machine Learning, Presenter.

•	Yi-Fang Chung – Reporting, Note Collection, PowerPoint Design, Data Visualization, Data Modeling/Machine Learning, Presenter.
