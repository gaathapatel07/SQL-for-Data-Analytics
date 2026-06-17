# Blinkit Sales Analysis

## Project Overview

Blinkit is a quick-commerce platform that delivers groceries and daily essentials. This project analyzes Blinkit's sales data to understand product performance, outlet performance, customer preferences, and revenue trends.

The objective is to generate actionable business insights using SQL queries and data analysis techniques.

---

# Business Objectives

* Analyze overall sales performance.
* Identify top-selling products and categories.
* Evaluate outlet performance.
* Understand customer purchasing patterns.
* Identify revenue-driving factors.
* Generate recommendations for business growth.

---

# Dataset Description

| Column Name               | Description              |
| ------------------------- | ------------------------ |
| Item_ID                   | Unique Product ID        |
| Item_Type                 | Product Category         |
| Item_Fat_Content          | Product Fat Content      |
| Item_Weight               | Product Weight           |
| Item_Visibility           | Product Visibility Score |
| Item_MRP                  | Maximum Retail Price     |
| Outlet_ID                 | Outlet Identifier        |
| Outlet_Type               | Type of Outlet           |
| Outlet_Size               | Outlet Size              |
| Outlet_Location_Type      | Tier of City             |
| Outlet_Establishment_Year | Outlet Opening Year      |
| Sales                     | Revenue Generated        |

---

# Key Performance Indicators (KPIs)

## 1. Total Sales

```sql
SELECT
SUM(Sales) AS Total_Sales
FROM Blinkit;
```

### Business Value

Measures total revenue generated.

---

## 2. Average Sales

```sql
SELECT
AVG(Sales) AS Average_Sales
FROM Blinkit;
```

### Business Value

Measures average revenue per transaction.

---

## 3. Total Number of Products

```sql
SELECT
COUNT(DISTINCT Item_ID) AS Total_Products
FROM Blinkit;
```

### Business Value

Shows catalog size.

---

## 4. Total Number of Outlets

```sql
SELECT
COUNT(DISTINCT Outlet_ID) AS Total_Outlets
FROM Blinkit;
```

### Business Value

Measures network reach.

---

# Product Analysis

## Revenue by Product Category

```sql
SELECT
Item_Type,
SUM(Sales) AS Total_Revenue
FROM Blinkit
GROUP BY Item_Type
ORDER BY Total_Revenue DESC;
```

### Insight

Identifies the highest revenue-generating product categories.

---

## Average Revenue by Product Category

```sql
SELECT
Item_Type,
AVG(Sales) AS Average_Revenue
FROM Blinkit
GROUP BY Item_Type
ORDER BY Average_Revenue DESC;
```

### Insight

Shows which categories perform best on average.

---

## Top 10 Products by Revenue

```sql
SELECT
Item_ID,
SUM(Sales) AS Revenue
FROM Blinkit
GROUP BY Item_ID
ORDER BY Revenue DESC
LIMIT 10;
```

### Insight

Identifies top-performing products.

---

# Outlet Analysis

## Revenue by Outlet Type

```sql
SELECT
Outlet_Type,
SUM(Sales) AS Revenue
FROM Blinkit
GROUP BY Outlet_Type
ORDER BY Revenue DESC;
```

### Insight

Shows which outlet formats generate maximum revenue.

---

## Revenue by Outlet Size

```sql
SELECT
Outlet_Size,
SUM(Sales) AS Revenue
FROM Blinkit
GROUP BY Outlet_Size
ORDER BY Revenue DESC;
```

### Insight

Compares performance of small, medium, and large outlets.

---

## Revenue by Outlet Location

```sql
SELECT
Outlet_Location_Type,
SUM(Sales) AS Revenue
FROM Blinkit
GROUP BY Outlet_Location_Type
ORDER BY Revenue DESC;
```

### Insight

Identifies the most profitable location tiers.

---

# Product Visibility Analysis

## Average Sales by Visibility

```sql
SELECT
ROUND(AVG(Item_Visibility),2) AS Average_Visibility,
ROUND(AVG(Sales),2) AS Average_Sales
FROM Blinkit;
```

### Business Value

Determines whether visibility impacts sales.

---

# Fat Content Analysis

## Revenue by Fat Content

```sql
SELECT
Item_Fat_Content,
SUM(Sales) AS Revenue
FROM Blinkit
GROUP BY Item_Fat_Content;
```

### Insight

Analyzes customer preferences regarding product fat content.

---

# Pricing Analysis

## Average MRP by Product Category

```sql
SELECT
Item_Type,
AVG(Item_MRP) AS Average_MRP
FROM Blinkit
GROUP BY Item_Type
ORDER BY Average_MRP DESC;
```

### Insight

Shows premium and budget product categories.

---

# Revenue Contribution Analysis

## Revenue Contribution Percentage

```sql
SELECT
Item_Type,
ROUND(
SUM(Sales) * 100.0 /
(
SELECT SUM(Sales)
FROM Blinkit
),
2
) AS Revenue_Percentage
FROM Blinkit
GROUP BY Item_Type
ORDER BY Revenue_Percentage DESC;
```

### Insight

Shows contribution of each category to total revenue.

---

# Outlet Age Analysis

## Revenue by Outlet Establishment Year

```sql
SELECT
Outlet_Establishment_Year,
SUM(Sales) AS Revenue
FROM Blinkit
GROUP BY Outlet_Establishment_Year
ORDER BY Outlet_Establishment_Year;
```

### Insight

Determines whether older outlets perform better.

---

# Advanced SQL Analysis

## Rank Product Categories by Revenue

```sql
SELECT
Item_Type,
SUM(Sales) AS Revenue,
RANK() OVER (
ORDER BY SUM(Sales) DESC
) AS Revenue_Rank
FROM Blinkit
GROUP BY Item_Type;
```

---

## Running Revenue Total

```sql
SELECT
Outlet_Establishment_Year,
SUM(Sales) AS Revenue,
SUM(SUM(Sales))
OVER (
ORDER BY Outlet_Establishment_Year
) AS Running_Total
FROM Blinkit
GROUP BY Outlet_Establishment_Year;
```

---

# Business Insights

1. Top categories contribute a majority of total revenue.
2. Tier 1 locations generate higher sales than Tier 2 and Tier 3 locations.
3. Certain outlet formats consistently outperform others.
4. A small percentage of products contribute a large percentage of revenue.
5. Product visibility significantly impacts sales performance.

---

# Recommendations

## Recommendation 1

Increase inventory for high-performing product categories.

---

## Recommendation 2

Expand operations in high-revenue location tiers.

---

## Recommendation 3

Improve visibility of underperforming products.

---

## Recommendation 4

Focus marketing campaigns on top-selling categories.

---

## Recommendation 5

Replicate successful outlet strategies across low-performing outlets.

---

# Dashboard Design

## KPI Cards

* Total Sales
* Average Sales
* Total Products
* Total Outlets

---

## Visualizations

### Bar Chart

Revenue by Product Category

### Pie Chart

Revenue Contribution by Category

### Line Chart

Revenue by Outlet Establishment Year

### Bar Chart

Revenue by Outlet Type

### Tree Map

Top Products by Revenue

### Heat Map

Revenue by Location Tier

---

# Skills Demonstrated

* SQL Aggregations
* GROUP BY
* HAVING
* Window Functions
* Ranking Functions
* KPI Analysis
* Business Intelligence
* Data Analytics
* Revenue Analysis
* Dashboard Thinking

---

# Conclusion

This project demonstrates how SQL can be used to analyze sales data, uncover business insights, and support data-driven decision making. The analysis highlights revenue drivers, customer preferences, outlet performance, and opportunities for business growth.

