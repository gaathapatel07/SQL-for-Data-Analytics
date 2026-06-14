# Customer Segmentation

## Overview

Customer Segmentation divides customers into groups based on behavior, spending, demographics, or activity.

It helps businesses target customers more effectively.

---

## Why It Matters

Data Analysts use Customer Segmentation to:

- Improve marketing campaigns
- Increase customer retention
- Identify premium customers
- Personalize experiences

---

## Sample Dataset

| Customer_ID | Revenue |
|-------------|---------|
| 1 | 3000 |
| 2 | 12000 |
| 3 | 8000 |
| 4 | 15000 |

---

## Example

Classify customers based on spending.

```sql
SELECT
Customer_ID,
Revenue,
CASE
    WHEN Revenue >= 10000 THEN 'Premium'
    WHEN Revenue >= 5000 THEN 'Regular'
    ELSE 'Basic'
END AS Customer_Type
FROM Customers;
```

---

## Business Questions

1. Who are premium customers?
2. Which segment generates the most revenue?
3. How many customers belong to each segment?

---

## Key Takeaways

- Segmentation improves decision-making.
- CASE statements are commonly used.
- Premium customers often generate most revenue.
