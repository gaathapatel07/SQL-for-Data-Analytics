# AVG() Function

## Overview

The AVG() function calculates the average value of a numeric column.

It is commonly used to analyze performance, customer behavior, sales trends, and business metrics.

## Why It Matters

Data Analysts use AVG() to:

- Calculate average sales
- Measure average order value
- Analyze average salaries
- Understand customer spending patterns

---

## Sample Dataset

### Orders Table

| Order_ID | Customer | Amount |
|----------|----------|---------|
| 101 | Rahul | 500 |
| 102 | Priya | 1000 |
| 103 | Aman | 700 |
| 104 | Neha | 800 |

---

## Syntax

```sql
SELECT AVG(column_name)
FROM table_name;
```

---

## Example

```sql
SELECT AVG(Amount)
FROM Orders;
```

### Result

| AVG(Amount) |
|-------------|
| 750 |

---

## Using AVG with WHERE

Calculate average order value above ₹500.

```sql
SELECT AVG(Amount)
FROM Orders
WHERE Amount > 500;
```

### Result

| AVG(Amount) |
|-------------|
| 833.33 |

---

## Business Use Case

Find the Average Order Value (AOV).

```sql
SELECT AVG(Amount)
FROM Orders;
```

AOV is a critical metric in e-commerce and retail analytics.

---

## Visual Explanation

```text
500
1000
700
800
----
3000 ÷ 4

Average = 750
```

---

## Common Mistakes

### Using AVG on Text Columns

Incorrect:

```sql
SELECT AVG(Customer)
FROM Orders;
```

AVG works only with numeric values.

---

## Interview Questions

### What does AVG() do?

It calculates the average value of a numeric column.

### Does AVG() ignore NULL values?

Yes.

---

## Practice Questions

1. Calculate average salary.
2. Calculate average sales.
3. Calculate average revenue above ₹1000.

---

## Key Takeaways

- AVG() calculates averages.
- Works only with numeric columns.
- Ignores NULL values.
- Frequently used in KPI analysis.
