# FIRST_VALUE() Function

## Overview

FIRST_VALUE() returns the first value in a window.

It is commonly used to compare current values with the best-performing value.

---

## Syntax

```sql
FIRST_VALUE(column_name)
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
FIRST_VALUE(Revenue)
OVER (
    ORDER BY Revenue DESC
) AS Highest_Revenue
FROM Employees;
```

---

## Result

| Employee | Revenue | Highest_Revenue |
|----------|---------|----------------|
| Priya | 12000 | 12000 |
| Aman | 7000 | 12000 |
| Rahul | 5000 | 12000 |

---

## Business Use Case

Compare each employee's revenue against the highest performer.

---

## Key Takeaways

- Returns the first value in a window.
- Useful for benchmarking.
