
# 🏡 California Housing Price Prediction

## Overview
End-to-end regression analysis on the 1990 California Census 
Housing dataset comparing multiple regression models from 
baseline Linear Regression to Polynomial + Lasso.

## Results

| Model | R² Test | KFold R² | Std | Features |
|---|---|---|---|---|
| Linear Regression | 0.6499 | 0.6666 | 0.0082 | 12 |
| Ridge (α=100) | 0.6508 | 0.6660 | 0.0071 | 12 |
| Poly + Ridge | 0.6976 | 0.7082 | 0.0515 | 384 |
| **Poly + Lasso** | **0.7090** | **0.7165** | **0.0266** | **90** |


## Key Findings
- **Median income** is the strongest price predictor
- **Geography** encodes a clear coastal premium
- **Non-linearity** explains 35% of variance missed by linear models
- **Lasso** automatically eliminated 80% (364/454) of polynomial features
- **KFold validation** revealed Poly+Ridge is unstable (std=0.0515)
  vs Poly+Lasso which is reliable (std=0.0266)

## Methodology
```
1. Data exploration & visualization
2. Missing value imputation (median — 1% missing)
3. Log transformation of target (skew: 0.98 → -0.17)
4. One-hot encoding of ocean_proximity
5. Polynomial feature expansion (12 → 454 features)
6. GridSearchCV for hyperparameter tuning
7. KFold cross-validation for model evaluation
```

## Tech Stack
```
Python      — core language
pandas      — data manipulation
numpy       — numerical computing
matplotlib  — visualization
seaborn     — statistical plots
scikit-learn — modelling & evaluation
```

## Dataset
- Source: [California Housing Prices — Kaggle](https://www.kaggle.com/datasets/camnugent/california-housing-prices)
- 20,640 observations | 9 features | 1990 US Census
- Target: median house value (log-transformed)

## Limitations
- $500,001 census cap affects ~4.7% of districts
- 1990 data — not suitable for current predictions
- 29.1% of variance still unexplained

## Next Steps
- Tree-based models (XGBoost, Random Forest) → expected R² > 0.82
- Spatial features (distance to coast, city centre)
- External data (school ratings, crime rates)

## Connect
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue)](https://www.linkedin.com/in/jean-fred-a-williama-36905315/)
