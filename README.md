# Rossmann Store Sales Forecasting

A reproducible portfolio analysis of 28-day sales forecasts for the highest-sales 20% of Rossmann stores. Eight models are compared across six chronological forecast periods, with separate checks for daily accuracy, four-week totals and public holidays.

## Key results

- Checked 1,017,209 store-day records from 1,115 stores.
- Selected 223 stores using 1 January-3 July 2015 sales, accounting for 30.5% of sales in that ranking period.
- Compared weekday Baseline, Regression, Trend, fixed Ridge, tuned Ridge, tuned Tree, fixed Forest and tuned KNN.
- KNN ranks first by mean daily MAE across the three main comparison periods: 149,857 sales units, 6.41% below Forest's 160,118.
- July Regression MAE is 109,611 versus Baseline's 264,217, a 58.5% reduction. Its four-week forecast is 57.33 million against 56.54 million actual sales, a 1.40% overforecast.
- Forest has the lowest four-holiday MAE, 48,195, versus KNN's 115,932. Only four holidays contribute to this comparison.

## Interpretation and limitations

No model leads on every measure. KNN wins the main daily-MAE comparison, Forest performs better in both earlier checks and on the four assessed holidays, and Regression has lower July MAE. Trend has lower mean RMSE and mean absolute four-week total percentage error than KNN and Forest across the three main comparison periods.

KNN and Forest underforecast four-week totals in all six examined periods. Their mean absolute total errors across the three main comparison periods are 5.68% and 4.87%, compared with Trend's 2.10%. Daily accuracy and budget-total accuracy therefore require separate evaluation.

All six periods have been examined during development; none is an untouched final test. The training histories overlap, the seasonal coverage is limited, and opening and promotion schedules are assumed available in advance. Relationships and impurity importance do not establish causal effects. The results identify candidates for fresh chronological validation before operational use.

## Notebook contents

1. Data validation, cleaning and store selection
2. Per-store and pooled descriptive statistics
3. Time series, 28-day rolling mean, promotion comparisons and correlations
4. Calendar and store-count feature construction
5. Chronological evaluation and nested earlier-period tuning
6. Full eight-model comparison, daily errors and four-week total errors
7. Holiday diagnosis, tree paths and KNN neighbours
8. Training-error diagnostics, Forest settings and seed sensitivity
9. Limitations, future validation and complete per-store statistics

The notebook is saved with its tables and charts for review without rerunning it. Smaller model subsets remain as explicitly labelled supporting comparisons.

## Run locally

Use Python 3.13, matching the tested environment. The numerical dependencies are pinned because KNN equal-distance neighbour selection can be sensitive to implementation and floating-point differences.

1. Download `train.csv` from the [Rossmann Store Sales competition](https://www.kaggle.com/c/rossmann-store-sales/data).
2. Save it as `data/raw/Rossmann_train.csv`, or gzip it as `data/raw/Rossmann_train.csv.gz`.
3. Install the environment:

```bash
python -m pip install -r requirements.txt
```

4. Open `rossmann_sales_forecasting.ipynb` from the repository root and run all cells in order.

Only the training dataset is used. The data are not redistributed in this repository; obtain them from the original source under its applicable terms. No course-specific plotting helper is required.

## Provenance

This is a personal portfolio adaptation of a collaborative coursework analysis. The original analysis was jointly developed; this repository does not claim sole authorship of that work. Personal identifiers and submission administration have been omitted. Method and dataset sources are retained in the notebook references.
