# Public-Utility-Company-Regression-Model
# Target Corporation Quarterly Revenue Regression Analysis

This project performs an Ordinary Least Squares (OLS) time-series regression analysis on Target Corporation's quarterly revenue data (`qSales_2024 (3).csv`) to model historical trends, seasonal spikes, and post-pandemic shifts. The analysis was prepared by **Mayurri Ravirajan (Quantfolio Solutions)** for **Chapman Wealth Management**.

---

## Repository Structure & Contents

* **Data Source**: Uses quarterly financial data (`qSales_2024 (3).csv`), filtering specifically for Target Corporation (`tic == 'TGT'`).


* **Key Features Engineered**:
* `time`: A sequential integer tracker capturing baseline organic growth.


* `holiday`: A dummy variable indicating fiscal Q4 ($4^\text{th}$ quarter) to capture the holiday shopping season.


* `holiday_it`: An interaction term between `time` and `holiday` to track how seasonal holiday effects evolve over time.


* `covid`: A dummy variable for quarters occurring in 2021 or later.


* `covid_it`: An interaction term tracking post-2021 changes.





---

## Methodology & Model Setup

1. **Train/Test Split**: The dataset is chronologically split, using the first **75% for training** (`dt4training`) and the remaining **25% for testing** (`dt4testing`).


2. **Regression Equation**:

$$\text{Revenue} = 9470.64 + 134.90(\text{time}) + 4006.81(\text{holiday}) + 15.53(\text{holiday\_it})$$


3. **Performance Evaluation**: Evaluated using Mean Absolute Percentage Error (MAPE) on the unseen testing set, achieving a MAPE of approximately **12%**.



---

## Key Findings & Limitations

* **Steady Organic Growth**: Target exhibits a stable baseline growth rate, increasing by roughly **$134.90** per time period.


* **Holiday Seasonality**: Q4 shows a reliable, predictable revenue surge, averaging an increase of **$4,006.81** above baseline.


* **COVID-19 Dummy Limitation**: Because the training data (first 75%) ends before 2021, the `covid` and `covid_it` coefficients estimated to `0.00` during model fitting. Consequently, the model under-predicts actual revenues in the post-2021 testing period. Adjusting the train/test split or expanding the dataset to include recent years will resolve this limitation.
