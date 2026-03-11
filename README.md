<h1 align="center">Customer Purchase Behavior Analysis <br> Python, SQL & Power BI</h1>
An end-to-end data analytics project that cleans retail customer data using Python, analyzes purchasing behavior with SQL, and visualizes key insights through an interactive Power BI dashboard.
<br><br><br>

<p align="center">
  <img width="650" alt="Customer Behavior Dashboard" src="https://github.com/user-attachments/assets/4fbf9107-3ffd-4495-b320-36e7cffd07ce">
</p>

## Overview

This project analyzes customer purchasing behavior using an end-to-end analytics workflow.  
The dataset was cleaned using **Python (Pandas)**, analyzed with **SQL**, and visualized using an **interactive Power BI dashboard**.

The goal is to identify patterns in customer spending, discount usage, and purchasing trends to generate insights that could help businesses improve marketing strategies and revenue performance.

---

## Business Problem

Retail businesses often collect large amounts of customer purchasing data but struggle to translate that data into actionable insights.

The goal of this project is to analyze customer purchase behavior to answer key business questions such as:

- Which customer segments generate the most revenue?
- How do discounts influence purchasing behavior?
- Do subscription customers spend more than non-subscribed customers?
- Which products and categories drive the most purchases?

By combining Python data cleaning, SQL analysis, and Power BI visualization, this project demonstrates how raw customer data can be transformed into insights that support data-driven business decisions.

---

## Skills Demonstrated

- Data cleaning with Python (Pandas)
- SQL data analysis and aggregation
- Customer segmentation analysis
- Business insight generation
- Interactive dashboard design in Power BI

---

## Key Analytical Questions & Insights

| Analytical Question | Key Insight |
|---------------------|-------------|
| Revenue by gender | Male customers generated higher total revenue in this dataset. |
| Discount usage by product | Certain products have significantly higher discount usage rates, suggesting reliance on promotional pricing. |
| Subscription vs. non-subscription spending | Customers with active subscriptions show higher average purchase amounts and total revenue contribution. |
| Customer segmentation | Repeat and loyal customers represent an important portion of the customer base, highlighting the value of retention strategies. |
| Top products by category | Some product categories consistently appear among the most frequently purchased items, indicating strong demand patterns. |

---

## Dataset
The dataset used in this project contains transactional/customer information used to analyze patterns and trends.

**Example attributes include:**

- Customer demographics  
- Purchase history  
- Product categories  
- Discount usage  
- Revenue metrics  

The dataset is loaded and processed using Python before being stored in a SQL database for further analysis.

---

## Tools & Technologies

| Tool | Purpose |
|-----|------|
| Python | Data loading, cleaning, and exploratory analysis |
| Pandas | Data manipulation and transformation |
| SQL (PostgreSQL / MySQL / SQL Server) | Querying and aggregating data |
| Power BI | Interactive dashboard and visualization |
| Jupyter Notebook | Data exploration and analysis |
| Git / GitHub | Version control and project documentation |

---

## Data Pipeline

Raw Excel Dataset  
↓  
Raw Excel to CSV
↓ 
Python (Pandas) Data Cleaning  
↓  
Cleaned Dataset  
↓  
SQL Analysis  
↓  
Power BI Dashboard


## Project Steps

### 1. Data Loading

- Imported the dataset into Python using Pandas  
- Verified column types and dataset structure  
- Performed initial data inspection  

```python
import pandas as pd

df = pd.read_csv("dataset.csv")
df.head()

```

### 2. Exploratory Data Analysis (EDA)

Performed exploratory analysis to understand the data.

Key steps included:

- Checking missing values

- Identifying outliers

- Understanding distributions

- Analyzing correlations

```python

df.describe()
df.isnull().sum()
```
Visualizations were used to better understand patterns and trends.


### 3. Data Cleaning

Data cleaning steps included:

- Handling missing values

- Standardizing column names

- Converting data types

- Removing duplicates

- Creating derived features

```python

df.columns = df.columns.str.lower().str.replace(" ", "_")
df.drop_duplicates(inplace=True)
```

### 4. SQL Analysis

The cleaned dataset was loaded into a SQL database to perform analytical queries.

### Example SQL queries:

Top products with highest discount usage

```SQL
SELECT item_purchased,
ROUND(100 * SUM(CASE WHEN discount_applied = 'YES' THEN 1 ELSE 0 END)/COUNT(*),2) AS discount_rate
FROM customer
GROUP BY item_purchased
ORDER BY discount_rate DESC
LIMIT 5;
```

## Customer segmentation

```SQL
SELECT 
CASE 
    WHEN previous_purchases = 0 THEN 'New'
    WHEN previous_purchases BETWEEN 1 AND 5 THEN 'Returning'
    ELSE 'Loyal'
END AS customer_segment,
COUNT(*) AS customers
FROM customer
GROUP BY customer_segment;
```

## Dashboard

A Power BI dashboard was built to visualize the key insights from the analysis.  Power BI was connected directly to the PostgreSQL database so the dashboard reflects the cleaned analytical dataset.

<img width="864" height="550" alt="image" src="https://github.com/user-attachments/assets/4fbf9107-3ffd-4495-b320-36e7cffd07ce" />


### Dashboard features include:

- Revenue analysis

- Customer segmentation

- Discount usage patterns

- Product performance

- Interactive filters

### Example visuals include:

- KPI cards

- Bar charts

- Donut charts

- Time series analysis


## Results & Insights

Key insights discovered during the analysis:

- Male customers generated significantly higher total revenue than female customers in this dataset.

- Several products show a high percentage of purchases made with discounts, indicating that some product categories rely more heavily on promotional pricing.

- Customers with active subscriptions demonstrate higher average purchase amounts and contribute greater total revenue than non-subscribed customers.

- Repeat and loyal customers represent a meaningful portion of the customer base, highlighting the importance of retention strategies and loyalty programs.

- Certain product categories consistently appear among the most frequently purchased items, suggesting strong customer demand and potential opportunities for targeted promotions.

#### These insights can help businesses optimize pricing, marketing, and customer retention strategies.


## Business Recommendations

Based on the analysis, several actionable recommendations can be made:

- Increase marketing efforts aimed at converting customers into subscription members, as subscribed customers demonstrate higher spending behavior.

- Evaluate pricing and promotion strategies for products with high discount usage to ensure discounts are effectively driving revenue rather than reducing margins.

- Develop retention strategies targeting repeat and loyal customers, as they represent a valuable portion of the customer base.

- Focus inventory and marketing on consistently high-performing product categories to maximize sales opportunities.


## Future Improvements

- Add predictive modeling

- Deploy dashboard to Power BI Service

- Automate data pipeline

- Integrate real-time data updates


## What I Learned

Through this project, I strengthened my ability to:

- clean and prepare raw Excel data using Python
- write SQL queries to answer business questions
- translate query results into dashboard visuals in Power BI
- think beyond the data by identifying business insights and recommendations


## How to Run the Project
### 1. Clone the Repository

```Bash
git clone https://github.com/yourusername/data-analytics-project.git
cd data-analytics-project
```
### 2. Install Dependencies
```Bash
pip install pandas numpy matplotlib seaborn sqlalchemy psycopg2
```

### 3. Run the Python Analysis
```Bash
python analysis.py
```

### 4. Run SQL Queries

Load the cleaned dataset into your SQL database and execute the queries provided in the sql_queries.sql 
```Bash
sql_queries.sql
```
file.

### 5. Open the Power BI Dashboard

Open the .pbix file in Power BI Desktop to interact with the dashboard.

### Project Structure

```
data-analytics-project
│
├── data
│   ├── raw
│   └── cleaned
│
├── notebooks
│   └── eda.ipynb
│
├── sql
│   └── analysis_queries.sql
│
├── dashboard
│   └── powerbi_dashboard.pbix
│
├── scripts
│   └── data_cleaning.py
│
└── README.md
```


![Python](https://img.shields.io/badge/Python-3.11-blue)
![SQL](https://img.shields.io/badge/SQL-PostgreSQL-green)
![Power BI](https://img.shields.io/badge/PowerBI-Dashboard-yellow)

