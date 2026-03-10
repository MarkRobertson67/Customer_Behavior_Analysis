# Data Analytics Project

## Overview
This project demonstrates an end-to-end data analytics workflow using Python, SQL, and Power BI. The goal of the project is to analyze a dataset, uncover insights through exploratory data analysis (EDA), clean and transform the data, and present findings through an interactive dashboard and written report.

The project follows a typical real-world analytics pipeline used by data analysts and business intelligence teams.

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

Excel Dataset  
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

- Certain products have significantly higher discount usage rates.

- Loyal customers contribute a disproportionate share of total revenue.

- Discount strategies impact purchasing behavior differently across customer segments.

- Seasonal trends influence purchasing patterns.

#### These insights can help businesses optimize pricing, marketing, and customer retention strategies.


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

## Future Improvements

- Add predictive modeling

- Deploy dashboard to Power BI Service

- Automate data pipeline

- Integrate real-time data updates


![Python](https://img.shields.io/badge/Python-3.11-blue)
![SQL](https://img.shields.io/badge/SQL-PostgreSQL-green)
![Power BI](https://img.shields.io/badge/PowerBI-Dashboard-yellow)

