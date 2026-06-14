# Customer Segmentation Analysis using K-Means Clustering

Welcome to the **Customer Segmentation Analysis** project, completed as part of the Data Analytics Internship at **Oasis Infobyte** (Level 1, Project 2). 

This project applies unsupervised machine learning algorithms (specifically K-Means Clustering) to partition a mall customer base into distinct, descriptive cohorts based on their demographic profiles and spending patterns.

---

## 🎯 Project Overview
Businesses must recognize that customers have different needs, buying frequency, and financial parameters. Customer segmentation allows organizations to target marketing campaigns, structure pricing tiers, select store merchandise, and manage customer relations effectively.

Using the **Mall Customers Dataset**, we:
1. Conducted exploratory analysis on customer age, income, and spending scores.
2. Determined the optimal number of segments ($K=5$) using the **Elbow Method**.
3. Grouped customers using the **K-Means Clustering** algorithm.
4. Profiled each cluster to construct detailed customer personas.
5. Formulated actionable business strategies for each persona.

---

## 📊 Dataset Information
The dataset contains **200 customer entries** with **5 features**:
- `CustomerID`: Unique sequential index.
- `Gender`: Male / Female.
- `Age`: Customer age in years (18 to 70).
- `Annual Income (k$)`: Approximate yearly earnings in thousands of dollars ($15k to $137k).
- `Spending Score (1-100)`: A rating assigned by the mall based on customer spending patterns (1 to 99).

*File location*: `Dataset/Mall_Customers.csv`

---

## 🛠️ Technologies Used
- **Programming Language**: Python 3.8+
- **Data Manipulation**: `Pandas`, `NumPy`
- **Machine Learning**: `Scikit-Learn` (KMeans)
- **Data Visualization**: `Matplotlib`, `Seaborn`
- **Environment**: `Jupyter Notebook`

---

## 📈 Workflow
1. **Data Loading & Cleaning**: Loaded the dataset using Pandas, checked for missing values (0 found), searched for duplicates (0 found), and verified column types.
2. **Exploratory Data Analysis (EDA)**: Visualized customer gender counts, age density curves, and the raw scatter plot of Annual Income vs. Spending Score.
3. **Elbow Method Curve**: Iterated K-Means from $K=1$ to $10$, calculated the Within-Cluster Sum of Squares (WCSS), and plotted the curve to isolate the "elbow point" at $K=5$.
4. **K-Means Modeling**: Fitted Scikit-Learn's `KMeans(n_clusters=5)` and mapped the labels back to the customers.
5. **Cluster Profiling**: Computed aggregate stats (average Age, average Income, and average Spending Score) per cluster.
6. **Insight Generation**: Drafted customized marketing recommendations for each cluster.

---

## 🔍 Results & Segment Profiles

The model successfully grouped the 200 customers into 5 distinct segments:

1. **VIP Target Segment (Cluster 1)**: Young adults (avg age 32.7) with high income (avg $86.5k) and high spending (avg score 82.1).
2. **Careful Spenders (Cluster 3)**: Middle-aged (avg age 41.1) with high income (avg $88.2k) but very low spending (avg score 17.1).
3. **Standard Customers (Cluster 0)**: Mid-aged (avg age 42.7) with average income (avg $55.3k) and average spending (avg score 49.5).
4. **Spendthrifts (Cluster 2)**: Very young (avg age 25.3) with low income (avg $25.7k) but high spending scores (avg score 79.4).
5. **Sensible Buyers (Cluster 4)**: Older shoppers (avg age 45.2) with low income (avg $26.3k) and low spending scores (avg score 20.9).

---

## 📂 Repository Navigation

```
Project_2_Customer_Segmentation/
├── Dataset/
│   └── Mall_Customers.csv                 # Raw dataset (CSV format)
├── Notebook/
│   └── Customer_Segmentation.ipynb         # Step-by-step Jupyter Notebook
├── Report/
│   └── Customer_Segmentation_Report.md    # In-depth business report
├── Visualizations/                        # PNG visual charts (300 DPI)
│   ├── customer_distribution.png          # Donut chart of customer genders
│   ├── age_distribution.png               # KDE Age distribution
│   ├── annual_income_vs_spending_score.png# Scatter plot before clustering
│   ├── elbow_method.png                   # Elbow plot for optimal K
│   └── customer_segments.png              # Scatter plot with cluster segments
└── README.md                              # This file
```

---

## 🚀 How to Run the Project
1. Install Python packages:
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn jupyter
   ```
2. Run the Jupyter Notebook:
   ```bash
   jupyter notebook Notebook/Customer_Segmentation.ipynb
   ```
3. To read the detailed business insights report, open [Customer_Segmentation_Report.md](file:///d:/Desktop/Oasis_Infobyte_Data_Analytics_Internship/Project_2_Customer_Segmentation/Report/Customer_Segmentation_Report.md).
