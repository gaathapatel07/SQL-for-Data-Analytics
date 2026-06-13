# FULL JOIN

## Overview

A FULL JOIN returns all records from both tables.

Matching records are combined, while non-matching records from either table are also included.

## Why It Matters

Data Analysts use FULL JOIN to:

- Compare datasets
- Detect missing records
- Audit data integrity
- Analyze complete relationships

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
FULL JOIN table2
ON table1.column = table2.column;
```

---

## Example

```sql
SELECT
Customers.Customer_Name,
Orders.Order_ID
FROM Customers
FULL JOIN Orders
ON Customers.Customer_ID = Orders.Customer_ID;
```

### Result

| Customer_Name | Order_ID |
|--------------|----------|
| Rahul | 101 |
| Priya | 102 |
| Aman | NULL |
| NULL | 103 |

---

## Visual Explanation

```text
All Records From Left Table
+
All Records From Right Table
```

---

## Business Use Case

Compare customer records and order records to identify missing matches.

```sql
SELECT *
FROM Customers c
FULL JOIN Orders o
ON c.Customer_ID = o.Customer_ID;
```

---

## Common Mistakes

### Assuming FULL JOIN Exists Everywhere

Some databases such as MySQL do not support FULL JOIN directly.

Alternative solutions use UNION.

---

## Interview Questions

### What does FULL JOIN return?

All records from both tables.

### What happens when there is no match?

NULL values are returned for missing columns.

---

## Practice Questions

1. Compare two customer lists.
2. Find unmatched records across tables.
3. Analyze missing relationships.

---

## Key Takeaways

- FULL JOIN returns all records from both tables.
- Useful for auditing and comparison.
- Includes matching and non-matching rows.
