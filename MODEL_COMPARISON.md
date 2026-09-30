# House Prices — Baseline Regression Comparison

## Objective

The objective of this task was to build a validated regression pipeline for predicting `SalePrice` using the cleaned Ames House Prices dataset.

The models were evaluated using:
- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- R² Score

The dataset was split into training and testing sets before preprocessing to avoid data leakage.

## Data Split

- Training samples: 1,168
- Testing samples: 292
- Test size: 20%
- Random state: 42

## Preprocessing

The preprocessing pipeline was implemented using `ColumnTransformer` and `Pipeline`.

### Numerical Features
- Median imputation
- StandardScaler

### Categorical Features
- Most-frequent imputation
- One-hot encoding
- `handle_unknown="ignore"`

All preprocessing steps were fitted only on the training data through the pipeline.

## Model Comparison

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| Mean Baseline | 62575.93 | 87619.03 | -0.001 |
| Linear Regression | 21103.80 | 65268.69 | 0.445 |
| Ridge (alpha=0.1) | 18514.97 | 29122.94 | 0.889 |
| Ridge (alpha=1) | 19138.06 | 29750.37 | 0.885 |
| Ridge (alpha=10) | 19159.15 | 30551.70 | 0.878 |
| Log-Target Ridge (alpha=0.1) | 15085.84 | 22823.79 | 0.932 |

## Log-Target Experiment

A log transformation was applied to the training target using `log1p(SalePrice)`.

The model predictions were converted back to the original price scale using `expm1()` before calculating the evaluation metrics.

The Log-Target Ridge model produced:

- MAE: 15085.84
- RMSE: 22823.79
- R²: 0.932

Compared with Ridge alpha=0.1 using the original target, the log-target experiment reduced both MAE and RMSE and increased the R² score on the test set.

## Conclusion

The regression experiments show that the linear and Ridge models improved the evaluation metrics compared with the mean-prediction baseline.

Ridge models were evaluated with alpha values of 0.1, 1, and 10. Among the standard Ridge models tested, alpha=0.1 produced the lowest MAE and RMSE and the highest R².

The additional log-target experiment further improved the reported test-set metrics. This indicates that the log transformation of `SalePrice` was useful for this dataset.

## Reproducibility

The complete preprocessing and modeling workflow is available in:

`regression_baseline.ipynb`

The notebook contains the data split, preprocessing pipeline, mean baseline, Linear Regression, Ridge models, and log-target experiment.
