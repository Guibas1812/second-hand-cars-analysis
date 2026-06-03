# Second-Hand Car Price Analysis

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=flat&logo=jupyter&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat&logo=scikit-learn&logoColor=white)

An end-to-end data analysis project exploring the second-hand car market, with the goal of estimating car depreciation and evaluating whether **buying and reselling a second-hand car** is more cost-effective than **leasing**.

---

## Project Structure
📁 notebooks/
├── 01_data_collection_template.ipynb   # Web scraping methodology (anonymised)
├── 02_data_cleaning_eda.ipynb          # Data cleaning and exploratory analysis
└── 03_modelling.ipynb                  # Regression modelling and depreciation estimates
📄 cars_data.csv                        # Collected dataset
📄 df_models.csv                        # Model-level reference data

---

## Notebooks Overview

### 01 — Data Collection
Data was collected using **Selenium** to scrape a second-hand car listing website, simulating real user interaction. Filters applied:
- Maximum price: €15,000
- Minimum registration year: 2020
- Vehicle types: Saloon, Estate, SUV

A two-step scraping approach was used — a broad initial scrape followed by a focused scrape targeting the most frequent brand-model pairs to balance the dataset.

> The executable scraping code is not included in this repository to respect website usage policies. Notebook 01 serves as a methodological template.

### 02 — Data Cleaning & EDA
Raw listings were cleaned and transformed into an analysis-ready dataset:
- Extracted numeric values from text fields (price, mileage, power)
- Engineered `Car_Age_Years` from registration date
- Encoded categorical features (`Accident_Free_Binary`, `Fuel_Group_ICE`)
- Removed utility/commercial vehicles and low-mileage outliers
- Explored distributions, brand/model breakdowns, correlations, and outliers

### 03 — Modelling
Built regression models to predict car price and estimate depreciation:
- **Baseline linear regression** — R² ≈ 0.70 using KM, age, power, fuel type, and accident-free status
- **VIF analysis** — confirmed no multicollinearity issues
- **Depreciation estimate** — using model coefficients, estimated ~€4,900 value loss over 3 years (3 years of age + 45,000 km)

---

## Business Question

> Is it cheaper to buy a second-hand car and resell it after 3 years, or to lease?

The model estimates depreciation at approximately **€1,070/year from age** and **€0.038/km from mileage**, giving a combined estimated loss of ~€4,900 over a typical ownership period — providing a data-driven benchmark to compare against leasing costs.

---

## Tech Stack

| Tool | Purpose |
|---|---|
| Python | Analysis and modelling |
| Selenium | Web scraping (methodology only) |
| Pandas | Data cleaning and manipulation |
| Matplotlib / Seaborn | Visualisation |
| Statsmodels / Scikit-learn | Regression modelling |
| Jupyter Notebook | Development environment |
