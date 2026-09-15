# Rossmann Store Sales Forecasting

An end-to-end sales forecasting project using the Rossmann Store Sales dataset. The analysis selects the highest-sales 20% of stores, explores the factors associated with daily sales, and evaluates a simple forecasting model on a chronological 28-day holdout period.

This portfolio version contains the complete analysis, model comparison, conclusions and reproducibility instructions.

## Key results

- Analysed 1,017,209 store-day records from 1,115 stores.
- Selected 223 high-sales stores, representing 30.5% of observed sales during the ranking period.
- Compared a weekday-mean baseline with multiple linear regression.
- Reduced held-out daily MAE from 264,217 to 109,611 sales units, a 58.5% improvement.
- Forecast 57.33 million sales units against 56.54 million actual units over four weeks, a 1.40% overforecast.

## Conclusions

Multiple linear regression provided the stronger short-term planning reference for the selected stores in the July 2015 evaluation window. It substantially reduced daily forecast error relative to the weekday baseline, while keeping the four-week total close to actual sales.

Promotions, opening coverage and weekday patterns were associated with daily sales, but these observational relationships should not be interpreted as causal effects. The model is most useful as a transparent benchmark for revenue planning. It still requires testing on later chronological periods, especially periods containing public holidays, before operational use.

## What the notebook covers

1. Data-quality checks and type standardisation
2. Selection of the highest-sales 20% of stores
3. Descriptive statistics and exploratory visualisations
4. Analysis of weekday, promotion, opening and holiday patterns
5. Chronological train-test split
6. Baseline and linear-regression forecasts
7. MAE, RMSE, R-squared and total-error comparison
8. Model limitations and proposed next steps

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

Python, Pandas, Matplotlib and scikit-learn.

## Scope and limitations

The evaluation covers one 28-day period and contains no public holidays. The linear model also produces several negative fitted values on public-holiday dates in the training period. Results are therefore suitable as a transparent forecasting exercise, rather than an operational forecasting system.

## Data source

Kaggle, [Rossmann Store Sales](https://www.kaggle.com/c/rossmann-store-sales/data). The dataset is not redistributed in this public portfolio repository; users should obtain it from the original source under Kaggle's applicable terms.
