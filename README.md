# Multiple Linear Regression

This repo contains a Jupyter notebook: `multiple-linear-regression.ipynb`, that trains and evaluates a Multiple Linear Regression model using scikit-learn.

## What the notebook does
- Loads the **50_Startups.csv** dataset
- Splits features (X) and target (y)
- One-hot encodes the categorical **State** column
- Splits the data into train and test sets
- Trains a `LinearRegression` model
- Predicts on the test set and prints **predicted vs actual** values

## Dataset
The notebook expects a CSV with columns similar to:
- R&D Spend
- Administration
- Marketing Spend
- State (categorical)
- Profit (target)

In the notebook, the dataset path is set to:
`/kaggle/input/multiple/50_Startups.csv`

If you are not running on Kaggle, update that path to wherever your CSV lives.

## Requirements
- Python 3.x
- numpy
- pandas
- matplotlib (imported, not strictly required for the current output)
- scikit-learn

Install deps:
```bash
pip install numpy pandas matplotlib scikit-learn
```

## How to run locally
1. Put `50_Startups.csv` next to the notebook (or anywhere you like).
2. Update the dataset path in the notebook:

```python
dataset = pd.read_csv("50_Startups.csv")  # or your local path
```

3. Run all cells.

## Output
At the end, the notebook prints a 2-column array:
- Column 1: model predictions (`y_pred`)
- Column 2: actual target values from the test set (`y_test`)

This makes it easy to eyeball how close the predictions are.

## Notes and common issues
- If you get a file not found error, it is almost always the CSV path. Change it to a valid local path.
- The code uses `OneHotEncoder` via `ColumnTransformer` on column index 3, which assumes:
  - The 4th column in X is the categorical column (State).
  - The last column in the CSV is the target (Profit).

If your CSV column order differs, adjust:
- `X = dataset.iloc[:, :-1].values`
- `y = dataset.iloc[:, -1].values`
- The encoder column index in `OneHotEncoder(), [3]`
