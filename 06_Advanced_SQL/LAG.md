# LAG() Function

## Overview

The `LAG()` function is a Window Function that allows you to access data from a previous row without using a self join.

It is commonly used for trend analysis, growth calculations, and time-series analysis.

---

## Why It Matters

Data Analysts use LAG() to:

* Compare current sales with previous sales
* Calculate month-over-month growth
* Analyze trends
* Track customer activity
* Build business dashboards

---

## Syntax

```sql
LAG(column_name, offset)
OVER (
    ORDER BY column_name
)
```

### Parameters

| Parameter   | Description         |
| ----------- | ------------------- |
| column_name | Column to retrieve  |
| offset      | Number of rows back |
| ORDER BY    | Defines row order   |

---

## Sample Dataset

### Monthly Sales

| Month | Revenue |
| ----- | ------- |
| Jan   | 1000    |
| Feb   | 1500    |
| Mar   | 1800    |
| Apr   | 2200    |

---

## Example

Retrieve previous month's revenue.

```sql
SELECT
Month,
Revenue,
LAG(Revenue, 1)
OVER (
    ORDER BY Month
) AS Previous_Revenue
FROM Sales;
```

### Result

| Month | Revenue | Previous_Revenue |
| ----- | ------- | ---------------- |
| Jan   | 1000    | NULL             |
| Feb   | 1500    | 1000             |
| Mar   | 1800    | 1500             |
| Apr   | 2200    | 1800             |

---

## Visual Explanation

```text
Jan → 1000
Feb → 1500 ← Previous = 1000
Mar → 1800 ← Previous = 1500
Apr → 2200 ← Previous = 1800
```

---

## Calculating Growth

```sql
SELECT
Month,
Revenue,
Revenue -
LAG(Revenue,1)
OVER (
    ORDER BY Month
) AS Revenue_Growth
FROM Sales;
```

### Result

| Month | Revenue | Revenue_Growth |
| ----- | ------- | -------------- |
| Jan   | 1000    | NULL           |
| Feb   | 1500    | 500            |
| Mar   | 1800    | 300            |
| Apr   | 2200    | 400            |

---

## Percentage Growth Calculation

```sql
SELECT
Month,
Revenue,
ROUND(
(
Revenue -
LAG(Revenue)
OVER (ORDER BY Month)
)
* 100.0
/
LAG(Revenue)
OVER (ORDER BY Month),
2
) AS Growth_Percentage
FROM Sales;
```

---

## Using LAG with PARTITION BY

Compare sales within departments.

```sql
SELECT
Department,
Employee,
Revenue,
LAG(Revenue)
OVER (
    PARTITION BY Department
    ORDER BY Revenue
) AS Previous_Revenue
FROM Employee_Sales;
```

---

## Business Use Cases

### Month-over-Month Revenue Growth

```sql
SELECT
Month,
Revenue,
Revenue -
LAG(Revenue)
OVER (
    ORDER BY Month
) AS Growth
FROM Sales;
```

---

### Compare Current Sales with Previous Sales

```sql
SELECT
Product,
Sales,
LAG(Sales)
OVER (
    ORDER BY Sales
) AS Previous_Sales
FROM Product_Sales;
```

---

## Common Mistakes

### Forgetting ORDER BY

Incorrect:

```sql
LAG(Revenue)
OVER ()
```

Correct:

```sql
LAG(Revenue)
OVER (
    ORDER BY Month
)
```

---

## LAG vs LEAD

### LAG()

Gets previous row.

```text
Current Row ← Previous Row
```

### LEAD()

Gets next row.

```text
Current Row → Next Row
```

---

## Interview Questions

### What does LAG() do?

Returns data from a previous row.

### Why use LAG() instead of a self join?

It is simpler, faster, and easier to read.

### What is the default offset?

1

```sql
LAG(Revenue)
```

is equivalent to:

```sql
LAG(Revenue, 1)
```

---

## Practice Questions

1. Compare monthly revenue with the previous month.
2. Calculate month-over-month growth.
3. Compare employee performance with previous employees.
4. Analyze customer spending trends.

---

## Key Takeaways

* LAG() accesses previous row values.
* Commonly used for trend analysis.
* Useful for growth calculations.
* Frequently asked in SQL interviews.
* Eliminates the need for self joins in many scenarios.

