# Real Estate Data Preparation and Linear Regression in Alteryx

## Project Overview

This project uses Alteryx Designer to prepare a real estate dataset and build a Linear Regression model to predict house prices. The work is divided into two connected workflows:

1. **Data Preparation and EDA**: cleans the original dataset, fixes missing values, removes outliers, creates new features, and exports a cleaned dataset.
2. **Linear Regression Modeling**: uses the cleaned dataset to analyze feature relationships, train a Linear Regression model, score test data, and calculate prediction error.

This repository includes the original dataset, cleaned dataset, and both Alteryx workflow files.

## Repository Structure

```text
real-estate-alteryx-regression/
│
├── data/
│   ├── real_estate.csv
│   └── final_real_estate.csv
│
├── workflows/
│   ├── EDA_RealEstate_Preparation.yxmd
│   └── Linear_Regression_Alteryx.yxmd
│
└── README.md
```

## Dataset

### Original Dataset

`data/real_estate.csv`

The original dataset includes real estate property information such as:

- price
- year_sold
- property_tax
- insurance
- beds
- baths
- sqft
- year_built
- lot_size
- basement
- property_type

### Cleaned Dataset

`data/final_real_estate.csv`

The cleaned dataset was generated from the Alteryx data preparation workflow. It contains 1,863 records and 15 columns. The text field `property_type` was converted into numeric flag columns, and new features were created for modeling.

Final columns include:

- price
- year_sold
- property_tax
- insurance
- beds
- baths
- sqft
- year_built
- lot_size
- basement
- Age
- Popular_Home
- Recession_Period
- Bunglow
- Condo

## Workflow 1: Data Preparation and EDA

File:

`workflows/EDA_RealEstate_Preparation.yxmd`

Main steps:

1. Import the original `real_estate.csv` dataset.
2. Use the Select tool to assign correct data types.
3. Use Field Summary for exploratory data analysis.
4. Create an Interactive Chart to compare square footage by property type.
5. Use Imputation to replace missing `basement` values with 0.
6. Use Filter to remove the outlier where `lot_size` is greater than or equal to 1,000,000.
7. Use Formula tools to create:
   - `Age = year_sold - year_built`
   - `Popular_Home`
   - `Recession_Period`
8. Remove records with negative age values.
9. Convert `property_type` into numeric flag columns:
   - `Bunglow`
   - `Condo`
10. Remove the original `property_type` text column.
11. Export the cleaned dataset as `final_real_estate.csv`.

## Workflow 2: Linear Regression Model

File:

`workflows/Linear_Regression_Alteryx.yxmd`

Main steps:

1. Import the cleaned dataset `final_real_estate.csv`.
2. Use the Select tool to verify numeric data types.
3. Use Association Analysis to review correlations with the target variable `price`.
4. Split the data using Create Samples:
   - 80% estimation/training sample
   - 20% validation/test sample
5. Train a Linear Regression model using `price` as the target variable.
6. Use the Score tool to generate predictions on the validation/test data.
7. Use the Formula tool to calculate prediction error:

```text
abs([Score_fit]-[price])
```

## Target Variable

The target variable for the Linear Regression model is:

```text
price
```

## Tools Used

- Alteryx Designer
- Input Data Tool
- Select Tool
- Field Summary Tool
- Interactive Chart Tool
- Imputation Tool
- Filter Tool
- Formula Tool
- Association Analysis Tool
- Create Samples Tool
- Linear Regression Tool
- Score Tool
- Browse Tool

## How to Run the Workflows

1. Open Alteryx Designer.
2. Open `workflows/EDA_RealEstate_Preparation.yxmd`.
3. Make sure the input path points to `data/real_estate.csv`.
4. Run the workflow to generate the cleaned dataset.
5. Open `workflows/Linear_Regression_Alteryx.yxmd`.
6. Make sure the input path points to `data/final_real_estate.csv`.
7. Run the workflow to train and test the Linear Regression model.

## Notes

The cleaned dataset is already included in this repository, so the Linear Regression workflow can be run directly using `data/final_real_estate.csv`.

## Author

Zainularab Zarabi  
Business Intelligence Systems Infrastructure Student  
Algonquin College
