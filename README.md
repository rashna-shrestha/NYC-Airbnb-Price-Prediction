# NYC Airbnb Price Prediction

This project uses the NYC Airbnb Open Data 2019 dataset to predict Airbnb listing prices with regression models. The analysis is implemented in [NYC_Airbnb_Price_Prediction.ipynb](NYC_Airbnb_Price_Prediction.ipynb).

## Project Structure

```text
.
├── AB_NYC_2019.csv
├── NYC_Airbnb_Price_Prediction.ipynb
├── requirements.txt
└── .gitignore
```

## Workflow

The notebook covers:

1. Loading and inspecting the dataset
2. Cleaning column names and handling missing values
3. Removing unused identifier/text columns and listings with a price of zero
4. Exploratory data analysis and outlier analysis
5. Feature selection with mutual information
6. Outlier capping, one-hot encoding, and standardization
7. Training and tuning regression models
8. Comparing model performance with MAE, RMSE, and R²

The target variable is `price`. The target is transformed with `log1p` before training to reduce the effect of its skewed distribution.

## Models

The notebook evaluates:

- Linear Regression
- Decision Tree Regressor
- Random Forest Regressor
- XGBoost Regressor

Based on the results recorded in the notebook, the final XGBoost model achieved the strongest R² and RMSE performance:

| Model | MAE | RMSE | R² |
| --- | ---: | ---: | ---: |
| XGBoost | 0.3184 | 0.4480 | 0.5821 |
| Random Forest | 0.3169 | 0.4488 | 0.5807 |
| Decision Tree | 0.3347 | 0.4675 | 0.5448 |
| Linear Regression | 0.3381 | 0.4737 | — |

Metrics are calculated on the log-transformed target variable. The complete comparison tables and charts are generated in the notebook.

## Requirements

- Python 3
- Jupyter Notebook or JupyterLab
- Packages listed in [requirements.txt](requirements.txt)

## Setup

Create and activate a virtual environment:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

Install the dependencies:

```bash
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

## Run the Notebook

Start Jupyter from the project directory:

```bash
jupyter notebook
```

Open `NYC_Airbnb_Price_Prediction.ipynb` and run the cells from top to bottom. Keep `AB_NYC_2019.csv` in the same directory as the notebook.

## Dataset

`AB_NYC_2019.csv` contains Airbnb listing information for New York City, including location, room type, availability, review activity, minimum nights, and price. The dataset is used locally by the notebook and is not recreated by the setup commands.

## Notes

- The notebook uses a fixed random seed of `42` for the train/test split and model reproducibility.
- Cross-validation is used during model tuning for the tree-based models.
- The notebook is an analysis workflow and does not currently expose a prediction API or web application.