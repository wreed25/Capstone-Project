Predicting NFL Player Value to Identify Contract Overpayment Risk

Team Members: William Reed (WR) and Jason Kuzmission (JK)
Course: DSE6311 Capstone Project
Stakeholder: NFL General Manager

Project Overview

This project asks whether historical wide receiver performance, usage,
efficiency, and player information can predict next season receiving yards
well enough to support later contract risk analysis for an NFL General
Manager.

The working hypothesis is that opportunity, efficiency, production, and
experience contain useful predictive information, and that a multivariable
model will outperform a simple forecast based only on previous season
receiving yards.

The workflow first predicts next season receiving yards without using contract
information. Contract data are introduced only after the performance forecast
is complete. The final output is a decision support screen intended to help a
front office identify contracts that deserve additional review.

Key Results

The final modeling dataset contains 2,129 player season observations and
134 model predictors.

Tuned Random Forest was selected as the primary model. On the held out player
grouped test set, it produced:

MAE: 219.94 receiving yards

RMSE: 295.65 receiving yards

R squared: 0.517

The final contract analysis produced 919 matched player season contract
observations and identified 10 High Cost / Lower Production Review cases.

The model is intended to create a review queue, not make an automatic contract
decision.

Quick Start

The project is organized as an ordered Jupyter notebook workflow.

Clone or download this repository.

Create and activate a Python virtual environment.

Install the dependencies in requirements.txt.

Open the notebooks directory.

Run Notebooks 01 through 08 in numerical order.

Windows PowerShell

python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
pip install -r requirements.txt

Open the repository in VS Code or Jupyter and select the Python interpreter
from the project virtual environment.

Notebook Execution Order

Order

Notebook

Purpose

01

01_Data_Source_Validation.ipynb

Validates required source data

02

02_Data_Collection_and_Integration.ipynb

Collects and integrates player season data

03

03_Exploratory_Data_Analysis_(EDA).ipynb

Performs exploratory data analysis

04

04_Feature_Engineering_and_Preprocessing.ipynb

Creates the target, engineers features, and prepares modeling data

05

05_Modeling.ipynb

Develops the initial modeling workflow

06

06_Baseline_Models.ipynb

Establishes baseline models and comparisons

07

07_Model_Tuning_and_Evaluation.ipynb

Tunes models and performs final performance validation

08

08_Contract_Value_and_GM_Decision_Support.ipynb

Integrates contracts and creates the GM decision support output

Run each notebook completely before moving to the next notebook. The notebooks
use project relative paths and create the processed data and model artifacts
required by later stages.

Reproducing the Analysis

For a clean reproduction:

Start with a fresh kernel.

Run Notebooks 01 through 08 in order.

Confirm that each notebook completes without an execution error.

Verify the final audit in Notebook 08.

A successful final Notebook 08 audit should report:

Final rows: 919
Final columns: 18
Duplicate player-season-outcome keys: 0
Missing GM categories: 0

The final category counts should be:

Market-Aligned / Other: 719
High-Cost / High-Production: 177
Lower-Cost / High-Production Value: 13
High-Cost / Lower-Production Review: 10

Minor differences in printed formatting are acceptable, but the values should
match.

Custom Function

Notebook 07 contains the custom function:

evaluate_model(y_true, y_pred)

The function accepts observed and predicted values and returns the regression
metrics used for model evaluation:

MAE

RMSE

R squared

Example:

metrics = evaluate_model(y_test, predictions)
print(metrics)

This provides a consistent and reusable method for evaluating regression model
performance.

Team Contributions and Code Review

Both team members contributed to project development, review, documentation,
and validation.

William Reed (WR): primary development of the authoritative
preprocessing, baseline modeling, candidate model, tuning, evaluation, and
GM decision support workflow; report development and analytical validation.

Jason Kuzmission (JK): exploratory analysis, preprocessing and baseline
modeling work on the team branch; documentation contributions and model and
code review.

Shared responsibilities: data validation, code review, model evaluation,
report review, and final project preparation.

Team member initials are used in notebook documentation and code annotations
to identify responsibility where appropriate.

Testing and Reproducibility

The workflow includes validation checks for the modeling data, player grouped
splits, temporal evaluation, contract matching, duplicate keys, and final GM
categories.

The finalized workflow has been self tested by running the notebooks through
the complete analysis.

For the final cross machine test, a second user should clone the finalized
repository, follow only this README, run the notebooks in order, and verify the
Notebook 08 audit shown above.

Cross machine test record

Tester: Jason Kuzmission

Date: August 28, 2026

Environment: Independent computer

Result: Successfully loaded and ran Notebooks 01 through 08 without errors.

Documentation

Additional project documentation is available in the repository:

Master Data Dictionary

Appendix A Codebook

Final Report

Repository Structure

Capstone-Project/
|
|-- data/
|   |-- processed/
|   `-- raw/
|
|-- documentation/
|
|-- figures/
|
|-- models/
|
|-- notebooks/
|   |-- 01_Data_Source_Validation.ipynb
|   |-- 02_Data_Collection_and_Integration.ipynb
|   |-- 03_Exploratory_Data_Analysis_(EDA).ipynb
|   |-- 04_Feature_Engineering_and_Preprocessing.ipynb
|   |-- 05_Modeling.ipynb
|   |-- 06_Baseline_Models.ipynb
|   |-- 07_Model_Tuning_and_Evaluation.ipynb
|   `-- 08_Contract_Value_and_GM_Decision_Support.ipynb
|
|-- references/
|-- reports/
|-- src/
|-- requirements.txt
`-- README.md