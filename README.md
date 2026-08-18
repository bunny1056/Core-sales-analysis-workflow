# Walmart Sales Analytics

An end-to-end sales analytics project using **MySQL and Python** to analyze Walmart transaction data, identify demand patterns, evaluate branch and product performance, and generate insights for inventory and pricing decisions.

## Features

* Analyzed **10K+ Walmart transactions**
* Built a structured **MySQL analytics pipeline**
* Created **15+ SQL queries** for business analysis
* Identified **14+ data-driven insights**
* Analyzed product, branch, region, customer, and profitability trends
* Identified top-selling products and high-revenue regions
* Evaluated branch-level sales performance
* Analyzed customer purchasing patterns
* Examined monthly sales trends
* Built interactive dashboards for business reporting

## Tech Stack

* **MySQL** — Data storage and SQL analytics
* **Python** — Data processing and exploratory analysis
* **Pandas** — Data manipulation
* **Matplotlib** — Data visualization
* **Power BI / Dashboarding** — Interactive business insights

## Dataset

The dataset contains Walmart transaction-level sales information including:

```text
Transaction
Date
Branch
Region
Product
Customer Type
Sales
Profit
```

## Analytics Workflow

```text
Walmart Transaction Data
          |
          v
    Data Cleaning
          |
          v
      MySQL Database
          |
          v
      SQL Analysis
          |
     +----+----+----+----+
     |    |    |    |    |
     v    v    v    v    v
 Product Region Branch Customer Profit
 Analysis Analysis Analysis Analysis Analysis
     |    |    |    |    |
     +----+----+----+----+
              |
              v
       Business Insights
              |
              v
       Interactive Dashboard
```

## Key Analysis

### Product Performance

Identified the highest-selling and most profitable products to support inventory planning.

```sql
SELECT
    product,
    SUM(sales) AS total_sales,
    SUM(profit) AS total_profit
FROM walmart_sales
GROUP BY product
ORDER BY total_sales DESC;
```

### Regional Performance

Compared sales across different regions to identify high-revenue markets.

```sql
SELECT
    region,
    SUM(sales) AS total_sales,
    SUM(profit) AS total_profit
FROM walmart_sales
GROUP BY region
ORDER BY total_sales DESC;
```

### Branch Performance

Evaluated branches based on revenue, average transaction value, and transaction volume.

```sql
SELECT
    branch,
    SUM(sales) AS revenue,
    AVG(sales) AS avg_transaction,
    COUNT(*) AS transactions
FROM walmart_sales
GROUP BY branch
ORDER BY revenue DESC;
```

### Customer Analysis

Analyzed purchasing behavior across different customer segments.

```sql
SELECT
    customer_type,
    COUNT(*) AS transactions,
    SUM(sales) AS total_sales,
    AVG(sales) AS avg_sales
FROM walmart_sales
GROUP BY customer_type;
```

### Monthly Sales Trends

Tracked sales performance over time to identify demand patterns and seasonal changes.

```sql
SELECT
    YEAR(date) AS year,
    MONTH(date) AS month,
    SUM(sales) AS monthly_sales
FROM walmart_sales
GROUP BY YEAR(date), MONTH(date)
ORDER BY year, month;
```

## Python Analysis

```python
import pandas as pd

df = pd.read_csv("walmart_sales.csv")

# Total sales
print("Total Sales:", df["sales"].sum())

# Top products
top_products = (
    df.groupby("product")["sales"]
    .sum()
    .sort_values(ascending=False)
    .head(10)
)

print(top_products)

# Regional performance
region_sales = (
    df.groupby("region")["sales"]
    .sum()
    .sort_values(ascending=False)
)

print(region_sales)
```

## Dashboard

The dashboard provides an interactive view of:

* Total sales
* Total profit
* Transaction volume
* Top-selling products
* Branch performance
* Regional revenue
* Customer trends
* Monthly sales trends
* Product profitability

### Key KPIs

| KPI                 | Purpose                     |
| ------------------- | --------------------------- |
| Total Sales         | Overall revenue performance |
| Total Profit        | Business profitability      |
| Transactions        | Sales volume                |
| Average Transaction | Customer spending           |
| Top Product         | Inventory prioritization    |
| Top Region          | Geographic performance      |

## Project Structure

```text
walmart-sales-analytics/
│
├── data/
│   └── walmart_sales.csv
│
├── sql/
│   ├── sales_analysis.sql
│   ├── product_analysis.sql
│   ├── branch_analysis.sql
│   └── customer_analysis.sql
│
├── notebooks/
│   └── exploratory_analysis.ipynb
│
├── src/
│   ├── data_cleaning.py
│   └── analysis.py
│
├── dashboard/
│   └── walmart_dashboard.pbix
│
├── requirements.txt
└── README.md
```

## Installation

```bash
git clone <repository-url>
cd walmart-sales-analytics

pip install -r requirements.txt
```

Import the dataset into MySQL and execute the SQL scripts from the `sql/` directory.

## Results

* **10K+** transactions analyzed
* **15+** SQL queries developed
* **14+** business insights identified
* Top-selling products identified for inventory planning
* High-revenue regions identified for regional strategy
* Branch performance compared using sales and profitability metrics
* Customer purchasing trends analyzed
* Interactive dashboard created for business decision-making

## Business Impact

The analysis provides data-driven support for:

* **Inventory planning** by identifying high-demand products
* **Pricing strategy** through product-level profitability analysis
* **Regional planning** by identifying high-revenue locations
* **Branch optimization** through performance comparisons
* **Customer strategy** through purchasing behavior analysis
