# Capstone Report — <your lane>

## Author: Rana Muhammad Hasnain

## Lane: Refresh / Content Opportunity Scoring

## Repo: https://github.com/Rana4682/flyrank-ml-internship

## Date: 27 July 2026

## 1. Problem framing

This project supports editorial decision-making by identifying content pages that should be refreshed.

Unit of analysis: One content page.

Output: A refresh priority score and ranked recommendation list.

Action: Editors can review the highest-ranked pages first and prioritize content updates.

Cost of a wrong decision: A page may be refreshed unnecessarily or an important page may be overlooked.

Machine learning helps identify patterns in historical search performance that are difficult to detect using manual inspection alone.

## 2. Data safety

Dataset used: FlyRank Internship Warehouse (content_refresh_anonymized.csv).

Features used:

ctr
avg_position
trend_pct

Excluded fields:

content_id
client_id

These identifiers were excluded because they are not predictive features.

Only anonymized data was used. No client names, URLs, credentials, or private queries appear anywhere in this project.

Potential leakage was considered by excluding identifier fields and using only observed search performance metrics.

## 3. Baseline

A transparent rule-based baseline was created using:

CTR
Average Position
Trend Percentage

Pages with lower CTR, poorer positions, and larger negative trends receive higher refresh scores.

This baseline provides an interpretable comparison for the machine learning model.

## 4. Model / analysis

Model used: Random Forest Regressor.

Features:

ctr
avg_position
trend_pct

Target:

Baseline Refresh Score.

The model was selected because it captures non-linear relationships while remaining easy to interpret through feature importance.

## 5. Evaluation

The dataset was divided using an 80/20 train-test split.

Evaluation metrics:

MAE: 0.1793
R² Score: 0.8713

The Random Forest model produced lower prediction error and accurately approximated the baseline scoring approach.

The results are intended for decision-support rather than causal claims.

## 6. Interpretation

Feature importance showed:

Trend Percentage
Average Position
CTR

Observed search trends contributed the most to refresh prioritization.

The model identified pages with declining performance as higher refresh candidates.

## 7. Recommendation

Recommended actions:

Refresh pages with declining trends.
Improve pages with low CTR.
Review pages with poor average positions.
Monitor stable pages before making changes.

Confidence: Medium

These recommendations are based on historical observations and should be combined with editorial judgment.

## 8. Reproducibility

Repository:

https://github.com/Rana4682/flyrank-ml-internship

## Environment:

Python
Pandas
Scikit-learn

## Random State:

42

The project can be reproduced by cloning the repository, installing the required libraries, and running the notebooks from top to bottom.

