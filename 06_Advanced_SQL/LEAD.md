# LEAD() Function

## Overview

The `LEAD()` function is a Window Function that allows you to access data from the next row without using a self join.

It is commonly used for forecasting, trend analysis, and period-over-period comparisons.

---

## Why It Matters

Data Analysts use LEAD() to:

* Compare current sales with future sales
* Analyze customer behavior
* Forecast trends
* Measure future growth
* Build analytical dashboards

---

## Syntax

```sql id="kz4qj2"
LEAD(column_name, offset)
OVER (
    ORDER BY column_name
)
```

### Parameters

| Parameter   | Description          |
| ----------- | -------------------- |
| column_name | Column to retrieve   |
| offset      | Number of rows ahead |
| ORDER BY    | Defines row order    |

---

## Sample Dataset

### Monthly Sales

| Month | Revenue |
| ----- | ------- |
| Jan   | 1000    |
| Feb   | 1500    |
| Mar   | 1800    |
| Apr   | 2200    |

---

## Example

Retrieve next month's revenue.

```sql id="9c7n9k"
SELECT
Month,
Revenue,
LEAD(Revenue, 1)
OVER (
    ORDER BY Month
) AS Next_Revenue
FROM Sales;
```

### Result

| Month | Revenue | Next_Revenue |
| ----- | ------- | ------------ |
| Jan   | 1000    | 1500         |
| Feb   | 1500    | 1800         |
| Mar   | 1800    | 2200         |
| Apr   | 2200    | NULL         |

---

## Visual Explanation

```text id="pgv4o7"
Jan → 1000 → Next = 1500
Feb → 1500 → Next = 1800
Mar → 1800 → Next = 2200
Apr → 2200 → Next = NULL
```

---

## Calculating Future Difference

```sql id="6zq7hi"
SELECT
Month,
Revenue,
LEAD(Revenue)
OVER (
    ORDER BY Month
) - Revenue AS Future_Difference
FROM Sales;
```

### Result

| Month | Revenue | Future_Difference |
| ----- | ------- | ----------------- |
| Jan   | 1000    | 500               |
| Feb   | 1500    | 300               |
| Mar   | 1800    | 400               |
| Apr   | 2200    | NULL              |

---

## Using PARTITION BY

Compare future revenue within departments.

```sql id="jhtv7l"
SELECT
Department,
Employee,
Revenue,
LEAD(Revenue)
OVER (
    PARTITION BY Department
    ORDER BY Revenue
) AS Next_Revenue
FROM Employee_Sales;
```

---

## LEAD vs LAG

### LAG()

Gets previous row.

```text id="5br1c0"
Current Row ← Previous Row
```

### LEAD()

Gets next row.

```text id="cax3d9"
Current Row → Next Row
```

---

## Business Use Cases

### Compare Current Month with Next Month

```sql id="u2dl2k"
SELECT
Month,
Revenue,
LEAD(Revenue)
OVER (
    ORDER BY Month
) AS Next_Month_Revenue
FROM Sales;
```

---

### Forecast Revenue Trends

```sql id="fczxv2"
SELECT
Month,
Revenue,
LEAD(Revenue)
OVER (
    ORDER BY Month
) - Revenue AS Expected_Growth
FROM Sales;
```

---

## Common Mistakes

### Forgetting ORDER BY

Incorrect:

```sql id="tr3r1e"
LEAD(Revenue)
OVER ()
```

Correct:

```sql id="qvq0gq"
LEAD(Revenue)
OVER (
    ORDER BY Month
)
```

---

## Interview Questions

### What does LEAD() do?

Returns data from a future row.

### What is the default offset?

1

```sql id="gcgc6r"
LEAD(Revenue)
```

is equivalent to:

```sql id="90p1g7"
LEAD(Revenue, 1)
```

### Difference between LEAD() and LAG()?

LAG gets previous row values.

LEAD gets next row values.

### Why use LEAD()?

To compare current records with future records without using self joins.

---

## Practice Questions

1. Compare monthly sales with next month's sales.
2. Calculate future revenue growth.
3. Analyze employee performance trends.
4. Compare customer purchases with future purchases.

---

## Key Takeaways

* LEAD() accesses future row values.
* Useful for forecasting and trend analysis.
* Commonly paired with LAG().
* Eliminates the need for self joins.
* Frequently asked in SQL interviews.

