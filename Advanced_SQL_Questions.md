# Advanced SQL Interview Questions

## Question 1: Find the Second Highest Salary

### Query

```sql id="lt11"
SELECT MAX(Salary) AS Second_Highest_Salary
FROM Employees
WHERE Salary <
(
    SELECT MAX(Salary)
    FROM Employees
);
```

### Explanation

Finds the highest salary below the maximum salary.

---

## Question 2: Find the Nth Highest Salary

### Query

```sql id="lt12"
SELECT Salary
FROM
(
    SELECT
    Salary,
    DENSE_RANK() OVER (
        ORDER BY Salary DESC
    ) AS Salary_Rank
    FROM Employees
) Ranked_Salaries
WHERE Salary_Rank = 3;
```

### Explanation

Returns the 3rd highest salary.

Change 3 to any value of N.

---

## Question 3: Remove Duplicate Records

### Query

```sql id="lt13"
WITH DuplicateRows AS
(
    SELECT *,
    ROW_NUMBER() OVER (
        PARTITION BY Email
        ORDER BY Customer_ID
    ) AS Row_Num
    FROM Customers
)
SELECT *
FROM DuplicateRows
WHERE Row_Num = 1;
```

### Explanation

Keeps only the first occurrence of duplicate records.

---

## Question 4: Top 3 Customers Per Region

### Query

```sql id="lt14"
SELECT *
FROM
(
    SELECT
    Region,
    Customer_Name,
    Revenue,
    ROW_NUMBER() OVER (
        PARTITION BY Region
        ORDER BY Revenue DESC
    ) AS Rank_Number
    FROM Customers
) Ranked_Customers
WHERE Rank_Number <= 3;
```

### Explanation

Returns top 3 customers from each region.

---

## Question 5: Running Total

### Query

```sql id="lt15"
SELECT
Order_Date,
Revenue,
SUM(Revenue) OVER (
    ORDER BY Order_Date
) AS Running_Total
FROM Orders;
```

### Explanation

Calculates cumulative revenue over time.

---

## Question 6: Month-over-Month Growth

### Query

```sql id="lt16"
SELECT
Month,
Revenue,
Revenue -
LAG(Revenue)
OVER (
    ORDER BY Month
) AS Revenue_Growth
FROM Monthly_Sales;
```

### Explanation

Compares current month's revenue with previous month's revenue.

---

## Question 7: Find Consecutive Login Days

### Query

```sql id="lt17"
SELECT
User_ID,
Login_Date,
LAG(Login_Date)
OVER (
    PARTITION BY User_ID
    ORDER BY Login_Date
) AS Previous_Login
FROM User_Logins;
```

### Explanation

Used to detect consecutive user activity.

---

## Question 8: Find Customer Retention

### Query

```sql id="lt18"
SELECT
Customer_ID,
COUNT(Order_ID) AS Total_Orders
FROM Orders
GROUP BY Customer_ID
HAVING COUNT(Order_ID) > 1;
```

### Explanation

Customers with multiple orders are considered retained customers.

---

## Question 9: Rank Products by Sales

### Query

```sql id="lt19"
SELECT
Product_Name,
Revenue,
RANK() OVER (
    ORDER BY Revenue DESC
) AS Product_Rank
FROM Products;
```

### Explanation

Ranks products based on revenue.

---

## Question 10: Find Highest Revenue Product in Each Category

### Query

```sql id="lt20"
SELECT *
FROM
(
    SELECT
    Category,
    Product_Name,
    Revenue,
    ROW_NUMBER() OVER (
        PARTITION BY Category
        ORDER BY Revenue DESC
    ) AS Row_Num
    FROM Products
) Ranked_Products
WHERE Row_Num = 1;
```

### Explanation

Returns the top product from every category.

---

## Question 11: Revenue Contribution Percentage

### Query

```sql id="lt21"
SELECT
Product_Name,
Revenue,
ROUND(
Revenue * 100.0 /
SUM(Revenue) OVER (),
2
) AS Revenue_Percentage
FROM Products;
```

### Explanation

Calculates each product's contribution to total revenue.

---

## Question 12: Identify Customers Above Average Revenue

### Query

```sql id="lt22"
SELECT *
FROM Customers
WHERE Revenue >
(
    SELECT AVG(Revenue)
    FROM Customers
);
```

### Explanation

Returns customers whose revenue is greater than the average customer revenue.

---

## Question 13: Find Employees Earning More Than Their Department Average

### Query

```sql id="lt23"
SELECT *
FROM Employees E
WHERE Salary >
(
    SELECT AVG(Salary)
    FROM Employees
    WHERE Department = E.Department
);
```

### Explanation

Compares employees against their department's average salary.

---

## Question 14: Find Most Recent Order Per Customer

### Query

```sql id="lt24"
SELECT *
FROM
(
    SELECT *,
    ROW_NUMBER() OVER (
        PARTITION BY Customer_ID
        ORDER BY Order_Date DESC
    ) AS Row_Num
    FROM Orders
) RecentOrders
WHERE Row_Num = 1;
```

### Explanation

Returns the latest order for every customer.

---

## Question 15: Find Top Performing Region

### Query

```sql id="lt25"
SELECT
Region,
SUM(Revenue) AS Total_Revenue
FROM Sales
GROUP BY Region
ORDER BY Total_Revenue DESC
LIMIT 1;
```

### Explanation

Finds the region generating the highest revenue.

---

## Key Takeaways

* Advanced SQL interviews focus heavily on Window Functions.
* Learn ROW_NUMBER(), RANK(), DENSE_RANK(), LAG(), and LEAD().
* Practice ranking, running totals, retention, and growth calculations.
* Most real-world analytics problems combine multiple SQL concepts.

