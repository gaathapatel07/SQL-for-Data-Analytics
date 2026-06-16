# PERCENT_RANK() Function

## Overview

PERCENT_RANK() calculates the relative rank of a row within a partition.

The result ranges from 0 to 1.

It helps analysts understand where a value stands relative to the rest of the dataset.

---

## Syntax

```sql
PERCENT_RANK() OVER (
    ORDER BY column_name
)
```

---

## Sample Dataset

| Employee | Revenue |
|----------|---------|
| Rahul | 5000 |
| Priya | 12000 |
| Aman | 7000 |
| Neha | 15000 |

---

## Example

```sql
SELECT
Employee,
Revenue,
PERCENT_RANK() OVER (
    ORDER BY Revenue
) AS Revenue_Percentile
FROM Employees;
```

---

## Business Use Case

Identify top-performing customers based on percentile rankings.

---

## Key Takeaways

- Returns values between 0 and 1.
- Useful for percentile analysis.
- Commonly used in reporting.
