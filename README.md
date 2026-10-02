# Rossmann Store Sales Forecasting

A sales forecasting project using the Rossmann Store Sales dataset. The analysis selects the highest-sales 20% of stores and compares seven forecasting procedures through chronological evaluation.

This portfolio version contains the complete analysis, model comparison, conclusions and reproducibility instructions.

## Key results

- Analysed 1,017,209 store-day records from 1,115 stores.
- Selected 223 high-sales stores, representing 30.5% of observed sales during the ranking period.
- Compared weekday baseline, linear regression, trend regression, fixed Ridge, tuned Ridge, decision tree and random forest.
- Reduced July daily MAE from 264,217 to 109,611 sales units using original regression, a 58.5% improvement.
- Forecast 57.33 million sales units against 56.54 million actual units over four weeks, a 1.40% overforecast.
- Random forest achieved mean MAE of 160,118 across three primary development windows, 0.95% below Trend and 2.52% below Regression.
- Forest holiday MAE was 48,195 across four development holiday dates, with no negative forecasts across six inspected windows.

## Conclusions

Random forest ranks first under the stated three-window development MAE rule. Its advantage is small: Trend has lower mean RMSE and absolute four-week total error, while original regression has lower July MAE (109,611 versus Forest's 138,087). All inspected periods have influenced development; no fresh independent final test is claimed. Retain Trend and Regression as references and validate fixed specifications on genuinely unseen seasons and holidays.

Promotions, opening coverage and weekday patterns were associated with daily sales, but these observational relationships should not be interpreted as causal effects. The model is most useful as a transparent benchmark for revenue planning. It still requires testing on later chronological periods, especially periods containing public holidays, before operational use.

## What the notebook covers

1. Data-quality checks and type standardisation
2. Selection of the highest-sales 20% of stores
3. Descriptive statistics and exploratory visualisations
4. Analysis of weekday, promotion, opening and holiday patterns
5. Chronological train-test split
6. Seven forecasting procedures and bounded Ridge/tree tuning
7. MAE, RMSE, R-squared and total-error comparison
8. Holiday diagnosis and non-negative sensitivity checks
9. Decision-tree interpretation, depth diagnostics and random forest comparison
10. Complete per-store statistics, model limitations and next steps

## Repository structure

```text
rossmann-sales-forecasting/
├── rossmann_sales_forecasting.ipynb
├── data/
│   └── README.md
├── requirements.txt
└── README.md
```

The notebook is saved with its outputs, so the analysis and charts can be reviewed directly on GitHub.

## Run locally

1. Download `train.csv` from the [Rossmann Store Sales competition](https://www.kaggle.com/c/rossmann-store-sales/data).
2. Save it as `data/raw/Rossmann_train.csv`, or gzip it as `data/raw/Rossmann_train.csv.gz`.
3. Install the dependencies:

```bash
python -m pip install -r requirements.txt
```

4. Open `rossmann_sales_forecasting.ipynb` and run all cells in order.

## Tools

Python, NumPy, Pandas, Matplotlib and scikit-learn. The correlation chart is self-contained and requires no course-specific helper.

## Scope and limitations

Six 28-day periods are inspected, including July and five earlier historical windows. The July window contains no public holidays. Regression can produce negative holiday forecasts; the forest improves the four-date development holiday check, but that sample cannot establish future reliability. Advance opening and promotion schedules are assumed. These aggregate forecasts cannot establish exact stock, staffing or profit gains.

## Data source

Kaggle, [Rossmann Store Sales](https://www.kaggle.com/c/rossmann-store-sales/data). The dataset is not redistributed in this public portfolio repository; users should obtain it from the original source under Kaggle's applicable terms.
