# HAVING Clause

## Overview

The HAVING clause is used to filter grouped data after the GROUP BY operation.

While WHERE filters rows before grouping, HAVING filters groups after aggregation.

## Why It Matters

Data Analysts use HAVING to:

- Find high-revenue cities
- Identify top-performing products
- Analyze profitable regions
- Create KPI reports

---

## Sample Dataset

### Orders Table

| Order_ID | City | Revenue |
|----------|------|----------|
| 101 | Mumbai | 500 |
| 102 | Delhi | 1000 |
| 103 | Mumbai | 700 |
| 104 | Delhi | 800 |

---

## Syntax

```sql
SELECT column_name,
       aggregate_function(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

---

## Example

Find cities generating more than ₹1500 revenue.

```sql
SELECT City,
       SUM(Revenue) AS Total_Revenue
FROM Orders
GROUP BY City
HAVING SUM(Revenue) > 1500;
```

### Result

| City | Total_Revenue |
|------|--------------|
| Delhi | 1800 |

---

## WHERE vs HAVING

### WHERE

Filters rows before grouping.

```sql
SELECT *
FROM Orders
WHERE Revenue > 500;
```

### HAVING

Filters groups after grouping.

```sql
SELECT City,
       SUM(Revenue)
FROM Orders
GROUP BY City
HAVING SUM(Revenue) > 1500;
```

---

## Business Use Case

Find cities generating significant revenue.

```sql
SELECT City,
       SUM(Revenue) AS Total_Revenue
FROM Orders
GROUP BY City
HAVING SUM(Revenue) > 10000;
```

This helps identify high-performing markets.

---

## Common Mistakes

### Using Aggregate Functions in WHERE

Incorrect:

```sql
SELECT City,
       SUM(Revenue)
FROM Orders
WHERE SUM(Revenue) > 1500
GROUP BY City;
```

Correct:

```sql
SELECT City,
       SUM(Revenue)
FROM Orders
GROUP BY City
HAVING SUM(Revenue) > 1500;
```

---

## Interview Questions

### What is the difference between WHERE and HAVING?

WHERE filters rows.

HAVING filters grouped results.

### Can HAVING be used without GROUP BY?

Yes, but it is typically used with GROUP BY.

---

## Practice Questions

1. Find cities with revenue above ₹1000.
2. Find products with sales above 50 units.
3. Find departments with average salary above ₹60,000.

---

## Key Takeaways

- HAVING filters grouped data.
- Used after GROUP BY.
- Frequently used with aggregate functions.
- Essential for business reporting.
