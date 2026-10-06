# ADS-505 Group Project: Rossmann Store Sales Analysis

## Project Purpose

Rossmann operates over 3,000 drug stores across 7 European countries. Store managers currently forecast daily sales up to six weeks ahead, but accuracy varies widely since sales are influenced by promotions, competition, holidays, seasonality, and locality.

This project analyzes the Rossmann Store Sales dataset (1,115 stores in Germany) to answer: **How does promotion effectiveness vary by store type, season, holidays, and nearby competition, and where should Rossmann focus promotions to get the strongest sales impact?**

We apply statistical methods, including hypothesis testing and regression modeling, to identify factors associated with sales variation and provide data-backed recommendations for promotional strategy.

## Team

- Ramin Fazli: Part 1, Data Cleaning and EDA
- Danitza Loya: Part 2, Feature Engineering and Statistical Analysis
- Christopher Andra: Part 3, Modeling, Tuning, and Final Model Selection

All three members contribute together to the Discussion and Conclusion, Model Brief, README/GitHub cleanup, Executive Brief, Presentation and Video, and AI Reflection Log.

## Repository Structure

```text
ADS-505_group-project/
├── data/
│   ├── raw/            # Original Kaggle files (train.csv, store.csv, test.csv)
│   └── processed/      # Cleaned/merged datasets and modeling splits
├── notebooks/          # Jupyter notebooks (.ipynb)
├── src/                # Reusable Python scripts (data cleaning, feature engineering)
├── requirements.txt    # Python dependencies
└── README.md
```

## Data Source

Cukierski, W., & Knauer, F. (2015). *Rossmann Store Sales* [Data set]. Kaggle.  
https://www.kaggle.com/competitions/rossmann-store-sales

Files used: `train.csv`, `store.csv`, `test.csv`

## Setup

1. Clone the repo:

   ```bash
   git clone git@github.com:raminfazlirf/ADS-505_group-project.git
   cd ADS-505_group-project
   ```

2. Create a virtual environment if desired and install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

3. Download the dataset from Kaggle (requires a free Kaggle account) and place `train.csv`, `store.csv`, and `test.csv` into `data/raw/`.

## How to Run

Open `notebooks/` in Jupyter Notebook and run the notebooks in order from top to bottom:

1. `01_data_cleaning_eda.ipynb`
2. `02_modeling_preparation.ipynb`
3. `03_modeling.ipynb`

Each notebook begins with a package import cell and is organized with markdown headings for the relevant stage of the project.

Part 1 prepares the cleaned dataset used by Part 2. Part 2 performs feature engineering, statistical analysis, leakage prevention, and creates the chronological train/validation/test splits used by Part 3. Part 3 performs regression modeling, hyperparameter tuning, final model selection, test evaluation, and feature importance analysis.

## Contributions

| **Member**        | **Part** | **Contribution** |
| ----------------- | -------- | ---------------- |
| Ramin Fazli       | Part 1   | Problem statement, data description, data loading/merging, data quality checks, data cleaning, EDA on sales patterns (promotions, store type, holidays, day/month, competition), GitHub repo setup |
| Danitza Loya      | Part 2   | Feature engineering, promotion effectiveness analysis by store type/season/holidays/competition, feature selection, leakage prevention, train/validation/test split |
| Christopher Andra | Part 3   | Model selection rationale, initial modeling, model comparison, hyperparameter tuning, final model evaluation, feature importance, and final model selection |

All members contribute to the Discussion and Conclusion, Model Brief, Executive Brief, Executive Presentation, README/GitHub cleanup, and AI Reflection Log.

## Notebooks

- `01_data_cleaning_eda.ipynb`: Part 1, problem setup, data cleaning, and exploratory data analysis
- `02_modeling_preparation.ipynb`: Part 2, feature engineering, statistical analysis, leakage prevention, and time-based splitting
- `03_modeling.ipynb`: Part 3, baseline and regression modeling, model comparison, hyperparameter tuning, final model evaluation, and feature importance

## Modeling Approach

Part 3 evaluates the following regression models:

- Baseline model
- Linear Regression
- Decision Tree Regressor
- Bagging Regressor
- Random Forest Regressor
- Gradient Boosting Regressor

The strongest ensemble models are further evaluated using focused hyperparameter tuning.

Because the training data contains more than 590,000 observations, tuning is performed on a reproducible sample of **250,000 training rows**. The selected hyperparameters are then used to retrain the final candidate models on the full training set.

## Runtime Note

On the development computer used for Part 3, the complete modeling and hyperparameter-tuning workflow requires approximately **3 hours** to run, with most of the time spent on ensemble-model training and tuning.

Runtime may vary substantially depending on CPU performance, RAM, and other system resources. The notebook currently uses `n_jobs=1` for the relevant ensemble models to reduce memory pressure. Users with stronger hardware may change supported `n_jobs` settings to `-1` to use all available CPU cores and potentially reduce runtime, although this can significantly increase memory usage.

Reducing the 250,000-row tuning sample can also shorten runtime, but it may change which hyperparameter combination is selected. If the sample size is changed, the tuning and model-selection steps should be rerun consistently.

## Final Model

The final selected model is a tuned **Random Forest Regressor** with:

- 150 trees
- Unrestricted tree depth
- `max_features = 0.8`
- `min_samples_leaf = 1`

### Validation Performance

- **MAE:** 845.59
- **RMSE:** 1,311.46
- **R²:** 0.8315

### Final Test Performance

- **MAE:** 780.02
- **RMSE:** 1,146.36
- **R²:** 0.8654

The test set was kept separate during model development and was evaluated after the final model was selected using validation performance.

## Key Modeling Findings

The tuned Random Forest achieved the strongest overall validation performance among the models evaluated.

Important model predictors included:

- Store
- Competition distance
- Promotion status
- Day of week
- Day
- Month
- Store type
- Assortment

Promotion was one of the strongest business-actionable predictors. These importance values describe predictive contribution within the Random Forest model and should not be interpreted as causal effects.

Store is represented by its numeric identifier in the current model. Although tree-based models can use this variable to distinguish store-level patterns, the numeric ordering of store IDs has no inherent business meaning.

## Limitations and Future Work

This project focuses on predictive relationships rather than causal inference, so the results do not establish that promotions directly caused changes in sales.

Additional limitations include computational constraints during hyperparameter tuning and the absence of external variables such as local economic conditions, weather, competitor promotions, and customer behavior.

Future work could evaluate:

- Additional external data sources
- Alternative store encoding approaches
- Model stability across different time periods and store segments
- More targeted analysis of promotion performance by store type, season, holiday period, and competition environment

## Reproducibility Notes

- Run notebooks in numerical order.
- Maintain the existing `data/raw/` and `data/processed/` folder structure.
- Install packages listed in `requirements.txt`.
- Random seeds are set where applicable for reproducibility.
- Part 3 uses `random_state=42` for sampling and supported models.
- Runtime will vary across computers.
- Changing the tuning sample size may change the selected hyperparameters and should be followed by a complete rerun of the tuning and model-selection workflow.
