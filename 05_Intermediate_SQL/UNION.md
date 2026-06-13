# UNION Operator

## Overview

The UNION operator combines results from two or more SELECT statements and removes duplicate rows.

## Syntax

```sql
SELECT column_name
FROM table1

UNION

SELECT column_name
FROM table2;
```

---

## Example

### Customers_2024

| Customer |
|----------|
| Rahul |
| Priya |

### Customers_2025

| Customer |
|----------|
| Priya |
| Aman |

```sql
SELECT Customer
FROM Customers_2024

UNION

SELECT Customer
FROM Customers_2025;
```

### Result

| Customer |
|----------|
| Rahul |
| Priya |
| Aman |

Notice that Priya appears only once.

---

## Business Use Case

Combine customer lists from multiple years while avoiding duplicates.

---

## Key Takeaways

- UNION combines query results.
- Removes duplicate rows.
- Column count and data types must match.
