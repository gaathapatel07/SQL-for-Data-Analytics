# RANK() Function

## Overview

The `RANK()` function is a Window Function that assigns a rank to each row based on a specified order.

If two or more rows have the same value, they receive the same rank.

Unlike `ROW_NUMBER()`, RANK() allows ties. Unlike `DENSE_RANK()`, it leaves gaps in ranking after ties.

---

## Why It Matters

Data Analysts use RANK() to:

* Rank customers by revenue
* Rank employees by salary
* Build leaderboards
* Identify top-performing products
* Analyze business performance

---

## Syntax

```sql id="6k4l3r"
RANK() OVER (
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

```sql id="6yjlwm"
SELECT
Employee,
Revenue,
RANK() OVER (
    ORDER BY Revenue DESC
) AS Revenue_Rank
FROM Employee_Sales;
```

### Result

| Employee | Revenue | Revenue_Rank |
| -------- | ------- | ------------ |
| Priya    | 15000   | 1            |
| Aman     | 15000   | 1            |
| Rahul    | 10000   | 3            |
| Neha     | 5000    | 4            |

---

## Visual Explanation

```text id="s5sx0l"
Revenue Ranking

15000 → Rank 1
15000 → Rank 1
10000 → Rank 3
5000  → Rank 4
```

Notice that Rank 2 is skipped because two employees share Rank 1.

---

## Difference Between ROW_NUMBER(), RANK(), and DENSE_RANK()

### ROW_NUMBER()

```text id="c1pp5m"
15000 → 1
15000 → 2
10000 → 3
5000  → 4
```

Every row gets a unique number.

---

### RANK()

```text id="xbg7ar"
15000 → 1
15000 → 1
10000 → 3
5000  → 4
```

Ranks are skipped after ties.

---

### DENSE_RANK()

```text id="bz9txc"
15000 → 1
15000 → 1
10000 → 2
5000  → 3
```

No ranks are skipped.

---

## Using PARTITION BY

Rank employees within each department.

```sql id="mxrj6h"
SELECT
Department,
Employee,
Revenue,
RANK() OVER (
    PARTITION BY Department
    ORDER BY Revenue DESC
) AS Department_Rank
FROM Employee_Sales;
```

---

## Business Use Case

Find the top-selling products in each category.

```sql id="ah4f4z"
SELECT
Category,
Product_Name,
Revenue,
RANK() OVER (
    PARTITION BY Category
    ORDER BY Revenue DESC
) AS Product_Rank
FROM Products;
```

---

## Common Mistakes

### Confusing RANK with ROW_NUMBER

ROW_NUMBER always gives unique numbers.

RANK allows ties.

---

### Confusing RANK with DENSE_RANK

RANK skips numbers after ties.

DENSE_RANK does not skip numbers.

---

## Interview Questions

### What does RANK() do?

Assigns rankings based on sorting order.

### What happens when values are tied?

Rows receive the same rank.

### Why are ranks skipped?

Because RANK leaves gaps after ties.

### Difference between RANK() and DENSE_RANK()?

RANK skips numbers after ties.

DENSE_RANK continues ranking without gaps.

---

## Practice Questions

1. Rank employees by salary.
2. Rank products by sales.
3. Find the top 3 customers by revenue.
4. Compare ROW_NUMBER, RANK, and DENSE_RANK outputs.

---

## Key Takeaways

* RANK() assigns rankings based on sorting.
* Equal values receive the same rank.
* Ranking gaps occur after ties.
* Frequently used in business reporting.
* Common SQL interview topic.

