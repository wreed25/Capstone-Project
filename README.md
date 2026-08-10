
# Predicting NFL Player Value to Identify Contract Overpayment Risk

## Project Overview

NFL front offices must balance player performance with salary cap constraints when making roster and contract decisions. This capstone project uses machine learning to evaluate wide receiver performance and ultimately identify potential contract overpayment risk.

The project is being completed in phases. The current modeling phase focuses on predicting a wide receiver's next season receiving yards using historical player performance data. A later phase will integrate performance predictions with contract information to evaluate potential contract overpayment risk.

## Research Question

Can machine learning help NFL front offices identify player contract overpayment risk by predicting future player performance before signing or extending a contract?

## Current Modeling Objective

The current modeling objective is to predict next season receiving yards for NFL wide receivers.

The finalized modeling dataset contains:

- 2,127 player season observations
- 619 unique wide receivers
- 139 predictor variables
- next_season_receiving_yards as the prediction target

Because players can appear across multiple seasons, the data have a longitudinal structure. The modeling workflow uses a grouped train and test split based on player_id so that all observations for an individual player remain entirely within either the training or testing set. This prevents player level information leakage.

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
|-- figures/
|-- models/
|
|-- notebooks/
|   |-- 01_Data_Source_Validation.ipynb
|   |-- 02_Data_Collection_and_Integration.ipynb
|   |-- 03_Exploratory_Data_Analysis_EDA.ipynb
|   |-- 04_Feature_Engineering_and_Preprocessing.ipynb
|   `-- 05_Modeling.ipynb
|
|-- references/
|-- reports/
|-- src/
|-- requirements.txt
`-- README.md