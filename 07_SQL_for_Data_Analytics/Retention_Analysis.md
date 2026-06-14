# Retention Analysis

## Overview

Retention Analysis measures how well a business keeps its customers over time.

Customer retention is often more cost-effective than acquiring new customers.

---

## Why It Matters

Data Analysts use Retention Analysis to:

- Measure customer loyalty
- Reduce churn
- Improve user engagement
- Track long-term growth

---

## Example Question

How many customers returned after their first purchase?

---

## Example Query

```sql
SELECT
Customer_ID,
COUNT(Order_ID) AS Total_Orders
FROM Orders
GROUP BY Customer_ID;
```

Customers with multiple orders are generally considered retained customers.

---

## Business Metrics

- Retention Rate
- Repeat Purchase Rate
- Churn Rate
- Customer Lifetime Value

---

## Key Takeaways

- Retention is critical for sustainable growth.
- Repeat customers often generate higher profits.
- SQL helps measure customer loyalty.
