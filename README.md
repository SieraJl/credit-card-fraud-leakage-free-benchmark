# Thresholds, not resampling

Code and results for the paper **"Thresholds, not resampling: a leakage-free
evaluation of imbalance handling, calibration and cost-sensitive decisions in
credit card fraud detection"** (Jlassi, Taktak, Besbes).

## Overview

This repository regenerates every table, figure and number reported in the
paper. It compares SMOTE-ENN, cost-sensitive weighting and no correction,
combined with logistic regression, XGBoost and CatBoost (with a balanced random
forest as reference), on the European card-holder fraud dataset under a
leakage-free protocol:

- exact duplicates removed before splitting
- scaling, resampling and hyperparameter tuning confined to training data
- thresholds and calibration maps fitted on a separate validation set
- a single test evaluation with bootstrap confidence intervals
- 5x5 repeated cross-validation with corrected resampled t-tests (Holm adjustment)

It also covers probability calibration (prior correction, Platt, isotonic),
class-dependent and amount-dependent cost analysis, chronological validation,
and SHAP explainability.

## Main finding

Once the decision threshold is selected on validation data, the imbalance
strategy has little effect on gradient-boosted trees. Thresholds, calibration
and costs matter more than resampling.

## Data

The dataset is public: https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud
Download `creditcard.csv` and place it in `data/`. It is not redistributed here.

## Requirements

Python 3.13, scikit-learn 1.9, XGBoost 3.4, CatBoost 1.2, imbalanced-learn 0.14,
Optuna 5.0, SHAP 0.53. Random seed: 42.


(Suggested: MIT for code.)
