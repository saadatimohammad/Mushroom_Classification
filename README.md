# Mushroom Classification

## Project Overview

This project develops a machine learning model to classify mushrooms as poisonous or edible based on their physical characteristics.

The main objective is to minimize the number of poisonous mushrooms incorrectly classified as edible. For this reason, **recall for the poisonous class** is the primary evaluation metric.

The project was developed as part of the Data Science program at WBS Coding School.

## Dataset

The dataset contains categorical features describing mushroom characteristics.

- **Training dataset:** 6,499 observations
- **Test dataset:** 1,625 observations
- **Target variable:** `poisonous`
  - `1`: Poisonous
  - `0`: Edible

The predictive features are:

- `cap.shape`
- `cap.color`
- `bruises`
- `stalk.color.above.ring`
- `stalk.color.below.ring`
- `population`

The `Id` column is excluded from model training.

## Methodology

The machine learning workflow includes:

1. Loading and exploring the dataset.
2. Separating features and the target variable.
3. Creating a stratified training-validation split.
4. Establishing a baseline with a Dummy Classifier.
5. Training and comparing Logistic Regression and Random Forest models.
6. Encoding categorical features using One-Hot Encoding.
7. Evaluating models using recall, precision, confusion matrices, and ROC AUC.
8. Comparing decision thresholds using stratified cross-validation and out-of-fold predictions.
9. Training the selected model on the complete labeled dataset.
10. Generating predictions for the competition test dataset.

## Model Selection

**Random Forest** was selected because it achieved higher recall for poisonous mushrooms than Logistic Regression on the validation dataset.

The model uses 200 decision trees and a fixed random seed for reproducibility.

A decision threshold of **0.10** was selected based on out-of-fold predictions, prioritizing the identification of poisonous mushrooms while considering false-positive predictions.

## Results

### Validation Results

At the selected decision threshold of 0.10:

| Metric | Result |
|---|---:|
| Recall (poisonous class) | 100.00% |
| Precision (poisonous class) | 89.25% |
| False negatives | 0 |
| False positives | 76 |

These results describe the project's validation split and should not be interpreted as guaranteed performance on unseen data.

### Competition Results

The model was evaluated on a separate competition test dataset.

| Metric | Result |
|---|---:|
| Competition score | 0.9946 |
| Recall | 99.74% |
| Accuracy | 94.22% |
| Poisonous mushrooms classified as edible | 2 |
| Edible mushrooms classified as poisonous | 92 |

The competition results demonstrate strong recall but also show that the model is not error-free.

## Technologies

- Python 3.11.18
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- JupyterLab
- Git

## Project Structure

```text
Mushroom Classification/
├── Mushroom Classification.ipynb
├── README.md
├── requirements.txt
├── LICENSE.txt
├── .gitignore
└── data/
    ├── train.csv
    ├── test.csv
    ├── data_description.txt
    └── output/
        ├── example_submission.csv
        └── mushroom_submission.csv
```

The datasets and generated submission files are excluded from version control.

## How to Run

1. Clone the repository.
2. Install the dependencies:

   ```bash
   pip install -r requirements.txt
   ```

3. Place the required training and test datasets in the `data/` directory.
4. Open `Mushroom Classification.ipynb` in JupyterLab or Jupyter Notebook.
5. Run the notebook cells in order.

The final submission file is generated in `data/output/`.

## Limitations

- The model was trained on a limited set of mushroom characteristics.
- Validation results do not guarantee equivalent performance on new data.
- The competition evaluation identified two poisonous mushrooms incorrectly classified as edible.
- The model is intended exclusively for educational machine learning purposes.

**Safety warning:** This model must never be used to determine whether a real mushroom is safe to eat.

## Author

**Mohammad Saadati**

Developed as part of the Data Science program at WBS Coding School.