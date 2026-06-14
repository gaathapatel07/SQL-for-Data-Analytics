# Funnel Analysis

## Overview

Funnel Analysis tracks how users move through different stages of a process.

It helps identify where users drop off.

---

## Example Funnel

```text
Visit Website
      ↓
Create Account
      ↓
Add Product to Cart
      ↓
Purchase
```

---

## Why It Matters

Data Analysts use Funnel Analysis to:

- Improve conversion rates
- Identify bottlenecks
- Optimize user journeys
- Increase revenue

---

## Example Dataset

| User_ID | Stage |
|----------|--------|
| 1 | Visit |
| 1 | Signup |
| 1 | Purchase |
| 2 | Visit |

---

## Example Query

```sql
SELECT
Stage,
COUNT(DISTINCT User_ID) AS Users
FROM Funnel
GROUP BY Stage;
```

---

## Business Questions

1. How many users reach each stage?
2. Where do users drop off?
3. Which stage needs optimization?

---

## Key Takeaways

- Funnel Analysis measures conversion.
- Helps identify drop-off points.
- Widely used in product and marketing analytics.
