# Oasis Infobyte Data Analytics Internship (OIBSIP)

Welcome to my **Data Analytics Internship Portfolio**! This repository contains a collection of projects completed during my Data Analytics Internship at **Oasis Infobyte**. 

These projects demonstrate hands-on experience in data cleaning, preprocessing, exploratory data analysis (EDA), time-series forecasting, customer demographic modeling, and high-impact business visualizations using Python's data science ecosystem.

---

## 📂 Project Catalog

| S.No. | Project Name | Level | Core Tech Stack | Description | Folder Link |
| :---: | :--- | :---: | :--- | :--- | :--- |
| **01** | **Retail Sales Exploratory Data Analysis** | **Level 1** | Python, Pandas, Matplotlib, Seaborn, Jupyter | Cleaning, statistics, monthly trend patterns, customer age/gender analysis, and correlation profiling of retail transactions. | [Project_1_Retail_Sales_EDA](./Project_1_Retail_Sales_EDA) |
| **02** | **Customer Segmentation Analysis** | **Level 1** | Python, Pandas, Scikit-Learn, Matplotlib, Seaborn, Jupyter | Unsupervised machine learning using K-Means Clustering and the Elbow Method to segment and profile shoppers based on earnings and spending behavior. | [Project_2_Customer_Segmentation](./Project_2_Customer_Segmentation) |
| **03** | **Data Cleaning and Preprocessing** | **Level 1** | Python, Pandas, NumPy, Scikit-Learn, Matplotlib, Seaborn, Jupyter | Preprocessing pipeline on NYC Airbnb dataset including missing value imputation, duplicate removal, outlier percentile-capping, scaling, and category encoding. | [Project_3_Data_Cleaning](./Project_3_Data_Cleaning) |

---

## 🛠️ Tech Stack & Skills Highlighted

- **Data Wrangling & Processing**: `Pandas`, `NumPy`
- **Data Visualization**: `Matplotlib`, `Seaborn`
- **Interactive Modeling**: `Jupyter Notebook`
- **Analytics Concepts**: Descriptive Statistics, Time Series Aggregations, Demographic Segmenting, Correlation Matrix Profiling.

---

## ⚙️ Environment Setup & Execution

To explore and run the projects locally, follow these steps:

### 1. Prerequisites
Ensure you have Python 3.8+ installed on your system. You can verify your python version using:
```bash
python --version
```

### 2. Clone the Repository
```bash
git clone https://github.com/Aditya11o/OIBSIP.git
cd OIBSIP
```

### 3. Set Up a Virtual Environment (Optional but Recommended)
On Windows:
```bash
python -m venv venv
.\venv\Scripts\activate
```
On macOS/Linux:
```bash
python3 -m venv venv
source venv/bin/activate
```

### 4. Install Dependencies
```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

### 5. Launch Project Notebooks
Navigate into a project directory to launch the Jupyter notebook or view report files.
For example, to run the **Retail Sales EDA** project:
```bash
cd Project_1_Retail_Sales_EDA
jupyter notebook Notebook/EDA_Retail_Sales.ipynb
```

---

## 📁 Repository Structure

```
OIBSIP/
│
├── Project_1_Retail_Sales_EDA/
│   ├── Dataset/
│   │   ├── Dataset 1.csv            # Retail sales dataset
│   │   └── Dataset 2.csv            # McDonald's nutrition reference data
│   ├── Notebook/
│   │   └── EDA_Retail_Sales.ipynb   # Interactive analysis notebook
│   ├── Report/
│   │   └── Retail_Sales_Report.md   # Final business insights report
│   ├── Visualizations/              # High-resolution PNG charts
│   │   ├── sales_trend.png
│   │   ├── category_sales.png
│   │   ├── top_products.png
│   │   └── heatmap.png
│   └── README.md                    # Project readme file
│
├── Project_2_Customer_Segmentation/
│   ├── Dataset/
│   │   ├── Mall_Customers.csv       # Mall customers dataset
│   │   └── marketing-analytics-...  # Unused reference notebook
│   ├── Notebook/
│   │   └── Customer_Segmentation.ipynb # Interactive clustering notebook
│   ├── Report/
│   │   └── Customer_Segmentation_Report.md # Business segmentation report
│   ├── Visualizations/              # High-resolution PNG charts
│   │   ├── customer_distribution.png
│   │   ├── age_distribution.png
│   │   ├── annual_income_vs_spending_score.png
│   │   ├── elbow_method.png
│   │   └── customer_segments.png
│   └── README.md                    # Project readme file
│
├── Project_3_Data_Cleaning/
│   ├── Dataset/
│   │   └── Dataset 1/
│   │       ├── AB_NYC_2019.csv      # NYC Airbnb 2019 dataset
│   │       └── New_York_City_.png   # Reference map
│   ├── Notebook/
│   │   └── Data_Cleaning_Preprocessing.ipynb # Interactive preprocessing notebook
│   ├── Report/
│   │   └── Data_Cleaning_Report.md  # Detailed cleaning business report
│   ├── Visualizations/              # High-resolution PNG charts
│   │   ├── missing_values_before.png
│   │   ├── missing_values_after.png
│   │   ├── outlier_detection.png
│   │   ├── feature_distribution.png
│   │   └── correlation_heatmap.png
│   └── README.md                    # Project readme file
│
└── README.md                        # Root readme (This index hub)
```

---

## 👤 Author
* **Aditya Halder**
* Role: Data Analytics Intern at Oasis Infobyte
* GitHub: [@Aditya11o](https://github.com/Aditya11o)
