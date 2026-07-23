
# Predicting NFL Player Value to Identify Contract Overpayment Risk


The National Football League (NFL) operates as a 32-team enterprise under a hard salary cap. For the 2026 season, each team is limited to a $301.2 million salary cap, while contract structures such as signing bonus proration, guaranteed money, and dead cap charges increase the complexity of roster construction. Every personnel decision requires balancing player performance, financial constraints, injury risk, and long-term roster strategy.

General Managers must determine which players provide the greatest value for their salary-cap investment, which veterans should receive contract extensions, which free agents represent good value, and when younger, less expensive players can replace higher-cost veterans.

This project investigates whether machine learning can improve personnel decisions by predicting a player's future value relative to contract cost before a contract is signed or extended.

## Research Question

Can machine learning help NFL front offices identify player contract overpayment risk by predicting a player's future value before signing or extending a contract?

## Hypothesis

Wide receivers with strong efficiency metrics, consistent target share, high snap participation, younger age, and minimal injury-related absences will generate greater future value per salary-cap dollar than receivers whose contracts are primarily justified by high volume statistics or one exceptional season.

## Prediction

If the hypothesis is supported, the model will identify characteristics associated with contract overpayment risk, including:

- Older receivers experiencing age-related performance decline
- Players with decreasing efficiency metrics
- Players with declining target share or snap participation
- Players whose recent production exceeds their long-term performance trend
- Contracts whose projected player value is lower than their financial commitment


## Data Sources

The project integrates three validated NFL datasets:

- **player_stats**: Seasonal player performance statistics
- **players**: Master player lookup table
- **contracts**: NFL contract and salary information

The data integration strategy was validated using the NFL GSIS player identifier:

```text
player_stats.player_id
        │
        ▼
players.gsis_id
        │
        ▼
contracts.gsis_id
```

This relationship was verified during the data validation phase and forms the foundation for constructing the modeling dataset.

## Project Status

The project is currently in the data engineering phase. Validated NFL datasets are being integrated into an analytical dataset for model development.

### Completed

- Repository structure established
- GitHub collaboration workflow configured
- Data source validation completed
- Dataset integration strategy validated

### In Progress

- Data collection
- Construction of the analytical dataset

### Upcoming

- Exploratory Data Analysis (EDA)
- Feature engineering
- Machine learning model development
- Model evaluation
- Final report

## Repository Structure

```text
Capstone-Project/
│
├── data/          # Raw and processed datasets
├── docs/          # Project documentation
├── figures/       # Visualizations
├── models/        # Saved models
├── notebooks/     # Jupyter notebooks
├── references/    # Supporting references
├── reports/       # Final reports and deliverables
├── src/           # Reusable source code
├── README.md
├── requirements.txt
└── .gitignore
```