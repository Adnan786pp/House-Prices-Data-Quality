
# DATA QUALITY REPORT

## 1. Dataset Overview

The dataset used for this assignment is the Kaggle House Prices - Advanced Regression Techniques dataset.

- Rows: 1460
- Columns: 81
- Target variable: SalePrice
- Problem type: Regression

## 2. Missing Value Analysis

A complete missing-value analysis was performed.

| Column | Missing Count | Missing Percentage |
|---|---:|---:|
| LotFrontage | 259 | 17.74% |
| Alley | 1369 | 93.77% |
| MasVnrType | 872 | 59.73% |
| MasVnrArea | 8 | 0.55% |
| BsmtQual | 37 | 2.53% |
| BsmtCond | 37 | 2.53% |
| BsmtExposure | 38 | 2.60% |
| BsmtFinType1 | 37 | 2.53% |
| BsmtFinType2 | 38 | 2.60% |
| Electrical | 1 | 0.07% |
| FireplaceQu | 690 | 47.26% |
| GarageType | 81 | 5.55% |
| GarageYrBlt | 81 | 5.55% |
| GarageFinish | 81 | 5.55% |
| GarageQual | 81 | 5.55% |
| GarageCond | 81 | 5.55% |
| PoolQC | 1453 | 99.52% |
| Fence | 1179 | 80.75% |
| MiscFeature | 1406 | 96.30% |

## 3. Missing Value Decisions

- LotFrontage: Median imputation was used because it is numerical and the median is less affected by extreme values.
- Alley: Filled with "None" because missing values generally indicate no alley access.
- MasVnrType: Filled with "None" because missing values generally indicate no masonry veneer.
- MasVnrArea: Filled with 0 because no masonry veneer means zero veneer area.
- Basement-related columns: Filled with "None" because missing values generally indicate that the property has no basement.
- FireplaceQu: Filled with "None" because missing values indicate no fireplace.
- GarageType, GarageFinish, GarageQual, GarageCond: Filled with "None" because missing values generally indicate no garage.
- GarageYrBlt: Filled with 0 because the missing value occurs when a garage is not present.
- PoolQC: Filled with "None" because missing values indicate no pool.
- Fence: Filled with "None" because missing values indicate no fence.
- MiscFeature: Filled with "None" because missing values indicate no miscellaneous feature.
- Electrical: Filled with the mode because only one value was missing.

A blanket mean imputation strategy was not used.

## 4. Duplicate Records

- Exact duplicate rows: 0
- Potential near-duplicate records: 0

Therefore, no records were removed because of duplication.

## 5. Outlier Detection

The IQR method was used to identify numerical outliers.

| Column | Number of Outliers |
|---|---:|
| LotArea | 69 |
| GrLivArea | 31 |
| TotalBsmtSF | 6 |

The identified outliers were not automatically removed because extreme property sizes can represent genuine large properties.

Particularly extreme observations such as GrLivArea = 5642 and TotalBsmtSF = 6110 should be investigated further rather than automatically classified as errors.

## 6. Data Type Correction

MSSubClass was converted from integer to categorical/object type because its values represent building class codes rather than continuous numerical measurements.

## 7. Final Cleaning Result

After applying the selected missing-value strategies:

- Remaining missing values: 0
- Exact duplicates: 0
- Potential near-duplicates: 0
- Outliers were identified and retained for further investigation.
- MSSubClass was correctly converted to categorical type.

The original raw dataset was preserved, while cleaning was performed on a separate copy named `clean_df`.
