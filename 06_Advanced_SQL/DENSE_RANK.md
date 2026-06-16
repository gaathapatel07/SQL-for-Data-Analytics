# DENSE_RANK() Function

## Overview

The `DENSE_RANK()` function assigns a rank to each row based on the specified ordering.

If multiple rows have the same value, they receive the same rank.

Unlike `RANK()`, `DENSE_RANK()` does not skip rank numbers after a tie.

---

## Why It Matters

Data Analysts use DENSE_RANK() to:

* Rank customers by revenue
* Rank employees by salary
* Create leaderboards
* Identify top-performing products
* Generate business reports

---

## Syntax

```sql
DENSE_RANK() OVER (
    ORDER BY column_name
)
```

---

## Sample Dataset

### Employee_Sales

| Employee | Revenue |
| -------- | ------- |
| Rahul    | 10000   |
| Priya    | 15000   |
| Aman     | 15000   |
| Neha     | 5000    |

---

## Example

```sql
SELECT
Employee,
Revenue,
DENSE_RANK() OVER (
    ORDER BY Revenue DESC
) AS Revenue_Rank
FROM Employee_Sales;
```

### Result

| Employee | Revenue | Revenue_Rank |
| -------- | ------- | ------------ |
| Priya    | 15000   | 1            |
| Aman     | 15000   | 1            |
| Rahul    | 10000   | 2            |
| Neha     | 5000    | 3            |

---

## Visual Explanation

```text
Revenue Ranking

15000 → Rank 1
15000 → Rank 1
10000 → Rank 2
5000  → Rank 3
```

Notice there is **no missing rank number**.

---

## Difference Between ROW_NUMBER(), RANK(), and DENSE_RANK()

### ROW_NUMBER()

```text
15000 → 1
15000 → 2
10000 → 3
5000  → 4
```

Every row gets a unique number.

---

### RANK()

```text
15000 → 1
15000 → 1
10000 → 3
5000  → 4
```

Ranks are skipped after ties.

---

### DENSE_RANK()

```text
15000 → 1
15000 → 1
10000 → 2
5000  → 3
```

No ranks are skipped.

---

## Using PARTITION BY

Rank employees within each department.

```sql
SELECT
Department,
Employee,
Revenue,
DENSE_RANK() OVER (
    PARTITION BY Department
    ORDER BY Revenue DESC
) AS Department_Rank
FROM Employee_Sales;
```

---

## Business Use Case

Find the top-performing employees within each department.

```sql
SELECT
Department,
Employee,
Revenue,
DENSE_RANK() OVER (
    PARTITION BY Department
    ORDER BY Revenue DESC
) AS Department_Rank
FROM Employee_Sales;
```

This is commonly used in performance analysis and reporting dashboards.

---

## Common Mistakes

### Confusing DENSE_RANK with RANK

Many beginners assume both functions work the same way.

Remember:

* RANK() skips numbers after ties.
* DENSE_RANK() does not skip numbers.

---

## Interview Questions

### What does DENSE_RANK() do?

It assigns rankings without gaps.

### Difference between RANK() and DENSE_RANK()?

RANK() skips numbers after ties.

DENSE_RANK() continues ranking without gaps.

### When should DENSE_RANK() be used?

When continuous ranking is required.

---

## Practice Questions

1. Rank employees by salary using DENSE_RANK().
2. Rank customers by revenue.
3. Rank products by sales within categories.
4. Compare RANK() and DENSE_RANK() outputs.

---

## Key Takeaways

* DENSE_RANK() assigns rankings without gaps.
* Equal values receive the same rank.
* Useful for leaderboards and business reporting.
* Frequently asked in SQL interviews.

