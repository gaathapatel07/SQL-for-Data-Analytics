# Swiggy & Zomato Food Delivery Analysis

## Project Overview

Swiggy and Zomato are India's leading food delivery platforms. This project analyzes restaurant performance, customer ordering behavior, delivery efficiency, and revenue generation.

The objective is to identify business opportunities, improve customer experience, and optimize delivery operations using SQL.

---

# Business Objectives

* Analyze overall platform revenue.
* Identify top-performing restaurants.
* Understand customer ordering patterns.
* Evaluate delivery performance.
* Analyze city-wise demand.
* Improve operational efficiency.

---

# Dataset Description

| Column Name     | Description           |
| --------------- | --------------------- |
| Order_ID        | Unique Order ID       |
| Customer_ID     | Customer Identifier   |
| Restaurant_ID   | Restaurant Identifier |
| Restaurant_Name | Restaurant Name       |
| City            | Customer City         |
| Cuisine         | Food Category         |
| Order_Date      | Order Date            |
| Delivery_Time   | Delivery Duration     |
| Order_Value     | Order Revenue         |
| Delivery_Fee    | Delivery Charges      |
| Rating          | Customer Rating       |
| Payment_Method  | Payment Mode          |

---

# Key Performance Indicators

## Total Revenue

```sql
SELECT
SUM(Order_Value) AS Total_Revenue
FROM Orders;
```

---

## Total Orders

```sql
SELECT
COUNT(*) AS Total_Orders
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
AVG(Order_Value) AS Average_Order_Value
FROM Orders;
```

---

# Restaurant Analysis

## Top 10 Restaurants by Revenue

```sql
SELECT
Restaurant_Name,
SUM(Order_Value) AS Revenue
FROM Orders
GROUP BY Restaurant_Name
ORDER BY Revenue DESC
LIMIT 10;
```

---

## Restaurant Order Count

```sql
SELECT
Restaurant_Name,
COUNT(*) AS Total_Orders
FROM Orders
GROUP BY Restaurant_Name
ORDER BY Total_Orders DESC;
```

---

## Average Restaurant Rating

```sql
SELECT
Restaurant_Name,
AVG(Rating) AS Average_Rating
FROM Orders
GROUP BY Restaurant_Name
ORDER BY Average_Rating DESC;
```

---

# Cuisine Analysis

## Revenue by Cuisine

```sql
SELECT
Cuisine,
SUM(Order_Value) AS Revenue
FROM Orders
GROUP BY Cuisine
ORDER BY Revenue DESC;
```

---

## Most Popular Cuisines

```sql
SELECT
Cuisine,
COUNT(*) AS Total_Orders
FROM Orders
GROUP BY Cuisine
ORDER BY Total_Orders DESC;
```

---

# Customer Analysis

## Top Customers by Spending

```sql
SELECT
Customer_ID,
SUM(Order_Value) AS Total_Spent
FROM Orders
GROUP BY Customer_ID
ORDER BY Total_Spent DESC
LIMIT 10;
```

---

## Repeat Customers

```sql
SELECT
Customer_ID,
COUNT(*) AS Total_Orders
FROM Orders
GROUP BY Customer_ID
HAVING COUNT(*) > 1;
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
SUM(Order_Value) AS Customer_Revenue
FROM Orders
GROUP BY Customer_ID
) Customer_Data;
```

---

# City Analysis

## Revenue by City

```sql
SELECT
City,
SUM(Order_Value) AS Revenue
FROM Orders
GROUP BY City
ORDER BY Revenue DESC;
```

---

## Orders by City

```sql
SELECT
City,
COUNT(*) AS Total_Orders
FROM Orders
GROUP BY City
ORDER BY Total_Orders DESC;
```

---

# Delivery Analysis

## Average Delivery Time

```sql
SELECT
AVG(Delivery_Time) AS Average_Delivery_Time
FROM Orders;
```

---

## Fastest Delivering Cities

```sql
SELECT
City,
AVG(Delivery_Time) AS Average_Time
FROM Orders
GROUP BY City
ORDER BY Average_Time;
```

---

## Restaurants with Longest Delivery Time

```sql
SELECT
Restaurant_Name,
AVG(Delivery_Time) AS Average_Time
FROM Orders
GROUP BY Restaurant_Name
ORDER BY Average_Time DESC
LIMIT 10;
```

---

# Payment Analysis

## Revenue by Payment Method

```sql
SELECT
Payment_Method,
SUM(Order_Value) AS Revenue
FROM Orders
GROUP BY Payment_Method;
```

---

## Most Preferred Payment Method

```sql
SELECT
Payment_Method,
COUNT(*) AS Total_Transactions
FROM Orders
GROUP BY Payment_Method
ORDER BY Total_Transactions DESC;
```

---

# Advanced SQL Analysis

## Rank Restaurants by Revenue

```sql
SELECT
Restaurant_Name,
SUM(Order_Value) AS Revenue,
RANK() OVER (
ORDER BY SUM(Order_Value) DESC
) AS Revenue_Rank
FROM Orders
GROUP BY Restaurant_Name;
```

---

## Top 3 Restaurants per City

```sql
SELECT *
FROM
(
SELECT
City,
Restaurant_Name,
SUM(Order_Value) AS Revenue,
ROW_NUMBER() OVER (
PARTITION BY City
ORDER BY SUM(Order_Value) DESC
) AS Row_Num
FROM Orders
GROUP BY City, Restaurant_Name
) Ranked_Restaurants
WHERE Row_Num <= 3;
```

---

## Running Revenue Analysis

```sql
SELECT
Order_Date,
SUM(Order_Value) AS Daily_Revenue,
SUM(SUM(Order_Value))
OVER (
ORDER BY Order_Date
) AS Running_Revenue
FROM Orders
GROUP BY Order_Date;
```

---

# Business Insights

1. A few restaurants generate a majority of platform revenue.
2. Popular cuisines contribute significantly to order volume.
3. Repeat customers account for a large portion of revenue.
4. Delivery performance directly impacts ratings.
5. Metro cities contribute the highest revenue.

---

# Recommendations

## Recommendation 1

Promote top-performing restaurants through featured listings.

---

## Recommendation 2

Improve delivery operations in slow-performing areas.

---

## Recommendation 3

Create loyalty programs for repeat customers.

---

## Recommendation 4

Expand partnerships with high-demand cuisine providers.

---

## Recommendation 5

Offer personalized promotions based on customer ordering behavior.

---

# Dashboard Design

## KPI Cards

* Total Revenue
* Total Orders
* Total Customers
* Average Order Value
* Average Delivery Time

---

## Visualizations

### Revenue by City

Bar Chart

### Revenue by Cuisine

Bar Chart

### Top Restaurants

Horizontal Bar Chart

### Delivery Performance

Line Chart

### Payment Method Distribution

Pie Chart

### Customer Spending Analysis

Histogram

---

# Skills Demonstrated

* SQL Aggregations
* Window Functions
* Ranking Functions
* Customer Analytics
* Revenue Analysis
* Operational Analytics
* KPI Development
* Business Intelligence

---

# Conclusion

This project demonstrates how SQL can be used to analyze food delivery platform data, improve operational efficiency, optimize customer experience, and support strategic business decisions through data-driven insights.



