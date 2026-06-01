# Real Estate Price Prediction Using Alteryx

## Overview

This project demonstrates an end to end analytics workflow in Alteryx for real estate data preparation, exploratory data analysis (EDA), feature engineering, and linear regression modeling. The objective was to transform raw housing data into an analysis ready dataset and develop a predictive model for estimating property prices.

## Dataset

* **real_estate.csv** – Raw dataset
* **final_real_estate.csv** – Cleaned dataset used for modeling

The dataset contains information such as property price, property tax, insurance, bedrooms, bathrooms, square footage, lot size, basement size, year built, year sold, and property type.

## Data Preparation

The data preparation workflow included:

* Data type standardization
* Missing value handling
* Outlier removal
* Feature engineering
* Categorical variable encoding

New features created:

* Age
* Popular_Home
* Recession_Period
* Bunglow
* Condo

## EDA Workflow

![EDA Workflow](eda_workflow.png)

## Correlation Analysis

Correlation analysis was performed to identify relationships between property characteristics and house prices.

![Correlation Analysis](correlation_analysis.png)

## Linear Regression Model

A Linear Regression model was developed using the cleaned dataset to predict house prices.

![Linear Regression Workflow](linear_regression_workflow.png)

## Results

Model performance was evaluated by comparing actual and predicted property prices. Prediction error was calculated using:

`abs([Score_fit] - [price])`

The workflow successfully generated house price predictions and measured prediction accuracy on the validation dataset.

![Prediction Results](prediction_results.png)

## Tools Used

* Alteryx Designer
* Microsoft Excel

## Author
* Zainularab Zarabi
* Machine Learning Project
