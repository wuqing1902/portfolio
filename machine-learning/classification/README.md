# Breast Cancer Classification

## Overview

This project demonstrates a complete supervised machine learning workflow for breast cancer diagnosis using the Wisconsin Diagnostic Breast Cancer (WDBC) dataset.

Rather than focusing solely on building a classifier, the project follows an end-to-end machine learning pipeline, including exploratory data analysis, data preprocessing, model development, evaluation, explainability, model comparison, hyperparameter tuning, and model persistence.

The primary objective is to understand how machine learning models are developed, interpreted, and evaluated before deployment.

<br><br><br>

## Dataset

**Dataset:** Wisconsin Diagnostic Breast Cancer (WDBC)

The dataset contains numerical features extracted from digitized images of fine needle aspirates (FNA) of breast masses.

Target variable:

- **Benign (B)**
- **Malignant (M)**

After preprocessing, the diagnosis labels are encoded as:

| Original | Encoded |
|----------|---------|
| Benign | 0 |
| Malignant | 1 |

<br><br><br>

## Learning Objectives

This project aims to:

- Understand a complete machine learning workflow
- Perform exploratory data analysis (EDA)
- Build reusable preprocessing pipelines
- Train and evaluate classification models
- Interpret model decisions using explainable AI techniques
- Compare multiple machine learning algorithms
- Optimize model performance through hyperparameter tuning
- Save and reload trained models for future predictions

<br><br><br>

## Workflow

### 1. Data Exploration

Initial exploration includes:

- Dataset inspection
- Dataset statistics
- Data types
- Class distribution
- Feature distributions
- Duplicate detection
- Correlation analysis

Visualizations include:

- Histogram
- Class-wise Histogram
- Box Plot
- Correlation Heatmap
- Pair Plot

<br><br><br>

### 2. Data Preprocessing

The preprocessing pipeline includes:

- Removing unnecessary features
- Train-test split
- Target encoding
- Missing value imputation
- Feature scaling
- One-hot encoding (for categorical variables)
- ColumnTransformer
- Scikit-learn Pipeline

<br><br><br>

### 3. Baseline Model

The first model is built using:

- Logistic Regression

The complete preprocessing pipeline is integrated with the classifier to create a reusable end-to-end workflow.

<br><br><br>

### 4. Model Evaluation

Performance is evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC

Additional evaluation includes:

- Classification Report
- Confusion Matrix

Both training and testing datasets are evaluated to identify potential overfitting.

<br><br><br>

### 5. Model Interpretation

To better understand model behaviour, Logistic Regression coefficients are extracted and converted into Odds Ratios.

Feature importance is also investigated using:

- Random Forest Feature Importance

<br><br><br>

### 6. Explainable AI (XAI)

Model predictions are further interpreted using SHAP (SHapley Additive Explanations).

This includes:

- Global Feature Importance
- SHAP Summary Plot
- Feature Importance Ranking
- Individual Prediction Waterfall Plot

<br><br><br>

### 7. Model Comparison

Several classification algorithms are compared using Stratified K-Fold Cross Validation.

Models evaluated include:

- Logistic Regression
- Ridge Classifier
- Random Forest
- Histogram Gradient Boosting
- Support Vector Machine (Calibrated)

Evaluation metrics:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC

<br><br><br>

### 8. Hyperparameter Tuning

The Logistic Regression model is further optimized using GridSearchCV.

Hyperparameters explored include:

- Regularization strength (C)
- Elastic Net ratio (l1_ratio)
- Solver

The best model is selected based on Cross Validation F1-score.

<br><br><br>

### 9. Final Model Evaluation

The tuned Logistic Regression model is evaluated again on both training and testing datasets.

Additional visualizations include:

- Confusion Matrix
- ROC Curve

<br><br><br>

### 10. Prediction Pipeline

A reusable prediction function is implemented that accepts new patient measurements and returns:

- Predicted diagnosis
- Prediction label
- Probability of malignancy

This demonstrates how trained models can be integrated into real-world applications.

<br><br><br>

### 11. Model Persistence

The final trained model is exported using Joblib.

This allows the trained pipeline to be:

- saved
- reloaded
- reused for future predictions

without retraining.

<br><br><br>

## Machine Learning Concepts Covered

### Exploratory Data Analysis (EDA)

- Data inspection
- Distribution analysis
- Correlation analysis
- Duplicate detection
- Data visualization

### Data Preprocessing

- Train-test split
- Feature scaling
- Missing value imputation
- Target encoding
- ColumnTransformer
- Pipeline

### Classification

- Logistic Regression

### Ensemble Learning

- Random Forest

### Model Evaluation

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- Classification Report
- Confusion Matrix

### Model Selection

- Cross Validation
- Multiple Model Comparison

### Hyperparameter Optimization

- GridSearchCV

### Explainable AI (XAI)

- Logistic Regression Coefficients
- Odds Ratios
- Random Forest Feature Importance
- SHAP

### Deployment Preparation

- Prediction Pipeline
- Joblib Model Serialization

<br><br><br>

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-Learn
- SHAP
- Joblib

<br><br><br>

## Key Skills Demonstrated

- Exploratory Data Analysis (EDA)
- Correlation Analysis
- Data Preprocessing Pipelines
- Feature Scaling and Encoding
- Logistic Regression
- Random Forest
- Support Vector Machine (SVM)
- Ridge Classifier
- HistGradientBoosting Classifier
- Explainable AI (SHAP)
- Feature Importance Analysis
- Model Evaluation
- Cross Validation
- Hyperparameter Tuning
- Model Persistence
- End-to-End Machine Learning Workflow

<br><br><br>

<!--
## Future Improvements

Future extensions may include:

- XGBoost
- LightGBM
- CatBoost
- Threshold Optimization
- Probability Calibration
- Feature Selection
- Model Deployment with Flask or FastAPI
- Streamlit Web Application
-->

## Summary

This notebook demonstrates a complete classification machine learning pipeline, beginning with exploratory data analysis and ending with a deployable prediction model.

In addition to implementing Logistic Regression as a baseline model, multiple classification algorithms are compared using cross-validation, the best-performing model is optimized through hyperparameter tuning, and the final model is prepared for deployment through model serialization, explainable AI techniques, and reusable prediction functions.
