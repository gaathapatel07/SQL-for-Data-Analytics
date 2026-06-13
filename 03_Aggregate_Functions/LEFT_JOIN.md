# LEFT JOIN

## Overview

A LEFT JOIN returns all records from the left table and matching records from the right table.

If there is no match, NULL values are returned for the right table columns.

## Why It Matters

Data Analysts use LEFT JOIN to:

- Find customers without orders
- Identify missing relationships
- Perform retention analysis
- Analyze inactive users

---

## Sample Tables

### Customers

| Customer_ID | Customer_Name |
|------------|--------------|
| 1 | Rahul |
| 2 | Priya |
| 3 | Aman |
| 4 | Neha |

### Orders

| Order_ID | Customer_ID | Amount |
|----------|------------|--------|
| 101 | 1 | 500 |
| 102 | 2 | 1000 |
| 103 | 1 | 700 |

---

## Syntax

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```

---

## Example

```sql
SELECT
Customers.Customer_Name,
Orders.Order_ID
FROM Customers
LEFT JOIN Orders
ON Customers.Customer_ID = Orders.Customer_ID;
```

### Result

| Customer_Name | Order_ID |
|--------------|----------|
| Rahul | 101 |
| Rahul | 103 |
| Priya | 102 |
| Aman | NULL |
| Neha | NULL |

---

## Visual Explanation

```text
LEFT TABLE + MATCHING ROWS

All records from left table
```

---

## Business Use Case

Find customers who have never placed an order.

```sql
SELECT
c.Customer_Name
FROM Customers c
LEFT JOIN Orders o
ON c.Customer_ID = o.Customer_ID
WHERE o.Order_ID IS NULL;
```

### Result

| Customer_Name |
|--------------|
| Aman |
| Neha |

---

## Common Mistakes

### Confusing LEFT JOIN with INNER JOIN

INNER JOIN excludes non-matching rows.

LEFT JOIN includes all rows from the left table.

---

## Interview Questions

### What does LEFT JOIN return?

All rows from the left table and matching rows from the right table.

### What appears when there is no match?

NULL values.

---

## Practice Questions

1. Find customers without orders.
2. Find employees without departments.
3. Find products without sales.

---

## Key Takeaways

- LEFT JOIN keeps all rows from the left table.
- Missing matches appear as NULL.
- Useful for identifying missing relationships.
- Frequently used in customer analysis.
