# SUM() Function

## Overview

The SUM() function is used to calculate the total of numeric values in a column.

It is widely used in business reporting and financial analysis.

## Why It Matters

Data Analysts use SUM() to:

- Calculate revenue
- Measure sales
- Analyze profits
- Track expenses

---

## Sample Dataset

### Sales Table

| Sale_ID | Product | Revenue |
|----------|----------|---------|
| 1 | Laptop | 50000 |
| 2 | Mobile | 30000 |
| 3 | Tablet | 20000 |
| 4 | Mouse | 5000 |

---

## Syntax

```sql
SELECT SUM(column_name)
FROM table_name;
```

---

## Example

```sql
SELECT SUM(Revenue)
FROM Sales;
```

### Result

| SUM(Revenue) |
|--------------|
| 105000 |

---

## Using SUM with WHERE

Calculate revenue from Laptop sales only.

```sql
SELECT SUM(Revenue)
FROM Sales
WHERE Product = 'Laptop';
```

### Result

| SUM(Revenue) |
|--------------|
| 50000 |

---

## Business Use Case

Calculate total company revenue.

```sql
SELECT SUM(Revenue)
FROM Sales;
```

This is one of the most common KPI calculations.

---

## Visual Explanation

```text
50000
30000
20000
 5000
------
105000
```

---

## Common Mistakes

### Using SUM on Text Columns

Incorrect:

```sql
SELECT SUM(Product)
FROM Sales;
```

SUM only works with numeric data.

---

## Interview Questions

### What does SUM() do?

It calculates the total of numeric values.

### Can SUM() work with WHERE?

Yes.

```sql
SELECT SUM(Revenue)
FROM Sales
WHERE Product = 'Laptop';
```

---

## Practice Questions

1. Calculate total revenue.
2. Calculate total sales for a specific product.
3. Calculate total revenue above ₹10,000.

---

## Key Takeaways

- SUM() calculates totals.
- Works only on numeric columns.
- Frequently used in financial and sales analysis.
- Can be combined with WHERE for filtered calculations.
