# INNER JOIN

## Overview

An INNER JOIN returns only the rows that have matching values in both tables.

If a record exists in one table but not in the other, it is excluded from the result.

## Why It Matters

Data Analysts use INNER JOIN to:

- Combine customer and order data
- Merge product and sales information
- Analyze relationships between tables
- Generate business reports

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
|----------|------------|---------|
| 101 | 1 | 500 |
| 102 | 2 | 1000 |
| 103 | 1 | 700 |

---

## Syntax

```sql
SELECT columns
FROM table1
INNER JOIN table2
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
INNER JOIN Orders
ON Customers.Customer_ID = Orders.Customer_ID;
```

### Result

| Customer_Name | Order_ID | Amount |
|--------------|----------|--------|
| Rahul | 101 | 500 |
| Priya | 102 | 1000 |
| Rahul | 103 | 700 |

---

## Visual Explanation

```text
Customers ∩ Orders

Only matching records
```

---

## Business Use Case

Find customer names along with their orders.

```sql
SELECT
c.Customer_Name,
o.Order_ID,
o.Amount
FROM Customers c
INNER JOIN Orders o
ON c.Customer_ID = o.Customer_ID;
```

---

## Common Mistakes

### Missing ON Clause

Incorrect:

```sql
SELECT *
FROM Customers
INNER JOIN Orders;
```

Correct:

```sql
SELECT *
FROM Customers
INNER JOIN Orders
ON Customers.Customer_ID = Orders.Customer_ID;
```

---

## Interview Questions

### What does INNER JOIN return?

Only matching rows from both tables.

### What happens if there is no match?

The row is excluded.

---

## Practice Questions

1. Join Employees and Departments tables.
2. Display customer names with order amounts.
3. Display products with sales information.

---

## Key Takeaways

- INNER JOIN returns matching records.
- Non-matching records are excluded.
- Most commonly used SQL join.
