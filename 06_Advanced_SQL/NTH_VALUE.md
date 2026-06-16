# NTH_VALUE() Function

## Overview

NTH_VALUE() returns the value from a specified row position within a window.

It allows analysts to access the nth record in an ordered set.

---

## Syntax

```sql
NTH_VALUE(column_name, n)
OVER (
    ORDER BY column_name
)
```

---

## Example

```sql
SELECT
Employee,
Revenue,
NTH_VALUE(Revenue, 2)
OVER (
    ORDER BY Revenue DESC
) AS Second_Highest_Revenue
FROM Employees;
```

---

## Business Use Case

Find benchmark values such as second-highest revenue or third-highest sales.

---

## Key Takeaways

- Returns value from a specified position.
- Useful for benchmarking.
- Less commonly used than ROW_NUMBER or RANK.
