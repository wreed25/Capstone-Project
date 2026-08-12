
# Predicting NFL Player Value to Identify Contract Overpayment Risk

**Team Members:** William Reed (WR) and Jason Kuzmission (JK)  
**Course:** DSE6311 Capstone Project

## Background and Research Question

This project asks whether historical wide receiver performance, usage, efficiency, and player information can predict next season receiving yards well enough to support later contract risk analysis for an NFL General Manager.

The working hypothesis is that opportunity, efficiency, production, and experience contain useful predictive information, and that a multivariable model will outperform a simple forecast based only on previous season receiving yards.

The current phase focuses on predicting next season receiving yards. Contract data will be added later so predicted production can be compared with compensation without allowing contract information to influence the performance target.

## Current Modeling Objective

The current modeling objective is to predict next season receiving yards for NFL wide receivers.

The finalized modeling dataset contains:

- 2,127 player season observations
- 619 unique wide receivers
- 139 predictor variables
- next_season_receiving_yards as the prediction target

Because players can appear across multiple seasons, the data have a longitudinal structure. The modeling workflow uses a grouped train and test split based on player so that all observations for an individual player remain entirely within either the training or testing set. This prevents player level information leakage.

## Preprocessing and Feature Engineering

The completed preprocessing and feature engineering workflow includes:

- Creation of the next season receiving yards target
- Removal of variables that could introduce leakage or unnecessary redundancy
- Grouped train and test splitting by player
- Median imputation using values learned from the training data
- Feature standardization using parameters learned from the training data
- Principal Component Analysis
- Lasso feature selection

Principal Component Analysis reduced the 139 predictor variables to 48 principal components while retaining approximately 95 percent of the variance.

Lasso retained 69 predictors and removed 70 predictors, providing an alternative feature selection approach using the original football variables.

## Project Status

### Completed

- Preliminary project proposal
- Final project proposal
- Data source validation
- Data collection and integration
- Exploratory Data Analysis
- Preprocessing and feature engineering
- Data dictionary and codebook
- Grouped validation strategy

### Current

- Model development and evaluation

### Upcoming

- Model refinement
- Hyperparameter tuning
- Final model evaluation
- Contract data integration
- Contract overpayment risk analysis
- Final report and presentation

## Repository Structure

```text
Capstone-Project/
|
|-- data/
|   |-- processed/
|   `-- raw/
|
|-- documentation/
|   |-- Appendix_A_Codebook.docx
|   `-- Master_Codebook.xlsx
|
|-- notebooks/
|   |-- 01_Data_Source_Validation.ipynb
|   |-- 02_Data_Collection_and_Integration.ipynb
|   |-- 03_Exploratory_Data_Analysis_(EDA).ipynb
|   |-- 04_Feature_Engineering_and_Preprocessing.ipynb
|   `-- 05_Modeling.ipynb
|
|-- reports/
|
`-- README.md
```
## Reproducing the Analysis

The project notebooks are designed to be run in numerical order because later notebooks use datasets created during earlier stages of the analysis.

1. Clone or download the repository.
2. Open the project from the repository root directory.
3. Run the notebooks in the following order:
   - `01_Data_Source_Validation.ipynb`
   - `02_Data_Collection_and_Integration.ipynb`
   - `03_Exploratory_Data_Analysis_(EDA).ipynb`
   - `04_Feature_Engineering_and_Preprocessing.ipynb`
   - `05_Modeling.ipynb`
4. Keep the repository folder structure unchanged so the relative data paths used in the notebooks remain valid.
5. Run each notebook from beginning to end before proceeding to the next notebook.

The notebooks contain markdown documentation, validation checks, and saved outputs to document the analytical workflow and verify key processing and modeling steps.
