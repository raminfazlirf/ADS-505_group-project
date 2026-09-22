# ADS-505 Group Project: Rossmann Store Sales Analysis

## Project Purpose
Rossmann operates over 3,000 drug stores across 7 European countries. Store managers currently forecast daily sales up to six weeks ahead, but accuracy varies widely since sales are driven by promotions, competition, holidays, seasonality, and locality.

This project analyzes the Rossmann Store Sales dataset (1,115 stores in Germany) to answer:
**How does promotion effectiveness vary by store type, season, holidays, and nearby competition, and where should Rossmann focus promotions to get the strongest sales impact?**

We apply statistical methods (hypothesis testing, regression modeling) to identify what drives sales variance and provide data-backed recommendations for promotional strategy.

## Team
- Ramin Fazli — Data Foundation & EDA
- Christopher Andra — Modeling & Analysis
- Danitza Loya — Executive Communication

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
| Member | Contribution |
|---|---|
| Ramin Fazli | Data cleaning, EDA, GitHub repo setup |
| Christopher Andra | Statistical modeling, hypothesis testing, model brief |
| Danitza Loya | Executive brief, presentation, task coordination |

All members contributed to the AI Reflection Log.
