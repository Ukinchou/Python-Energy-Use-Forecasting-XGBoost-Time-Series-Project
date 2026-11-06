# Python-Energy-Use-Forecasting-XGBoost-Time-Series-Project

Using a machine learning model XGBoost to predict energy consumption in Pennsylvania, New Jersey, Maryland area after 2015 



# Electricity Demand Forecasting with XGBoost

## Project Overview

This project uses machine learning to predict hourly electricity consumption in the PJM East region of the United States.

The objective is to explore historical electricity demand patterns, develop an XGBoost regression model using time-based features, and evaluate its predictive performance.

## Dataset

**Dataset:** PJM Hourly Energy Consumption (`PJME_hourly.csv`)

The dataset contains historical hourly electricity consumption measurements in megawatts (MW).

- **Target Variable:** `PJME_MW`
- **Time Column:** `Datetime`
- **Training Period:** Before January 1, 2015
- **Test Period:** January 1, 2015 onward

## Tools & Technologies

- **Python** — Data analysis and machine learning
- **Pandas** — Data manipulation and feature engineering
- **NumPy** — Numerical computations
- **Matplotlib & Seaborn** — Data visualization
- **XGBoost** — Gradient boosting regression
- **Scikit-learn** — Model evaluation
- **Jupyter Notebook** — Development environment

## Methodology

### 1. Exploratory Data Analysis (EDA)

Explored historical electricity consumption to identify temporal patterns and variations.

- Visualized historical hourly electricity consumption.
- Examined demand patterns across different hours of the day.
- Analyzed monthly variations in electricity consumption.
- Investigated seasonal fluctuations in electricity demand.

### 2. Feature Engineering

Extracted calendar-based features from the datetime index:

| Feature | Description |
|---|---|
| `hour` | Hour of the day (0–23) |
| `dayofweek` | Day of the week (0–6) |
| `quarter` | Quarter of the year (1–4) |
| `month` | Month (1–12) |
| `year` | Calendar year |
| `dayofyear` | Day of the year (1–366) |

### 3. Model Development

Trained an XGBoost regression model to predict hourly electricity consumption based on calendar features.

Initial model configuration:

- `n_estimators = 1000`
- `learning_rate = 0.01`
- `early_stopping_rounds = 50`

The dataset was split chronologically to preserve the time-series structure.

### 4. Feature Importance

Analyzed XGBoost feature importance scores to examine the relative contribution of calendar-based variables to model predictions.

## Model Performance

The initial XGBoost model produced the following evaluation results:

| Metric | Result |
|---|---:|
| Mean Absolute Error (MAE) | 2,895.09 MW |
| Root Mean Squared Error (RMSE) | 3,738.67 MW |
| Mean Absolute Percentage Error (MAPE) | 9.20% |

The model achieved a mean absolute percentage error of 9.20%, indicating that its predictions differed from actual electricity consumption by approximately 9.20% on average in relative terms.

**Evaluation note:** These are preliminary results. The test period was also used for early stopping, so a separate validation set is needed for an unbiased final evaluation.

## Key Findings

- Electricity consumption exhibits recurring daily and seasonal patterns.
- The XGBoost model captures broad seasonal demand fluctuations using calendar-based features.
- The model tends to underestimate certain peak electricity demand periods.
- Calendar-based features alone may not fully explain short-term changes in electricity consumption.

## Limitations & Future Improvements

Potential improvements include:

- Incorporating historical electricity consumption through lag features.
- Adding weather variables, particularly temperature.
- Including public holiday indicators.
- Implementing a separate validation set and time-series cross-validation.
- Comparing XGBoost against baseline forecasting methods.
- Optimizing model hyperparameters.

## How to Run

1. Clone this repository.
2. Install the required Python packages.
3. Obtain the `PJME_hourly.csv` dataset and place it in the project directory.
4. Open `energy_forecasting.ipynb` in Jupyter Notebook or VS Code.
5. Run the notebook cells sequentially.

## Project Status

Initial model development and evaluation completed. Further improvements and validation are planned.
