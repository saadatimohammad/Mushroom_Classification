# Predicting House Prices

## Project Overview

This project explores machine learning approaches to house price prediction using the Ames Housing dataset.

It addresses two predictive tasks:

- **Classification:** Predicting whether a house belongs to the expensive category.
- **Regression:** Predicting the sale price of a house.

The project was developed as part of the Data Science program at WBS Coding School.

## Dataset

The project uses two versions of the Ames Housing dataset, containing numerical and categorical information about residential properties in Ames, Iowa, USA.

| Dataset | Training Samples | Prediction Samples | Target |
|---|---:|---:|---|
| Classification | 1,460 | 1,459 | Expensive |
| Regression | 1,460 | 1,459 | SalePrice |

The datasets include property characteristics such as location, size, construction quality, building condition, garage capacity, and basement area.

Regression dataset source: [Kaggle - House Prices: Advanced Regression Techniques](https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques)

The regression dataset and its accompanying documentation are not redistributed in this repository. They must be downloaded directly from Kaggle in accordance with the competition rules.

## Methodology

Both notebooks follow a structured machine learning workflow:

- Exploratory data analysis
- Data cleaning and validation
- Domain-specific missing value handling
- Numerical and categorical feature preprocessing
- Feature scaling and one-hot encoding
- Baseline model development
- Machine learning pipelines
- Hyperparameter tuning using GridSearchCV
- 5-fold cross-validation
- Model evaluation and comparison
- Final model training and prediction

Preprocessing is integrated into model pipelines to minimize the risk of data leakage.

## Classification

**Objective:** Predict whether a residential property belongs to the expensive or non-expensive category.

### Models and Results

| Model | CV Accuracy | Test Accuracy | Test F1 Score |
|---|---:|---:|---:|
| Decision Tree | 94.4% | 91.1% | 0.698 |
| K-Nearest Neighbors | 94.3% | 93.5% | 0.740 |
| Random Forest | 95.4% | 94.9% | 0.800 |
| Logistic Regression | 94.6% | 94.9% | 0.805 |

**Baseline Accuracy:** 85.3%

**Final Model:** Logistic Regression

Logistic Regression achieved a test accuracy of 94.9% and the highest F1 score among the evaluated models.

The final model generates predictions for 1,459 properties.

## Regression

**Objective:** Predict residential property sale prices.

### Models and Results

| Model | CV RMSLE | Test RMSLE | MAE | R² |
|---|---:|---:|---:|---:|
| Baseline | 0.4124 | 0.4066 | $53,560 | -0.0475 |
| Decision Tree | 0.1863 | 0.1935 | $22,102 | 0.7263 |
| Linear Regression | 0.1740 | 0.1723 | $18,288 | 0.7731 |
| SGD Regression | 0.1573 | 0.1749 | $16,505 | 0.7896 |
| Random Forest | 0.1449 | 0.1560 | $16,638 | 0.7901 |

**Final Model:** Random Forest Regressor

### Key Results

- 61.6% reduction in RMSLE compared to the baseline.
- 68.9% reduction in mean absolute error compared to the baseline.
- R² score of 0.7901 on the held-out test set.

The final model generates sale price predictions for 1,459 properties.

## Project Structure

```text
Predicting House Prices/
├── data/
│   ├── classification/
│   │   ├── data_description.txt
│   │   ├── train.csv
│   │   └── test.csv
│   ├── regression/                   # Local Kaggle files
│   │   ├── data_description.txt
│   │   ├── train.csv
│   │   └── test.csv
│   └── output/                       # Generated locally
├── House Price Classification.ipynb
├── House Price Regression.ipynb
├── requirements.txt
├── .gitignore
└── README.md
```

The regression dataset directory and generated prediction files are excluded from version control. The structure above represents the local project after dataset setup and execution.

## Technologies

- Python 3.11
- NumPy
- Pandas
- Matplotlib
- Scikit-learn
- JupyterLab
- Git

## Installation and Usage

### 1. Install Dependencies

Install the required dependencies:

```bash
pip install -r requirements.txt
```

### 2. Prepare the Datasets

Ensure that the classification dataset is available in `data/classification/`.

For the regression task:

1. Visit the [Kaggle competition data page](https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques/data).
2. Accept the competition rules and download the required files.
3. Create the `data/regression/` directory.
4. Place the following files in that directory:
   - `train.csv`
   - `test.csv`
   - `data_description.txt`

### 3. Run the Notebooks

Launch JupyterLab from the project directory:

```bash
jupyter lab
```

Open either notebook and run all cells:

- `House Price Classification.ipynb`
- `House Price Regression.ipynb`

### 4. Generated Predictions

Prediction files are automatically generated in the `data/output/` directory:

- `submission.csv`
- `regression_submission.csv`

These files are excluded from version control.

## Limitations

- Cross-validation scores are based on the model development and hyperparameter tuning process rather than nested cross-validation.
- The regression notebook uses RMSLE, which differs slightly from the logarithmic RMSE metric used by the Kaggle competition.
- The models are intended for educational purposes rather than production property valuation.

## License

The original project code is licensed under the MIT License.

Third-party datasets and educational materials are excluded from this license and remain subject to their respective terms.

## Author

Mohammad Saadati