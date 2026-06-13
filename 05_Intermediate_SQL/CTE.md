# Common Table Expressions (CTE)

## Overview

A Common Table Expression (CTE) is a temporary result set that exists only during the execution of a query.

CTEs make complex queries easier to read, write, and maintain.

## Why It Matters

Data Analysts use CTEs to:

- Break complex queries into smaller steps
- Improve query readability
- Perform advanced analysis
- Replace deeply nested subqueries

---

## Syntax

```sql
WITH cte_name AS
(
    SELECT column_name
    FROM table_name
)
SELECT *
FROM cte_name;
```

---

## Sample Dataset

### Employees

| Employee_ID | Name | Salary |
|------------|------|---------|
| 1 | Rahul | 40000 |
| 2 | Priya | 70000 |
| 3 | Aman | 55000 |
| 4 | Neha | 80000 |

---

## Example

Find employees earning above average salary.

```sql
WITH AverageSalary AS
(
    SELECT AVG(Salary) AS Avg_Salary
    FROM Employees
)
SELECT
Name,
Salary
FROM Employees
WHERE Salary >
(
    SELECT Avg_Salary
    FROM AverageSalary
);
```

### Result

| Name | Salary |
|------|---------|
| Priya | 70000 |
| Neha | 80000 |

---

## Visual Explanation

```text
Step 1
Create CTE

AverageSalary
|
|-- Avg_Salary = 61250

Step 2
Use CTE in Main Query
```

---

## CTE vs Subquery

### Subquery

```sql
SELECT *
FROM Employees
WHERE Salary >
(
    SELECT AVG(Salary)
    FROM Employees
);
```

### CTE

```sql
WITH AverageSalary AS
(
    SELECT AVG(Salary) AS Avg_Salary
    FROM Employees
)
SELECT *
FROM Employees;
```

CTEs are generally easier to read.

---

## Business Use Case

Find customers spending above average revenue.

```sql
WITH RevenueStats AS
(
    SELECT AVG(Revenue) AS Avg_Revenue
    FROM Customers
)
SELECT *
FROM Customers
WHERE Revenue >
(
    SELECT Avg_Revenue
    FROM RevenueStats
);
```

---

## Interview Questions

### What is a CTE?

A temporary result set used within a query.

### Why use CTEs?

To improve readability and simplify complex SQL.

### Can multiple CTEs be used?

Yes.

---

## Practice Questions

1. Find employees earning above average salary.
2. Find products priced above average.
3. Create multiple CTEs in a query.

---

## Key Takeaways

- CTE stands for Common Table Expression.
- Improves query readability.
- Often replaces complex subqueries.
- Widely used in analytics queries.
