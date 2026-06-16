# NTILE() Function

## Overview

NTILE() divides rows into a specified number of groups.

It is useful for customer segmentation and performance analysis.

---

## Syntax

```sql
NTILE(number_of_groups)
OVER (
    ORDER BY column_name
)
```

---

## Sample Dataset

| Customer | Revenue |
|----------|---------|
| A | 1000 |
| B | 2000 |
| C | 3000 |
| D | 4000 |
| E | 5000 |
| F | 6000 |

---

## Example

Divide customers into 3 groups.

```sql
SELECT
Customer,
Revenue,
NTILE(3) OVER
(
    ORDER BY Revenue DESC
) AS Revenue_Group
FROM Customers;
```

---

## Business Use Case

Segment customers into Top, Medium, and Low spenders.

---

## Key Takeaways

- Divides rows into groups.
- Useful for customer segmentation.
- Common in analytics projects.
