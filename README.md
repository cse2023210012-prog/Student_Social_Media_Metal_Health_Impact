# Student Mental Health Prediction Using Machine Learning

## Project Overview

This project analyzes the relationship between students' social media usage, lifestyle factors, stress levels, and mental health. Machine learning classification models predict a student's mental health status into one of three categories:

- Fair
- Good
- Poor

The repository covers the complete end-to-end pipeline: Exploratory Data Analysis (EDA), feature engineering, data preprocessing, model training across three algorithms, hyperparameter tuning, and cross-model evaluation.

---

## Dataset & Mental Health Classification

### Dataset Location
data/
└── Student Social Media And Mental Health Impact.csv

### Categorization Logic
The continuous Mental_Health_Score feature was mapped into three discrete classes:

- Score 0 to 4: Poor
- Score 4 to 7: Fair
- Score 7 to 10: Good

Note on Class Imbalance: The target variable distribution is heavily imbalanced; the Poor category contains significantly fewer samples than the Fair and Good categories.

---

## Project Workflow

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
Train / Test Split
  ↓
Machine Learning Models
  ├── Logistic Regression
  ├── Random Forest
  └── XGBoost
  ↓
Model Evaluation
  ↓
Model Comparison

---

## Exploratory Data Analysis

The primary analysis and preprocessing steps are located in notebooks/01_EDA_Preprocessing.ipynb and include:

- Dataset shape and column type inspection
- Missing-value and duplicate checking
- Analysis of numerical feature distributions
- Outlier detection using Z-scores
- Target distribution analysis and stress-level correlation

---

## Machine Learning Models

1. Logistic Regression (Baseline)
- Pipeline Setup: Standard scaling, class balancing, lbfgs solver.
- Tuning: GridSearchCV optimized to C = 1.

2. Random Forest
- Pipeline Setup: Gini impurity criterion, class balancing, 5-fold cross-validation.
- Tuning: GridSearchCV optimized macro F1-score with n_estimators = 100, max_depth = None, and min_samples_split = 2.

3. XGBoost
- Pipeline Setup: Multiclass classification objective with sample weighting and 5-fold cross-validation.
- Tuning: GridSearchCV optimized macro F1-score with n_estimators = 200, max_depth = 6, and learning_rate = 0.01.

---

## Model Evaluation & Comparison

### Overall Performance

- Logistic Regression:
  * Accuracy: 73%
  * Macro Precision: 0.60
  * Macro Recall: 0.82
  * Macro F1: 0.60

- Random Forest (Best Performing):
  * Accuracy: 90%
  * Macro Precision: 0.76
  * Macro Recall: 0.78
  * Macro F1: 0.77

- XGBoost:
  * Accuracy: 81%
  * Macro Precision: 0.63
  * Macro Recall: 0.82
  * Macro F1: 0.65

### Class-Specific Performance (Poor Class)

- Logistic Regression:
  * Precision: 0.11
  * Recall: 0.87
  * F1-Score: 0.20

- Random Forest:
  * Precision: 0.52
  * Recall: 0.52
  * F1-Score: 0.52

- XGBoost:
  * Precision: 0.17
  * Recall: 0.78
  * F1-Score: 0.28

### Key Takeaways
- Random Forest achieved the highest overall performance across all major metrics (90% accuracy, 0.77 Macro F1).
- The Poor category was challenging for all models due to data scarcity, but Random Forest balanced precision and recall far better than Logistic Regression or XGBoost, which suffered from high false-positive rates on minority samples.

---

## Repository Structure

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

---

## Technologies Used

- Languages: Python
- Data Processing & Analytics: Pandas, NumPy, SciPy
- Visualization: Matplotlib, Seaborn
- Machine Learning: Scikit-learn, XGBoost
- Environment: Jupyter Notebook


4. Run the notebooks in sequential order:
   1. 01_EDA_Preprocessing.ipynb
   2. 02_Logistic_Regression.ipynb
   3. 03_Random_Forest.ipynb
   4. 04_XGBoost.ipynb
   5. 05_Model_Comparison.ipynb
