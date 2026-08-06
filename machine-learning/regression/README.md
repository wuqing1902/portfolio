# California Housing Regression

## Overview

This notebook documents a complete supervised machine learning workflow for a regression problem using the California Housing dataset.

Rather than focusing solely on Linear Regression, this project demonstrates the end-to-end process of developing, evaluating, comparing, tuning, and deploying regression models using Scikit-Learn pipelines.

The notebook emphasizes practical machine learning techniques, including data exploration, preprocessing, feature engineering, model comparison, hyperparameter tuning, explainable machine learning, and model persistence.

<br><br><br>

## Learning Objectives

After completing this notebook, I was able to:

- Understand a complete regression machine learning workflow.
- Perform exploratory data analysis (EDA).
- Build preprocessing pipelines for numerical and categorical features.
- Train and evaluate regression models.
- Compare multiple machine learning algorithms using cross validation.
- Tune model hyperparameters using GridSearchCV.
- Interpret model outputs using feature importance.
- Build reusable prediction functions.
- Save and reload trained models for deployment.

<br><br><br>

## Dataset

**Dataset:** California Housing Dataset

**Prediction Target**

- Median House Value

**Feature Types**

### Numerical Features

- Longitude
- Latitude
- Housing Median Age
- Total Rooms
- Total Bedrooms
- Population
- Households
- Median Income

### Categorical Feature

- Ocean Proximity

<br><br><br>

## Project Workflow

### 1. Data Exploration

The notebook begins with dataset inspection.

Topics covered include:

- dataset overview
- dataset shape
- data types
- descriptive statistics
- missing value inspection

<br><br><br>

### 2. Exploratory Data Analysis (EDA)

Several visualization techniques are used to better understand the dataset.

Visualizations include:

- feature distributions
- skewness analysis
- boxplots
- correlation matrix
- correlation heatmap
- scatter plots with regression lines
- geographic distribution
- pair plots
- duplicate detection

<br><br><br>

### 3. Data Preprocessing

A Scikit-Learn preprocessing pipeline is constructed.

Steps include:

- Train/Test Split
- Numerical feature selection
- Categorical feature selection
- Missing value imputation
- Feature scaling
- One-Hot Encoding
- ColumnTransformer
- Pipeline construction

<br><br><br>

### 4. Baseline Model

A baseline Linear Regression model is built using the preprocessing pipeline.

The model is evaluated using:

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- R² Score

<br><br><br>

### 5. Model Interpretation

The notebook examines the trained Linear Regression model by analysing:

- feature coefficients
- feature importance
- regression equation

This helps explain how each feature contributes to the predicted house price.

<br><br><br>

### 6. Model Comparison

Several regression algorithms are compared using 5-fold Cross Validation.

Models evaluated include:

- Linear Regression
- Ridge Regression
- Lasso Regression
- Random Forest Regressor
- HistGradientBoostingRegressor

Evaluation metrics include:

- RMSE
- MAE
- R² Score

The best-performing model is selected based on cross-validation performance.

<br><br><br>

### 7. Hyperparameter Tuning

The selected HistGradientBoostingRegressor is optimized using GridSearchCV.

Parameters explored include:

- learning rate
- maximum depth
- maximum leaf nodes
- minimum samples per leaf
- L2 regularization

<br><br><br>

### 8. Final Model Evaluation

The optimized model is evaluated on both the training and testing datasets.

Performance metrics include:

- RMSE
- MAE
- R² Score

Residual analysis is also performed through:

- Residual vs Prediction plot
- Residual distribution histogram

<br><br><br>

### 9. Prediction Function

A reusable prediction function is implemented that accepts new housing information and returns the predicted house price.

This demonstrates how a trained machine learning model can be used for inference on unseen data.

<br><br><br>

### 10. Model Persistence

The final trained model is saved using Joblib.

The notebook also demonstrates:

- saving models
- loading saved models
- making predictions after loading

This is an essential step for machine learning deployment.

<br><br><br>

## Machine Learning Concepts Covered

### Data Preparation

- Train/Test Split
- Missing Value Imputation
- Feature Scaling
- One-Hot Encoding
- Pipelines
- ColumnTransformer

### Exploratory Data Analysis

- Histograms
- Boxplots
- Correlation Analysis
- Scatter Plots
- Pair Plots
- Geographic Visualization

### Regression

- Linear Regression
- Ridge Regression
- Lasso Regression
- Random Forest Regression
- HistGradientBoosting Regression

### Model Evaluation

- MAE
- RMSE
- R² Score
- Residual Analysis

### Model Selection

- Cross Validation
- K-Fold Cross Validation
- Model Comparison

### Model Optimization

- GridSearchCV
- Hyperparameter Tuning

### Deployment Preparation

- Prediction Functions
- Model Serialization
- Joblib

<br><br><br>

## Libraries Used

- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-Learn
- Joblib

<br><br><br>

## Key Skills Demonstrated

- Exploratory Data Analysis (EDA)
- Correlation Analysis
- Data Preprocessing Pipelines
- Feature Scaling and Encoding
- Linear Regression
- Ridge Regression
- Lasso Regression
- Random Forest Regression
- HistGradientBoosting Regressor
- Feature Importance Analysis
- Model Evaluation
- Cross Validation
- Hyperparameter Tuning
- Residual Analysis
- Model Persistence
- End-to-End Machine Learning Workflow

<br><br><br>

## Summary

This notebook demonstrates a complete regression machine learning pipeline, beginning with exploratory data analysis and ending with a deployable prediction model.

In addition to implementing Linear Regression as a baseline model, multiple regression algorithms are compared using cross-validation, the best-performing model is optimized through hyperparameter tuning, and the final model is prepared for deployment through model serialization and reusable prediction functions.
  
