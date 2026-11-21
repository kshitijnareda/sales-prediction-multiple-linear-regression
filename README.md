# Sales Prediction: Multiple Linear Regression

Predicting sales (in lakh INR) from advertising spend, pricing and store count using multiple linear regression in Python (scikit-learn).

## Overview
Sales are driven by several factors at once. This project models sales as a linear function of six inputs and shows how each one is associated with sales while the others are held constant.

## Dataset
- **File:** `data/sales_regression_dataset.csv` (60 observations, no missing values)
- **Source:** Practice dataset used for learning purposes

| Column | Description |
|---|---|
| `Sales_Lakh_INR` | Sales in lakh INR (**target**) |
| `TV_Ad_Spend_Lakh` | TV advertising spend (lakh INR) |
| `Digital_Ad_Spend_Lakh` | Digital advertising spend (lakh INR) |
| `Radio_Ad_Spend_Lakh` | Radio advertising spend (lakh INR) |
| `Price_INR` | Own product price (INR) |
| `Competitor_Price_INR` | Competitor product price (INR) |
| `Num_Stores` | Number of stores |
| `Observation` | Row ID (not used as a feature) |

## Approach
1. Load the data and check types and missing values
2. Select the six features and the target
3. Split 80/20 (`random_state=42`): 48 training rows, 12 test rows
4. Train a `LinearRegression` model
5. Predict on the test set and compare actual vs predicted sales
6. Evaluate with MSE, RMSE and R²
7. Plot actual vs predicted sales against a perfect-prediction line

## Results

| Metric | Value |
|---|---|
| MSE | 988.68 |
| RMSE | 31.44 (lakh INR) |
| R² | 0.777 |

Fitted coefficients (change in sales, in lakh INR, per one-unit increase with the other features held constant):

| Feature | Coefficient |
|---|---|
| TV ad spend | ≈ +3.10 |
| Digital ad spend | ≈ +3.56 |
| Radio ad spend | ≈ +0.45 |
| Own price | ≈ −2.52 |
| Competitor price | ≈ +1.81 |
| Number of stores | ≈ +3.47 |
| Intercept | ≈ 84.62 |

The signs are sensible: a higher own price lowers sales, a higher competitor price lifts them, and more ad spend and more stores raise them. Radio shows the weakest effect.

## Limitations
- Small dataset (60 rows) and a 12-row test set, so the metrics are noisy
- Coefficients show association, not causation
- No significance tests or multicollinearity check (e.g. VIF), so individual coefficients should be read cautiously
- Single train/test split, with no cross-validation

## Getting Started
```bash
git clone https://github.com/kshitijnareda/sales-prediction-multiple-linear-regression.git
cd sales-prediction-multiple-linear-regression
pip install pandas numpy matplotlib scikit-learn jupyter
jupyter notebook
```
Open `multiple_linear_regression_sales.ipynb` and run all cells.

## Repository Structure
```
├── data/
│   └── sales_regression_dataset.csv
├── multiple_linear_regression_sales.ipynb
└── README.md
```

## Tech Stack
Python · pandas · NumPy · scikit-learn · Matplotlib · Jupyter

## Author
**Kshitij Nareda**
GitHub: [@kshitijnareda](https://github.com/kshitijnareda)
