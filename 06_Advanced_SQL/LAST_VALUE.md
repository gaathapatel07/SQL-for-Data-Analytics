# LAST_VALUE() Function

## Overview

LAST_VALUE() returns the last value in a window.

It is useful when comparing records against the lowest-performing or final value.

---

## Syntax

```sql
LAST_VALUE(column_name)
OVER (
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

---

## Example

```sql
SELECT
Employee,
Revenue,
LAST_VALUE(Revenue)
OVER (
    ORDER BY Revenue
    ROWS BETWEEN UNBOUNDED PRECEDING
    AND UNBOUNDED FOLLOWING
) AS Lowest_Revenue
FROM Employees;
```

---

## Business Use Case

Compare each employee against the lowest performer.

---

## Key Takeaways

- Returns the last value in a window.
- Useful for comparisons and benchmarking.
