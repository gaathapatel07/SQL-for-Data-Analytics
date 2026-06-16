# Window Functions

## Overview

Window Functions perform calculations across a set of table rows related to the current row.

Unlike GROUP BY, Window Functions do not collapse rows. Every row remains visible while calculations are performed.

Window Functions are heavily used in Data Analytics, Business Intelligence, and SQL Interviews.

---

## Why Window Functions Matter

Data Analysts use Window Functions to:

* Rank customers
* Rank employees
* Calculate running totals
* Compare current values with previous values
* Analyze trends
* Build dashboards

---

## General Syntax

```sql
FUNCTION_NAME()
OVER (
    PARTITION BY column_name
    ORDER BY column_name
)
```

---

## Sample Dataset

### Employee_Sales

| Employee | Department | Revenue |
| -------- | ---------- | ------- |
| Rahul    | Sales      | 10000   |
| Priya    | Sales      | 15000   |
| Aman     | Marketing  | 8000    |
| Neha     | Marketing  | 12000   |

---

## Example: Ranking Employees

```sql
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
| Neha     | 12000   | 2            |
| Rahul    | 10000   | 3            |
| Aman     | 8000    | 4            |

---

## PARTITION BY

PARTITION BY creates separate groups.

```sql
SELECT
Employee,
Department,
Revenue,
RANK() OVER (
    PARTITION BY Department
    ORDER BY Revenue DESC
) AS Department_Rank
FROM Employee_Sales;
```

### Result

Sales Department

| Employee | Rank |
| -------- | ---- |
| Priya    | 1    |
| Rahul    | 2    |

Marketing Department

| Employee | Rank |
| -------- | ---- |
| Neha     | 1    |
| Aman     | 2    |

---

## Common Window Functions

| Function      | Purpose                 |
| ------------- | ----------------------- |
| ROW_NUMBER()  | Unique ranking          |
| RANK()        | Ranking with gaps       |
| DENSE_RANK()  | Ranking without gaps    |
| LAG()         | Previous row            |
| LEAD()        | Next row                |
| NTILE()       | Divide rows into groups |
| FIRST_VALUE() | First value             |
| LAST_VALUE()  | Last value              |

---

## Window Functions vs GROUP BY

### GROUP BY

```sql
SELECT Department,
SUM(Revenue)
FROM Employee_Sales
GROUP BY Department;
```

Result:

| Department | Revenue |
| ---------- | ------- |
| Sales      | 25000   |
| Marketing  | 20000   |

Rows are collapsed.

---

### Window Function

```sql
SELECT
Employee,
Department,
Revenue,
SUM(Revenue) OVER (
PARTITION BY Department
) AS Department_Total
FROM Employee_Sales;
```

Result:

| Employee | Revenue | Department_Total |
| -------- | ------- | ---------------- |
| Rahul    | 10000   | 25000            |
| Priya    | 15000   | 25000            |
| Aman     | 8000    | 20000            |
| Neha     | 12000   | 20000            |

Rows remain visible.

---

## Interview Questions

### What is a Window Function?

A function that performs calculations across related rows while keeping individual rows visible.

### Difference between GROUP BY and Window Functions?

GROUP BY collapses rows.

Window Functions preserve rows.

### What is PARTITION BY?

It divides data into groups before calculations are performed.

---

## Key Takeaways

* Window Functions preserve rows.
* Used for ranking and trend analysis.
* Essential for Data Analysts.
* Frequently asked in SQL interviews.

