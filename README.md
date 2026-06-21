# Ransomware Detection Using Machine Learning

> Academic cybersecurity project that classifies network records as ransomware or non-ransomware using supervised Machine Learning models.

## Project Description

This project implements a ransomware detection workflow using the **UGRansome Dataset**. The notebook loads and prepares the data, trains five classification models, compares their performance, and selects the best model based on the F1-score.

The main goal is to evaluate which Machine Learning algorithm performs best when detecting ransomware-related records from the dataset.

This project is focused on defensive cybersecurity research and does not execute, distribute, or analyze live ransomware samples.

## Dataset

- **Dataset Name:** UGRansome Dataset
- **Source:** [Kaggle – UGRansome Dataset](https://www.kaggle.com/datasets/nkongolo/ugransome-dataset)
- **Repository Note:** The CSV dataset is not included in this repository. It must be downloaded directly from Kaggle and uploaded to Google Colab when running the notebook.

The dataset contains approximately **149,043 records** and 14 original columns.

Some of the main variables used are:

- `Protocol`
- `Flag`
- `Family`
- `Clusters`
- `BTC`
- `USD`
- `Netflow_Bytes`
- `Threats`
- `Port`

## Classification Target

The notebook creates a binary target variable called `is_ransomware` from the original `Prediction` column.

| Original Value | Generated Class | Meaning |
|---|---:|---|
| `A` | 0 | Non-ransomware |
| `S` or `SS` | 1 | Ransomware |

## Workflow

1. Upload the CSV dataset to Google Colab.
2. Correct column names.
3. Check missing values and duplicate records.
4. Create the binary target variable `is_ransomware`.
5. Separate categorical and numerical features.
6. Preprocess the data:
   - `OneHotEncoder` for categorical features.
   - `StandardScaler(with_mean=False)` for numerical features.
7. Split the dataset:
   - 80% training data.
   - 20% testing data.
   - Stratified split with `random_state = 42`.
8. Train and evaluate the Machine Learning models.
9. Compare metrics and identify the best model.
10. Predict ransomware and non-ransomware examples.

## Models Evaluated

The following Machine Learning models were trained and compared:

- Logistic Regression
- Decision Tree
- Random Forest
- AdaBoost
- XGBoost

## Results

The models were evaluated using a test set of approximately **29,809 records**.

| Model | Accuracy | Precision | Recall | F1-score | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| Logistic Regression | 0.8831 | 0.9547 | 0.8780 | 0.9148 | 0.9566 |
| Decision Tree | 0.9938 | 0.9990 | 0.9923 | 0.9957 | 0.9989 |
| Random Forest | 0.9930 | 0.9984 | 0.9918 | 0.9951 | 0.9997 |
| AdaBoost | 0.9356 | 0.9383 | 0.9738 | 0.9557 | 0.9762 |
| **XGBoost** | **0.9958** | **0.9969** | **0.9972** | **0.9971** | **0.9999** |

## Best Model

The best-performing model was **XGBoost**.

It achieved:

- **Accuracy:** 99.58%
- **Precision:** 99.69%
- **Recall:** 99.72%
- **F1-score:** 99.71%
- **ROC-AUC:** 99.99%

XGBoost was selected because it obtained the highest F1-score, which balances precision and recall.

## How to Run the Project in Google Colab

1. Download the dataset from Kaggle.
2. Download or clone this repository.
3. Upload the notebook `Trabajo_Ransomware.ipynb` to Google Colab.
4. Run the notebook cells in order.
5. When prompted, upload the CSV file downloaded from Kaggle.
6. Review the generated metrics, confusion matrices, and comparison charts.

## Requirements

```bash
pip install pandas numpy matplotlib scikit-learn xgboost
