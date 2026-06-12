# MIN() and MAX() Functions

## Overview

MIN() returns the smallest value in a column.

MAX() returns the largest value in a column.

These functions are commonly used to identify best and worst performers.

---

## Why They Matter

Data Analysts use MIN() and MAX() to:

- Find highest sales
- Find lowest sales
- Analyze salary ranges
- Identify top-performing products

---

## Sample Dataset

### Employees Table

| Employee_ID | Name | Salary |
|------------|------|---------|
| 1 | Rahul | 40000 |
| 2 | Priya | 65000 |
| 3 | Aman | 55000 |
| 4 | Neha | 80000 |

---

## MIN() Syntax

```sql
SELECT MIN(column_name)
FROM table_name;
```

---

## Example

```sql
SELECT MIN(Salary)
FROM Employees;
```

### Result

| MIN(Salary) |
|------------|
| 40000 |

---

## MAX() Syntax

```sql
SELECT MAX(column_name)
FROM table_name;
```

---

## Example

```sql
SELECT MAX(Salary)
FROM Employees;
```

### Result

| MAX(Salary) |
|------------|
| 80000 |

---

## Using MIN and MAX Together

```sql
SELECT
MIN(Salary) AS Lowest_Salary,
MAX(Salary) AS Highest_Salary
FROM Employees;
```

### Result

| Lowest_Salary | Highest_Salary |
|--------------|---------------|
| 40000 | 80000 |

---

## Business Use Case

Find highest and lowest sales.

```sql
SELECT
MIN(Revenue) AS Lowest_Revenue,
MAX(Revenue) AS Highest_Revenue
FROM Sales;
```

This helps identify performance boundaries.

---

## Common Mistakes

### Using MIN/MAX on Wrong Columns

These functions work best on numeric and date columns.

---

## Interview Questions

### What does MIN() return?

The smallest value.

### What does MAX() return?

The largest value.

### Can MIN() and MAX() work on dates?

Yes.

```sql
SELECT MIN(Order_Date)
FROM Orders;
```

---

## Practice Questions

1. Find the lowest salary.
2. Find the highest revenue.
3. Find the earliest order date.

---

## Key Takeaways

- MIN() returns the smallest value.
- MAX() returns the largest value.
- Useful for performance analysis.
- Frequently used in dashboards and reports.
