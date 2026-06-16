# CUME_DIST() Function

## Overview

CUME_DIST() calculates the cumulative distribution of a value within a group.

It returns the proportion of rows with values less than or equal to the current row.

---

## Syntax

```sql
CUME_DIST() OVER (
    ORDER BY column_name
)
```

---

## Example

```sql
SELECT
Employee,
Revenue,
CUME_DIST() OVER (
    ORDER BY Revenue
) AS Distribution
FROM Employees;
```

---

## Business Use Case

Determine how many customers fall below a specific spending threshold.

---

## Key Takeaways

- Measures cumulative distribution.
- Returns values between 0 and 1.
- Useful for customer segmentation.
