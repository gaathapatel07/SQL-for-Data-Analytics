# CASE WHEN Statement

## Overview

The CASE statement allows conditional logic in SQL.

It works similarly to IF-ELSE statements in programming languages.

## Why It Matters

Data Analysts use CASE to:

- Categorize customers
- Create revenue segments
- Build KPI dashboards
- Generate business-friendly reports

---

## Syntax

```sql
CASE
    WHEN condition THEN result
    WHEN condition THEN result
    ELSE result
END
```

---

## Sample Dataset

### Customers

| Customer_ID | Name | Revenue |
|------------|------|---------|
| 1 | Rahul | 5000 |
| 2 | Priya | 12000 |
| 3 | Aman | 3000 |
| 4 | Neha | 15000 |

---

## Example

Classify customers.

```sql
SELECT
Name,
Revenue,
CASE
    WHEN Revenue >= 10000 THEN 'Premium'
    ELSE 'Regular'
END AS Customer_Type
FROM Customers;
```

### Result

| Name | Revenue | Customer_Type |
|------|---------|---------------|
| Rahul | 5000 | Regular |
| Priya | 12000 | Premium |
| Aman | 3000 | Regular |
| Neha | 15000 | Premium |

---

## Business Use Case

Customer segmentation is one of the most common uses of CASE statements.

---

## Key Takeaways

- CASE adds conditional logic.
- Similar to IF-ELSE.
- Frequently used in reporting and dashboards.
