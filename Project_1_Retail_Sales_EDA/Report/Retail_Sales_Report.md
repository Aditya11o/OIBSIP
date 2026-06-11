# Retail Sales Exploratory Data Analysis (EDA) Report
**Oasis Infobyte Data Analytics Internship - Project 1**  
**Author:** Aditya Halder (Data Analytics Intern)  
**Date:** June 2026  

---

## 1. Introduction
Exploratory Data Analysis (EDA) is a critical first step in the data science lifecycle. It involves inspecting, cleaning, transforming, and visualizing raw data to discover hidden patterns, identify anomalies, test hypotheses, and verify assumptions using statistical summaries and graphical representations.

This project focuses on analyzing a transaction history dataset from a retail store. The primary objectives are to:
- Clean and preprocess raw transactional records.
- Understand transaction frequency, pricing limits, and quantity patterns.
- Analyze seasonal sales trends over time to identify high and low business cycles.
- Investigate consumer purchasing habits based on gender and age cohorts.
- Evaluate individual product category performances to optimize stock levels and store merchandising.
- Implement advanced customer segmentation to classify shoppers based on historical values.
- Extract data-driven business recommendations to support revenue growth and customer retention.

---

## 2. Dataset Overview

### Dataset Selection Note
The internship project proposal provided links to two distinct datasets:
1. **Dataset 1**: Retail Sales Data (1,000 rows of transaction logs).
2. **Dataset 2**: McDonald's Menu Nutrition Data (260 rows of food nutrition details).

To align with the project theme of **"Exploratory Data Analysis on Retail Sales Data"**, this project focuses exclusively on **Dataset 1**. Dataset 2 is preserved in the project directory under `Dataset/Dataset 2.csv` for structural completeness but is excluded from the analysis.

### Dataset 1 Structure
Dataset 1 comprises **1,000 records** and **9 attributes** tracking customer demographics, transaction dates, categories, and financial metrics.

### Attribute Descriptions:
| Column Name | Data Type | Description |
| :--- | :--- | :--- |
| **Transaction ID** | Integer | Unique identifier for each sales transaction |
| **Date** | Object (Date) | The calendar date of the purchase (formatted as YYYY-MM-DD) |
| **Customer ID** | Object (String) | Unique identifier representing an individual customer |
| **Gender** | Object (Categorical)| Customer's gender identity (Male / Female) |
| **Age** | Integer | Customer's age in years (ranging from 18 to 64) |
| **Product Category**| Object (Categorical)| Broad category of product purchased (Beauty / Clothing / Electronics) |
| **Quantity** | Integer | Total items purchased in the transaction (ranging from 1 to 4) |
| **Price per Unit** | Integer | The price of a single unit of the product ($25, $30, $50, $300, $500) |
| **Total Amount** | Integer | The transaction's total value ($) — calculated as `Quantity` * `Price per Unit` |

---

## 3. Data Cleaning and Preprocessing
To guarantee analytical accuracy, the dataset underwent several verification steps:
1. **Missing Value Check**: Checked for null values across all columns. No missing or null values were identified.
2. **Duplicate Row Check**: Scanned the data for duplicate transaction rows. No duplicate records exist.
3. **Data Type Correction**: The `Date` column was converted from a string (`object`) type to a pandas `datetime64[ns]` format. This allows for resampling, extraction of year, month, and day names, and chronological ordering.
4. **Calculational Consistency Check**: Verified that `Total Amount` equals `Quantity` * `Price per Unit` for all 1,000 observations. The verification confirmed 100% mathematical alignment across the dataset.

---

## 4. EDA Findings

### A. Descriptive Statistics
Key numerical observations from the descriptive statistics:
- **Customer Age**: Ranges from **18 to 64 years**, with a mean age of **41.39 years**, showing a mature customer base. The age distribution is relatively flat, indicating even market appeal across adults.
- **Product Quantity**: Customers purchase between **1 and 4 items** per transaction, averaging **2.51 items**.
- **Unit Prices**: Highly discrete pricing tiers ($25, $30, $50, $300, $500), averaging **$179.89** per item.
- **Total Spent**: Transaction amounts range from **$25 to $2,000**, with a mean transaction value of **$456.00** and a median of **$135.00**. The large difference between median and mean highlights a right-skewed distribution driven by high-value transactions (such as 4 items at $500 each).

### B. Time Series and Trend Analysis
- In 2023, the retail store generated **$456,000** in total revenue.
- The monthly sales analysis reveals significant seasonal volatility:
  - **Highest Revenue Months**: **May 2023 ($53,150)** and **October 2023 ($46,580)**.
  - **Lowest Revenue Month**: **September 2023 ($23,620)**. This drop represents a **55.5% decrease** compared to the May peak.
  - **Other Key Months**: Spring (March-May) shows a upward growth pattern, while late summer (August-September) shows a sharp decline.

### C. Category Performance
The store trades in three product categories:
- **Electronics**: Generated the highest total revenue (**$156,905**) across 342 transactions (849 units sold). This performance is led by higher average item values.
- **Clothing**: Driven by transaction frequency, bringing in **351 transactions** (894 units sold) and generating **$155,580** in revenue.
- **Beauty**: Contribution is slightly lower with **$143,515** in revenue, spanning 307 transactions (771 units sold).

### D. Demographic Breakdown
- **Gender Analysis**: 
  - **Female** customers contributed **$232,840** (51.1%) of total revenue across 510 transactions.
  - **Male** customers contributed **$223,160** (48.9%) across 490 transactions.
  - The average transaction value between genders is nearly identical: **$456.55** for females and **$455.43** for males.
- **Gender vs. Product Preference**:
  - Females are the dominant buyers of **Beauty** products, spending **$83,860** (compared to $59,655 by males).
  - Males spend more on **Electronics**, generating **$84,650** (compared to $72,255 by females).
  - Spending on **Clothing** is balanced between genders ($76,725 for females vs. $78,855 for males).
- **Age Analysis**:
  - The **46-55** age group is our largest contributor in terms of sheer revenue (**$97,235**) and transaction count (**225**).
  - The **18-25** age bracket is the smallest cohort (149 transactions) but has the highest average transaction value (**$501.01**).

### E. Advanced Customer Value Segmentation (RM Analysis)
A check on the dataset reveals that there are exactly 1,000 unique customer IDs for the 1,000 transactions (i.e. every customer bought exactly once, so purchase frequency is 1). Therefore, standard 3D RFM collapses into a 2D **Recency-Monetary (RM) Value Grid**:
* **Recency Score (R)**: Days since purchase relative to reference date `2024-01-02`.
  * `Score 3 (Recent)`: $\le 120$ days.
  * `Score 2 (Average)`: $120 < \text{days} \le 240$.
  * `Score 1 (Dormant)`: $> 240$ days.
* **Monetary Score (M)**: Transaction order value.
  * `Score 3 (High spend)`: $\ge \$500$
  * `Score 2 (Medium spend)`: $\$100 \le \text{spend} < \$500$
  * `Score 1 (Low spend)`: $< \$100$

By mapping these scores, customers are classified into 5 distinct behavioral segments:
1. **Champions** ($R=3, M=3$): Recent buyers who purchased high-value products.
2. **Active Prospects** ($R=3, M < 3$): Recent buyers who spent low-to-medium amounts.
3. **At Risk** ($R < 3, M=3$): High-value spenders who have not purchased in over 4 months.
4. **Regular Customers** ($R=2, M < 3$): Customers who purchased medium-value items mid-term.
5. **Lost Customers** ($R=1, M < 3$): Customers who made small purchases long ago and are dormant.

#### RM Value Segmentation Summary:
| Segment Name | Customer Count | Total Sales ($) | Revenue Share (%) | Average Ticket ($) | Status |
| :--- | :---: | :---: | :---: | :---: | :--- |
| **At Risk** | 242 | $264,100 | **57.9%** | $1,091.32 | Dormant High-Value |
| **Champions** | 108 | $125,000 | 27.4% | $1,157.41 | Active High-Value |
| **Lost Customers** | 233 | $23,410 | 5.1% | $100.47 | Dormant Low-Value |
| **Active Prospects** | 216 | $23,295 | 5.1% | $107.85 | Active Low-Value |
| **Regular Customers**| 201 | $20,195 | 4.4% | $100.47 | Mid-term Low-Value |

---

## 5. Visualizations
The visual charts generated during this project are saved under the `Visualizations` directory.

### Chart 1: Monthly Sales Trend (2023)
*Visualizes monthly revenue fluctuations, highlighting the seasonal high and low periods.*
![Monthly Sales Trend](../Visualizations/sales_trend.png)

### Chart 2: Product Category Sales Share
*Donut chart depicting the relative revenue share contribution of the three product categories.*
![Category Sales Share](../Visualizations/category_sales.png)

### Chart 3: Category Performance by Gender
*Grouped bar chart displaying how male and female spending compares across product types.*
![Sales by Category and Gender](../Visualizations/top_products.png)

### Chart 4: Customer Value Segments (RM Analysis)
*Side-by-side bar plots displaying the customer size vs. the total financial contribution of each RM cohort.*
![Customer Value Segments](../Visualizations/customer_segments.png)

### Chart 5: Correlation Heatmap of Numerical Features
*A correlation matrix illustrating the relationships between Age, Quantity, Price, and Total Amount.*
![Correlation Matrix](../Visualizations/heatmap.png)

---

## 6. Key Insights and Business Recommendations

1. **Win Back the "At Risk" Segment (Highest Priority)**:
   - *Insight*: 242 customers belong to the **At Risk** category, representing **57.9% of the store's total revenue ($264,100)**. These are customers who previously spent big (average ticket of $1,091.32) but haven't returned in over 120 days.
   - *Recommendation*: Create a customized "We Miss You" email retargeting campaign offering a high-value incentive (e.g., a $50 gift voucher or 15% discount on high-ticket Electronics) to reactivate this critical revenue engine.
2. **Leverage Seasonal Trends**:
   - *Insight*: Sales peak in May and October, but slump severely in September and March.
   - *Recommendation*: Introduce a major clearance sale or "Back to School" promotion in late August/early September to mitigate the seasonal dip. Run promotional campaigns ahead of May and October to maximize high-buying interest.
3. **Nurture the "Champions" VIPs**:
   - *Insight*: 108 **Champions** represent active high-value spenders (average ticket of $1,157.41), bringing in $125,000 (27.4% of total sales).
   - *Recommendation*: Invite this cohort to a VIP loyalty tier giving them early access to product launches, free shipping, and personalized product recommendations.
4. **Optimize Marketing by Category and Gender**:
   - *Insight*: Females spent 40% more on Beauty than males, while males spent 17% more on Electronics.
   - *Recommendation*: Target digital advertisements for newly launched Beauty collections primarily at female demographics, and target Electronics promotions (gaming consoles, smart home gadgets) at male customer segments. Cross-promote clothing, as it has uniform interest.
5. **Upsell the Active Prospects and Regulars**:
   - *Insight*: Prospects and Regulars represent 417 customers who purchase frequently but only average ~$100 per transaction.
   - *Recommendation*: Introduce item bundles ("Buy 2, Get 1 Free") or threshold discounts ("Spend $150 and save $25") to increase transaction size for low-ticket buyers.

---

## 7. Conclusion
This retail sales dataset shows a healthy, balanced business profile, but with a critical warning sign: **over 57% of total revenue is tied to customers who have gone dormant** (the "At Risk" segment). 

By executing the targeted recommendations—particularly the win-back campaign for dormant high-spenders, VIP treatment for Champions, and cross-category item bundles—the retail store is well-positioned to stabilize seasonal sales volatility, mitigate customer churn, and expand its overall margins. The clean, preprocessed data structure and successful visual exploration in the project lay a firm foundation for future predictive modeling (such as customer segmentation, lifetime value forecasting, or inventory replenishment optimization).
