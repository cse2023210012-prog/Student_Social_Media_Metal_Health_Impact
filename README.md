# Student Mental Health Prediction Using Machine Learning

## Project Overview

This project analyzes the relationship between students' social media usage,
lifestyle factors, stress levels, and mental health.

The project uses machine learning classification models to predict students'
mental health category as:

- Fair
- Good
- Poor

The project includes Exploratory Data Analysis (EDA), data preprocessing,
three machine learning algorithms, hyperparameter tuning, and model
evaluation.

---

## Dataset

The dataset used in this project is:

**Student Social Media And Mental Health Impact**

The dataset contains information related to students' social media usage,
sleep, study habits, physical activity, stress level, and mental health score.

The original dataset is stored in:

```text
data/
└── Student Social Media And Mental Health Impact.csv

Project Workflow

Dataset
   ↓
Exploratory Data Analysis
   ↓
Data Preprocessing
   ↓
Create Mental Health Categories
   ↓
Feature Encoding
   ↓
Train/Test Split
   ↓
Machine Learning Models
   ├── Logistic Regression
   ├── Random Forest
   └── XGBoost
   ↓
Model Evaluation
   ↓
Model Comparison

Mental Health Classification

The original Mental_Health_Score was converted into three categories:

Score Range	Category
0–4	Poor
4–7	Fair
7–10	Good

The target variable was then encoded for machine learning.

The dataset has an imbalanced target distribution, with the Poor category
having substantially fewer samples than Fair and Good.

Exploratory Data Analysis

The EDA includes:

Dataset shape and structure
Column and data type inspection
Missing-value checking
Duplicate checking
Numerical feature distributions
Outlier checking using Z-score
Mental health category distribution
Stress level distribution across mental health categories

The EDA and preprocessing are available in:
notebooks/01_EDA_Preprocessing.ipynb

Machine Learning Models
1. Logistic Regression

Logistic Regression was used as a baseline classification model.

A pipeline was used with:

StandardScaler
Logistic Regression
Balanced class weights

GridSearchCV was used for hyperparameter tuning.

Best parameters:

C = 1
solver = lbfgs

2. Random Forest

Random Forest was trained using the Gini criterion.

The model used:

Class-balanced training
Gini impurity
GridSearchCV
5-fold cross-validation
Macro F1-score for model selection

Best parameters:

n_estimators = 100
max_depth = None
min_samples_split = 2
criterion = gini

3. XGBoost

XGBoost was trained as a multiclass classification model.

The model used:

Multi-class classification
Balanced sample weights
GridSearchCV
5-fold cross-validation
Macro F1-score for model selection

Best parameters:

n_estimators = 200
max_depth = 6
learning_rate = 0.01
Model Results

The models were evaluated using:

Accuracy
Precision
Recall
F1-score
Macro F1-score
Classification report
Overall Comparison
Model	Accuracy	Macro Precision	Macro Recall	Macro F1
Logistic Regression	73%	0.60	0.82	0.60
Random Forest	90%	0.76	0.78	0.77
XGBoost	81%	0.63	0.82	0.65
Performance on the Poor Class

Because the Poor class has fewer samples, its performance is particularly important.

Model	Poor Precision	Poor Recall	Poor F1
Logistic Regression	0.11	0.87	0.20
Random Forest	0.52	0.52	0.52
XGBoost	0.17	0.78	0.28
Results and Conclusion

Among the three models, Random Forest achieved the best overall performance.

It achieved:

90% accuracy
0.77 macro F1-score
0.52 F1-score for the Poor class

Random Forest performed better overall than Logistic Regression and XGBoost,
especially in balancing performance across the three mental health categories.

The results also show that the Poor category is more difficult to predict
because it contains substantially fewer samples than the Fair and Good
categories.

Project Structure
student-mental-health-ml/
│
├── README.md
├── requirements.txt
├── .gitignore
│
├── data/
│   └── Student Social Media And Mental Health Impact.csv
│
├── notebooks/
│   ├── 01_EDA_Preprocessing.ipynb
│   ├── 02_Logistic_Regression.ipynb
│   ├── 03_Random_Forest.ipynb
│   ├── 04_XGBoost.ipynb
│   └── 05_Model_Comparison.ipynb
│
└── results/
    ├── X_train.csv
    ├── X_test.csv
    ├── y_train.csv
    ├── y_test.csv
    └── model_comparison.csv
Technologies Used
Python
Pandas
NumPy
Matplotlib
Seaborn
SciPy
Scikit-learn
XGBoost
Jupyter Notebook
How to Run the Project
1. Clone the repository
git clone <your-github-repository-url>
2. Open the project folder
cd student-mental-health-ml
3. Install the required packages
pip install -r requirements.txt
4. Open the notebooks

Run the notebooks in the following order:

01_EDA_Preprocessing.ipynb
02_Logistic_Regression.ipynb
03_Random_Forest.ipynb
04_XGBoost.ipynb
05_Model_Comparison.ipynb
Authors

This project was developed as a collaborative machine learning project.



---


## Step 2 — Save it


Press:


**Ctrl + S**


Then click the `README.md` file in VS Code and check that it looks nicely formatted.


---


## Step 3 — One thing we should fix before GitHub


I want to make one small improvement before you push.


Your README says:


```text
Score 0–4 → Poor
4–7 → Fair
7–10 → Good

The original `Mental_Health_Score` was grouped into three categories using
score ranges defined in the preprocessing notebook:

- Poor
- Fair
- Good