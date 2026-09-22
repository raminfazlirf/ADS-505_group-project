# ADS-505 Group Project: Rossmann Store Sales Analysis

## Project Purpose
Rossmann operates over 3,000 drug stores across 7 European countries. Store managers currently forecast daily sales up to six weeks ahead, but accuracy varies widely since sales are driven by promotions, competition, holidays, seasonality, and locality.

This project analyzes the Rossmann Store Sales dataset (1,115 stores in Germany) to answer:
**How does promotion effectiveness vary by store type, season, holidays, and nearby competition, and where should Rossmann focus promotions to get the strongest sales impact?**

We apply statistical methods (hypothesis testing, regression modeling) to identify what drives sales variance and provide data-backed recommendations for promotional strategy.

## Team
- Ramin Fazli: Part 1, Data Cleaning and EDA
- Christopher Andra: Part 2, Feature Engineering and Statistical Analysis
- Danitza Loya: Part 3, Modeling, Tuning, and Final Model Selection

All three members contribute together to the Discussion and Conclusion, Model Brief, README/GitHub cleanup, Executive Brief, Presentation and Video, and AI Reflection Log.

## Repository Structure
```
ADS-505_group-project/
├── data/
│   ├── raw/            # Original Kaggle files (train.csv, store.csv, test.csv)
│   └── processed/      # Cleaned/merged datasets used for modeling
├── notebooks/          # Jupyter notebooks (.ipynb)
├── src/                # Reusable Python scripts (data cleaning, feature engineering)
├── requirements.txt    # Python dependencies
└── README.md
```

## Data Source
Cukierski, W., & Knauer, F. (2015). *Rossmann Store Sales* [Data set]. Kaggle. https://www.kaggle.com/competitions/rossmann-store-sales

Files used: `train.csv`, `store.csv`, `test.csv`

## Setup
1. Clone the repo:
   ```
   git clone git@github.com:raminfazlirf/ADS-505_group-project.git
   cd ADS-505_group-project
   ```
2. Create a virtual environment and install dependencies:
   ```
   pip install -r requirements.txt
   ```
3. Download the dataset from Kaggle (requires a free Kaggle account) and place `train.csv`, `store.csv`, and `test.csv` into `data/raw/`.

## How to Run
Open `notebooks/` in Jupyter or Google Colab and run cells top to bottom. Each notebook begins with a package import cell and is organized with markdown headings for EDA, preprocessing, modeling, and results.

## Contributions
| Member | Part | Contribution |
|---|---|---|
| Ramin Fazli | Part 1 | Problem statement, data description, data loading/merging, data quality checks, data cleaning, EDA on sales patterns (promotions, store type, holidays, day/month, competition), GitHub repo setup |
| Christopher Andra | Part 2 | Feature engineering, promotion effectiveness analysis by store type/season/holidays/competition, feature selection, train/validation/test split |
| Danitza Loya | Part 3 | Model selection rationale, initial modeling, model comparison, hyperparameter tuning, final model evaluation |

All members contribute to the Discussion and Conclusion, Model Brief, Executive Brief, Executive Presentation, and AI Reflection Log.

## Notebooks
- `01_data_cleaning_eda.ipynb`: Part 1, problem setup, data cleaning, and exploratory data analysis
