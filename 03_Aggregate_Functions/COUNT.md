# COUNT() Function

## Overview

The COUNT() function is used to count the number of rows in a table or the number of non-NULL values in a column.

It is one of the most frequently used aggregate functions in SQL.

## Why It Matters

Data Analysts use COUNT() to:

- Count customers
- Count orders
- Count products
- Measure business activity
- Generate KPIs

---

## Sample Dataset

### Orders Table

| Order_ID | Customer_ID | Amount |
|----------|-------------|---------|
| 101 | 1 | 500 |
| 102 | 2 | 1000 |
| 103 | 1 | 700 |
| 104 | 3 | 1200 |

---

## Syntax

```sql
SELECT COUNT(column_name)
FROM table_name;
```

---

## Count All Rows

```sql
SELECT COUNT(*)
FROM Orders;
```

### Result

| COUNT(*) |
|-----------|
| 4 |

---

## Count Specific Column

```sql
SELECT COUNT(Customer_ID)
FROM Orders;
```

### Result

| COUNT(Customer_ID) |
|-------------------|
| 4 |

---

## Count Unique Values

```sql
SELECT COUNT(DISTINCT Customer_ID)
FROM Orders;
```

### Result

| COUNT(DISTINCT Customer_ID) |
|-----------------------------|
| 3 |

---

## Business Use Case

Find total number of orders.

```sql
SELECT COUNT(*)
FROM Orders;
```

This helps businesses measure transaction volume.

---

## Common Mistakes

### Confusing COUNT(*) and COUNT(Column)

```sql
COUNT(*)
```

Counts all rows.

```sql
COUNT(Column_Name)
```

Counts only non-NULL values.

---

## Interview Questions

### What is the difference between COUNT(*) and COUNT(column)?

COUNT(*) counts all rows.

COUNT(column) counts only non-NULL values.

### How do you count unique values?

```sql
SELECT COUNT(DISTINCT Customer_ID)
FROM Orders;
```

---

## Practice Questions

1. Count total customers.
2. Count total orders.
3. Count unique cities.

---

## Key Takeaways

- COUNT() counts records.
- COUNT(*) counts all rows.
- COUNT(column) ignores NULL values.
- COUNT(DISTINCT) counts unique values.
