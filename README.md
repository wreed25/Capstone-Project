
# Predicting NFL Player Value to Identify Contract Overpayment Risk

**Team Members:** William Reed (WR) and Jason Kuzmission (JK)  
**Course:** DSE6311 Capstone Project

## Background and Research Question

This project asks whether historical wide receiver performance, usage,
efficiency, and player information can predict next season receiving yards
well enough to support later contract risk analysis for an NFL General
Manager.

The working hypothesis is that opportunity, efficiency, production, and
experience contain useful predictive information, and that a multivariable
model will outperform a simple forecast based only on previous season
receiving yards.

The current modeling phase predicts next season receiving yards. Contract
data will be incorporated separately so predicted production can later be
compared with compensation without allowing contract information to influence
the performance prediction model.

## Current Modeling Objective

The current modeling objective is to predict next season receiving yards for
NFL wide receivers.

The finalized modeling dataset contains:

- 2,127 player-season observations
- 619 unique wide receivers
- 139 predictor variables
- next_season_receiving_yards as the prediction target

Because players can appear across multiple seasons, the data have a
longitudinal structure. The modeling workflow uses a grouped train and test
split based on player so that all observations for an individual player remain
entirely within either the training or testing set.

The finalized split contains:

- 1,683 training observations from 495 players
- 444 held-out test observations from 124 players
- 0 players appearing in both training and testing data

This player grouped design reduces the risk of player level information
leakage.

## Preprocessing and Feature Engineering

The completed preprocessing and feature engineering workflow includes:

- Creation of the next season receiving-yards target
- Removal of observations without a valid consecutive season target
- Removal of variables that could introduce leakage or unnecessary redundancy
- Grouped train and test splitting by player
- Median imputation using values learned from the training data
- Feature standardization using parameters learned from the training data
- Principal Component Analysis
- Lasso feature selection

Principal Component Analysis reduced the 139 predictor variables to 48
principal components while retaining approximately 95 percent of the
variance.

Lasso retained 69 predictors and removed 70 predictors, providing an
alternative feature-selection approach using the original football variables.

## Model Development and Evaluation

Notebook 06 establishes the baseline models and diagnostic framework.
Notebook 07 evaluates tunable nonlinear models and performs hyperparameter
tuning.

Models evaluated include:

- Historical persistence baseline
- Multiple Linear Regression
- Principal Component Regression
- Lasso Regression
- Random Forest Regression
- Gradient Boosting Regression

Model performance is evaluated using:

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- R-squared
- Training-versus-testing performance
- Five-fold player-grouped cross-validation
- Residual and model diagnostics

The current best-performing model is tuned Gradient Boosting, with held-out
test performance of:

- MAE: 212.33 receiving yards
- RMSE: 284.28 receiving yards
- R-squared: 0.549

The selected Gradient Boosting hyperparameters are:

- n_estimators = 300
- learning_rate = 0.05
- max_depth = 2
- min_samples_leaf = 10

The tuned Gradient Boosting model currently provides the strongest held-out
performance, although the tuned Random Forest performs similarly. Model
selection will continue to be evaluated as the project moves into the
contract-value phase.

## Custom Function

Notebook 07 includes the custom evaluate_model(y_true, y_pred) function.

The function accepts observed and predicted values and returns the regression
metrics used throughout model evaluation:

- MAE
- RMSE
- R-squared

The function provides a reusable and consistent approach for evaluating
regression-model performance during continued model development.

## Team Contributions

Both team members contribute to project development, review, documentation,
and validation.

- **William Reed (WR):** primary development of the current authoritative
  preprocessing, baseline-modeling, candidate-model, tuning, and evaluation
  workflow; report development and analytical validation.
- **Jason Kuzmission (JK):** exploratory analysis, preprocessing and baseline
  modeling work on the team branch; documentation contributions and model/code
  review.
- **Shared responsibilities:** data validation, code review, model evaluation,
  report review, and final project preparation.

Team roles may change by week as required by the course project.

## Project Status

### Completed

- Preliminary project proposal
- Final project proposal
- Data source validation
- Data collection and integration
- Exploratory Data Analysis
- Preprocessing and feature engineering
- Data dictionary and codebook
- Player-grouped validation strategy
- Baseline model development
- Candidate model evaluation
- Random Forest hyperparameter tuning
- Gradient Boosting hyperparameter tuning
- Current best-model selection
- Model diagnostics and overfitting assessment

### Current

- Code review and reproducibility validation
- Final model documentation

### Upcoming

- Contract data integration
- Contract overpayment risk analysis
- Final model interpretation
- Final report and presentation
- Final cross-machine reproducibility testing

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
|   |-- 05_Modeling.ipynb
|   |-- 06_Baseline_Models.ipynb
|   `-- 07_Model_Tuning_and_Evaluation.ipynb
|
|-- reports/
|
`-- README.md