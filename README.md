# SQL Exploratory Data Analysis — Global Layoffs Dataset

## Project Overview

This project focuses on performing Exploratory Data Analysis (EDA) on a real-world global layoffs dataset using SQL.

The objective of this analysis was to explore layoff trends across companies, industries, countries, funding stages, and time periods in order to uncover meaningful business insights and patterns.

Before analysis, the dataset was cleaned and standardized using SQL-based data cleaning techniques such as duplicate removal, null handling, data standardization, and date formatting.

This project simulates a real-world analyst workflow:

* Raw Data → Data Cleaning → Exploratory Data Analysis → Business Insights

---

# Dataset Information

The dataset contains global layoffs data including:

* Company names
* Industry types
* Countries and locations
* Total employees laid off
* Percentage layoffs
* Funding raised
* Company stage
* Layoff dates

Dataset Source:
Layoffs Dataset from Kaggle

---

# Project Objectives

The main goals of this project were to:

* Analyze companies with the highest layoffs
* Identify industries most impacted by layoffs
* Explore layoffs trends across countries and years
* Track rolling cumulative layoffs over time
* Rank top companies by yearly layoffs
* Practice advanced SQL concepts on real-world datasets
* Develop business-oriented analytical thinking

---

# Tools & Technologies Used

* MySQL
* SQL Window Functions
* Common Table Expressions (CTEs)
* Aggregate Functions
* Date Functions
* Git & GitHub

---

# Data Cleaning Process

The dataset was cleaned before performing analysis.

Cleaning tasks included:

* Removing duplicate records
* Creating staging tables
* Standardizing inconsistent values
* Handling null and blank values
* Formatting date columns
* Removing unnecessary rows and columns

Data cleaning queries are included in:

```sql
layoffs_data_cleaning.sql
```

---

# Exploratory Data Analysis (EDA)

EDA queries are included in:

```sql
layoffs_eda.sql
```

The analysis focused on identifying trends, patterns, outliers, and business insights from the layoffs dataset.

---

# Key SQL Concepts Used

## Aggregate Functions

```sql
SUM()
MAX()
MIN()
COUNT()
AVG()
```

## Window Functions

```sql
ROW_NUMBER()
DENSE_RANK()
SUM() OVER()
```

## Date Functions

```sql
YEAR()
SUBSTRING()
STR_TO_DATE()
```

## Common Table Expressions (CTEs)

```sql
WITH cte_name AS (...)
```

---

# Analysis Performed

## Company Analysis

* Companies with the highest total layoffs
* Companies with the largest single-day layoffs
* Companies with complete (100%) layoffs

## Industry Analysis

* Industries most affected by layoffs
* Comparison of layoffs across sectors

## Country & Location Analysis

* Countries with highest layoffs
* Locations most impacted globally

## Time Series Analysis

* Yearly layoffs trends
* Monthly layoffs trends
* Rolling cumulative layoffs over time

## Ranking Analysis

* Top companies by layoffs per year using `DENSE_RANK()`

---

# Example Query — Rolling Cumulative Layoffs

```sql
WITH DATE_CTE AS (
    SELECT
        SUBSTRING(date,1,7) AS month,
        SUM(total_laid_off) AS laid_off_month
    FROM layoffs_staging2
    GROUP BY SUBSTRING(date,1,7)
)

SELECT
    month,
    laid_off_month,
    SUM(laid_off_month)
    OVER(ORDER BY month ASC) AS cumulative_layoffs
FROM DATE_CTE;
```

---

# Key Insights Discovered

* Several startups experienced complete shutdowns with 100% layoffs.
* The technology industry recorded some of the highest layoffs globally.
* Layoffs increased significantly during economic downturn periods.
* Some heavily funded companies still experienced major layoffs or shutdowns.
* The United States had one of the highest total layoffs across the dataset.
* Rolling cumulative analysis showed rapid growth in layoffs during peak periods.

---

# Learning Outcomes

Through this project, I strengthened my understanding of:

* Real-world SQL workflows
* Data cleaning techniques
* Exploratory Data Analysis (EDA)
* Window functions and ranking analysis
* Business-focused analytical thinking
* Writing optimized and readable SQL queries
* Structuring portfolio-ready analytics projects

---

# Author

Pulkit

This project was built as part of my journey in Data Analytics and SQL portfolio development.
