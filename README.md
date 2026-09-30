# Canada Per Capita Income Prediction (Linear Regression)

Predicting the per capita income of Canadian citizens for the year **2020**, and forecasting the trend up to 2026, using simple linear regression in Python.

## Problem Statement
Using `canada_per_capita_income.csv`, build a regression model and predict Canada's per capita income in the year 2020.

## Dataset
- **File:** `canada_per_capita_income.csv`
- **Period:** 1970 to 2016 (yearly)
- **Size:** 47 rows, 2 columns
- **Columns:** `year`, `per capita income (US$)`
- **Missing values:** none

| Statistic | Income (US$) |
|---|---|
| Mean | 18,920 |
| Minimum (1970) | 3,399 |
| Maximum (2013) | 42,676 |

## Approach
1. Load the data with `pandas` and inspect it (`head`, `tail`, `shape`, `isna`, `describe`)
2. Set `year` as the feature (X) and `per capita income (US$)` as the target (y)
3. Train a `LinearRegression` model from `scikit-learn`
4. Check the fitted slope, intercept and R²
5. Predict the income for 2020
6. Forecast the following years (2017-2026) with the same model and plot the result

## Results

| Metric | Value |
|---|---|
| Slope | 828.47 (income rises about $828 per year) |
| Intercept | -1,632,210.76 |
| R² | 0.891 |
| **Predicted income in 2020** | **$41,288.69** |

The model follows `income = 828.47 × year − 1,632,210.76`, so for 2020 the result is about **$41,289**.

## Forecast (2017-2026)

![Regression line and forecast](images/canada_forecast.png)

| Year | Predicted income (US$) |
|---|---|
| 2017 | 38,803.30 |
| 2018 | 39,631.76 |
| 2019 | 40,460.23 |
| **2020** | **41,288.69** |
| 2021 | 42,117.16 |
| 2022 | 42,945.62 |
| 2023 | 43,774.09 |
| 2024 | 44,602.55 |
| 2025 | 45,431.02 |
| 2026 | 46,259.48 |

Because the model is a straight line, the forecast rises by the same amount (about $828) every year.

## Project Structure
```
.
├── predicting_canada_per_capita.ipynb   # main notebook
├── canada_per_capita_income.csv         # dataset
├── images/
│   └── canada_forecast.png              # regression and forecast graph
└── README.md
```

## How to Run
```bash
git clone <your-repo-url>
cd <your-repo-name>
pip install pandas numpy matplotlib scikit-learn jupyter
jupyter notebook predicting_canada_per_capita.ipynb
```

## Limitations
- `year` is the only feature, so economic shocks (for example the 2014-2016 fall in income) are not captured by the straight-line model.
- The data ends in 2016, so the 2020 value and the forecast are extrapolations of the historical trend and do not reflect later events such as COVID-19.
- The model is evaluated on the same data it was trained on (R² = 0.891), so there is no separate test-set error.
- The forecast is a single line with no confidence interval, so the uncertainty around each prediction is not shown.

## Future Improvements
- Hold out the last few years as a test set and report RMSE / MAPE
- Add 95% prediction intervals to the forecast
- Compare with polynomial regression or time-series models (Holt-Winters, ARIMA)
- Add features such as oil price, inflation and exchange rate

## Tech Stack
Python, pandas, NumPy, scikit-learn, Matplotlib, Jupyter Notebook
