# E-Commerce Sales Analysis

## Project Overview

This project analyzes sales data from an e-commerce platform to understand customer behavior, product performance, revenue trends, and business growth opportunities.

The objective is to use SQL to answer key business questions and generate actionable insights.

---

# Business Objectives

* Analyze overall sales performance.
* Identify top-selling products.
* Find high-value customers.
* Track revenue trends.
* Understand customer purchasing behavior.
* Improve business decision-making.

---

# Dataset Description

| Column Name    | Description         |
| -------------- | ------------------- |
| Order_ID       | Unique Order ID     |
| Customer_ID    | Customer Identifier |
| Product_ID     | Product Identifier  |
| Product_Name   | Product Name        |
| Category       | Product Category    |
| Order_Date     | Date of Purchase    |
| Quantity       | Quantity Purchased  |
| Price          | Product Price       |
| Revenue        | Sales Revenue       |
| City           | Customer City       |
| Payment_Method | Payment Type        |

---

# Key Performance Indicators

## Total Revenue

```sql
SELECT
SUM(Revenue) AS Total_Revenue
FROM Orders;
```

---

## Total Orders

```sql
SELECT
COUNT(DISTINCT Order_ID) AS Total_Orders
FROM Orders;
```

---

## Total Customers

```sql
SELECT
COUNT(DISTINCT Customer_ID) AS Total_Customers
FROM Orders;
```

---

## Average Order Value

```sql
SELECT
AVG(Revenue) AS Average_Order_Value
FROM Orders;
```

---

# Product Analysis

## Top 10 Products by Revenue

```sql
SELECT
Product_Name,
SUM(Revenue) AS Total_Revenue
FROM Orders
GROUP BY Product_Name
ORDER BY Total_Revenue DESC
LIMIT 10;
```

---

## Revenue by Category

```sql
SELECT
Category,
SUM(Revenue) AS Revenue
FROM Orders
GROUP BY Category
ORDER BY Revenue DESC;
```

---

## Best Selling Products

```sql
SELECT
Product_Name,
SUM(Quantity) AS Total_Quantity
FROM Orders
GROUP BY Product_Name
ORDER BY Total_Quantity DESC
LIMIT 10;
```

---

# Customer Analysis

## Top Customers by Revenue

```sql
SELECT
Customer_ID,
SUM(Revenue) AS Total_Spent
FROM Orders
GROUP BY Customer_ID
ORDER BY Total_Spent DESC
LIMIT 10;
```

---

## Average Customer Spend

```sql
SELECT
AVG(Customer_Revenue)
FROM
(
SELECT
Customer_ID,
SUM(Revenue) AS Customer_Revenue
FROM Orders
GROUP BY Customer_ID
) Customers;
```

---

# Revenue Trend Analysis

## Monthly Revenue

```sql
SELECT
YEAR(Order_Date) AS Year,
MONTH(Order_Date) AS Month,
SUM(Revenue) AS Revenue
FROM Orders
GROUP BY
YEAR(Order_Date),
MONTH(Order_Date)
ORDER BY
Year,
Month;
```

---

## Running Revenue Total

```sql
SELECT
Order_Date,
Revenue,
SUM(Revenue)
OVER (
ORDER BY Order_Date
) AS Running_Total
FROM Orders;
```

---

# Geographic Analysis

## Revenue by City

```sql
SELECT
City,
SUM(Revenue) AS Revenue
FROM Orders
GROUP BY City
ORDER BY Revenue DESC;
```

---

## Top Performing Cities

```sql
SELECT
City,
SUM(Revenue) AS Revenue
FROM Orders
GROUP BY City
ORDER BY Revenue DESC
LIMIT 10;
```

---

# Payment Method Analysis

## Revenue by Payment Method

```sql
SELECT
Payment_Method,
SUM(Revenue) AS Revenue
FROM Orders
GROUP BY Payment_Method
ORDER BY Revenue DESC;
```

---

# Advanced SQL Analysis

## Rank Products by Revenue

```sql
SELECT
Product_Name,
SUM(Revenue) AS Revenue,
RANK() OVER (
ORDER BY SUM(Revenue) DESC
) AS Product_Rank
FROM Orders
GROUP BY Product_Name;
```

---

## Top 3 Products in Each Category

```sql
SELECT *
FROM
(
SELECT
Category,
Product_Name,
SUM(Revenue) AS Revenue,
ROW_NUMBER() OVER (
PARTITION BY Category
ORDER BY SUM(Revenue) DESC
) AS Row_Num
FROM Orders
GROUP BY Category, Product_Name
) Ranked_Products
WHERE Row_Num <= 3;
```

---

# Business Insights

1. A small percentage of products contribute most revenue.
2. Top customers account for a significant share of sales.
3. Certain cities generate substantially higher revenue.
4. Specific payment methods are preferred by customers.
5. Revenue shows seasonal trends throughout the year.

---

# Recommendations

## Recommendation 1

Increase inventory for high-selling products.

---

## Recommendation 2

Launch loyalty programs for top customers.

---

## Recommendation 3

Expand marketing in high-performing cities.

---

## Recommendation 4

Bundle products from top-selling categories.

---

## Recommendation 5

Optimize promotions during low-revenue periods.

---

# Dashboard Design

## KPI Cards

* Total Revenue
* Total Orders
* Total Customers
* Average Order Value

---

## Charts

### Revenue by Category

Bar Chart

### Monthly Revenue Trend

Line Chart

### Top Products

Horizontal Bar Chart

### Revenue by City

Map Visualization

### Payment Method Distribution

Pie Chart

---

# Skills Demonstrated

* SQL Aggregations
* GROUP BY
* HAVING
* Window Functions
* Ranking Functions
* Customer Analytics
* Revenue Analysis
* KPI Development
* Business Intelligence

---

# Conclusion

This project demonstrates how SQL can be used to analyze e-commerce sales data, uncover revenue drivers, identify customer trends, and support data-driven business decisions.
