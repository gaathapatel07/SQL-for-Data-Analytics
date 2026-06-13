# RIGHT JOIN

## Overview

A RIGHT JOIN returns all records from the right table and matching records from the left table.

If there is no match, NULL values are returned for the left table columns.

## Why It Matters

Data Analysts use RIGHT JOIN to:

- Identify records existing only in the right table
- Analyze unmatched transactions
- Verify data consistency
- Perform auditing and validation

---

## Sample Tables

### Customers

| Customer_ID | Customer_Name |
|------------|--------------|
| 1 | Rahul |
| 2 | Priya |
| 3 | Aman |

### Orders

| Order_ID | Customer_ID | Amount |
|----------|------------|--------|
| 101 | 1 | 500 |
| 102 | 2 | 1000 |
| 103 | 4 | 700 |

---

## Syntax

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```

---

## Example

```sql
SELECT
Customers.Customer_Name,
Orders.Order_ID,
Orders.Amount
FROM Customers
RIGHT JOIN Orders
ON Customers.Customer_ID = Orders.Customer_ID;
```

### Result

| Customer_Name | Order_ID | Amount |
|--------------|----------|--------|
| Rahul | 101 | 500 |
| Priya | 102 | 1000 |
| NULL | 103 | 700 |

---

## Visual Explanation

```text
Matching Records
+
All Rows From Right Table
```

---

## Business Use Case

Find orders that do not have a matching customer.

```sql
SELECT *
FROM Customers c
RIGHT JOIN Orders o
ON c.Customer_ID = o.Customer_ID
WHERE c.Customer_ID IS NULL;
```

---

## Common Mistakes

### Confusing LEFT JOIN and RIGHT JOIN

LEFT JOIN keeps all rows from the left table.

RIGHT JOIN keeps all rows from the right table.

---

## Interview Questions

### What does RIGHT JOIN return?

All rows from the right table and matching rows from the left table.

### When is RIGHT JOIN useful?

When the focus is on preserving all records from the right table.

---

## Practice Questions

1. Find orders without customers.
2. Find sales without products.
3. Find transactions without accounts.

---

## Key Takeaways

- RIGHT JOIN preserves all rows from the right table.
- Missing matches appear as NULL.
- Less commonly used than LEFT JOIN.
