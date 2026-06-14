# Data Cleaning and Preprocessing - NYC Airbnb 2019

Welcome to the **Data Cleaning and Preprocessing** project, completed as part of the Data Analytics Internship at **Oasis Infobyte** (Level 1, Project 3).

This project focuses on building a robust data cleaning and preprocessing pipeline using the **New York City Airbnb Open Data (2019)**. The raw dataset contains missing entries, extreme outliers, date formatting errors, and invalid prices, making it a perfect case study for demonstrating industry-standard preprocessing steps before building predictive machine learning models.

---

## 🎯 Project Overview
In data analytics, the phrase "garbage in, garbage out" highlights the importance of data quality. Before training a machine learning model, raw data must be cleaned, formatted, and scaled. 

This project implements:
1. **Missing Data Imputation**: Statistical placeholders for null text descriptions and reviews.
2. **Duplicate checks**: Verification of row uniqueness.
3. **Invalid Listing Filtering**: Removing listings with price = $0.
4. **Outlier Treatment**: Percentile-capping price and booking nights.
5. **Categorical Feature Encoding**: Applying One-Hot Encoding to categorical columns.
6. **Feature Scaling**: Standardizing continuous attributes using `StandardScaler`.

---

## 📊 Dataset Information
The dataset represents New York City Airbnb listings in 2019, consisting of **48,895 rows** and **16 columns**.
- `name` & `host_name` contain missing text entries.
- `last_review` & `reviews_per_month` contain 10,052 missing entries (when a listing has zero reviews).
- `price` contains extreme outliers (up to $10,000/night) and invalid values ($0).
- `minimum_nights` contains extreme outliers (up to 1,250 nights).

*File location*: `Dataset/Dataset 1/AB_NYC_2019.csv`

---

## 🛠️ Preprocessing Pipeline Steps

1. **Text Imputation**: Null descriptions in `name` and `host_name` are imputed with `"Unknown"`.
2. **Review Metrics Imputation**: Null records in `reviews_per_month` are filled with `0.0`. `last_review` is parsed to datetime and null records filled with a sentinel date `'1970-01-01'`.
3. **Filtering**: Listings with `price = $0` are dropped (11 rows).
4. **Outlier Capping**: Capped `price` at its 99th percentile (**$799.00**) and `minimum_nights` at its 99th percentile (**45.00 nights**).
5. **One-Hot Encoding**: Converted geographic `neighbourhood_group` and `room_type` categorical columns into dummy variables.
6. **Scaling**: Scaled clean numerical features using `StandardScaler` to have a mean of 0 and a standard deviation of 1.

---

## 📁 Repository Structure

```
Project_3_Data_Cleaning/
├── Dataset/
│   └── Dataset 1/
│       ├── AB_NYC_2019.csv              # Raw Airbnb dataset
│       └── New_York_City_.png           # Geographic guide map
├── Notebook/
│   └── Data_Cleaning_Preprocessing.ipynb# Interactive cleaning notebook
├── Report/
│   └── Data_Cleaning_Report.md          # Comprehensive analysis report
├── Visualizations/                      # High-resolution PNG charts (300 DPI)
│   ├── missing_values_before.png        # Null entries heatmap before cleaning
│   ├── missing_values_after.png         # Verifying 0 nulls post-cleaning
│   ├── outlier_detection.png            # Boxplots showing raw vs. capped limits
│   ├── feature_distribution.png         # Histograms of cleaned attributes
│   └── correlation_heatmap.png          # Correlation matrix of continuous features
└── README.md                            # This file
```

---

## ⚙️ How to Run the Project
1. Install Python packages:
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn jupyter
   ```
2. Run the Jupyter Notebook:
   ```bash
   jupyter notebook Notebook/Data_Cleaning_Preprocessing.ipynb
   ```
3. To read the detailed preprocessing metrics and business explanations, open [Data_Cleaning_Report.md](file:///d:/Desktop/Oasis_Infobyte_Data_Analytics_Internship/Project_3_Data_Cleaning/Report/Data_Cleaning_Report.md).
