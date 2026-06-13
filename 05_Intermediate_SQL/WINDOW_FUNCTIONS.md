# Window Functions

## Overview

Window Functions perform calculations across a set of rows related to the current row without grouping the result.

Unlike GROUP BY, window functions preserve individual rows.

## Why It Matters

Data Analysts use window functions to:

- Rank customers
- Calculate running totals
- Compare rows
- Analyze trends over time

---

## Syntax

```sql
SELECT
column_name,
window_function()
OVER (
    PARTITION BY column_name
    ORDER BY column_name
)
FROM table_name;
```

---

## Sample Dataset

### Sales

| Employee | Revenue |
|-----------|----------|
| Rahul | 5000 |
| Priya | 12000 |
| Aman | 7000 |
| Neha | 15000 |

---

## Example: Ranking Employees

```sql
SELECT
Employee,
Revenue,
RANK() OVER
(
    ORDER BY Revenue DESC
) AS Rank_Number
FROM Sales;
```

### Result

| Employee | Revenue | Rank_Number |
|-----------|----------|-------------|
| Neha | 15000 | 1 |
| Priya | 12000 | 2 |
| Aman | 7000 | 3 |
| Rahul | 5000 | 4 |

---

## Visual Explanation

```text
Revenue Ranking

15000 → Rank 1
12000 → Rank 2
7000  → Rank 3
5000  → Rank 4
```

---

## Common Window Functions

### ROW_NUMBER()

Assigns unique numbers.

```sql
SELECT
ROW_NUMBER() OVER
(
    ORDER BY Revenue DESC
)
FROM Sales;
```

---

### RANK()

Assigns ranks with gaps.

```sql
SELECT
RANK() OVER
(
    ORDER BY Revenue DESC
)
FROM Sales;
```

---

### DENSE_RANK()

Assigns ranks without gaps.

```sql
SELECT
DENSE_RANK() OVER
(
    ORDER BY Revenue DESC
)
FROM Sales;
```

---

## Business Use Case

Find the top 5 customers by revenue.

```sql
SELECT
Customer_Name,
Revenue,
RANK() OVER
(
    ORDER BY Revenue DESC
) AS Revenue_Rank
FROM Customers;
```

---

## Interview Questions

### What is a Window Function?

A function that performs calculations across related rows while keeping individual rows.

### Difference between GROUP BY and Window Functions?

GROUP BY collapses rows.

Window Functions preserve rows.

---

## Practice Questions

1. Rank employees by salary.
2. Rank customers by revenue.
3. Compare ROW_NUMBER and RANK.

---

## Key Takeaways

- Window Functions preserve rows.
- Useful for ranking and trend analysis.
- Frequently used in Data Analyst interviews.
- Considered an advanced SQL topic.
