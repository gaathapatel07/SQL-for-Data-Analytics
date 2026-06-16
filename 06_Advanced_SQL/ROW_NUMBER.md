# ROW_NUMBER() Function

## Overview

The `ROW_NUMBER()` function is a Window Function that assigns a unique sequential number to each row in a result set.

The numbering starts from 1 and increases by 1 for every row.

Unlike `RANK()` and `DENSE_RANK()`, `ROW_NUMBER()` never assigns the same number to multiple rows.

---

## Why It Matters

Data Analysts use ROW_NUMBER() to:

* Rank records uniquely
* Find top-performing customers
* Remove duplicate records
* Identify first or last transactions
* Build reporting dashboards

---

## Syntax

```sql
ROW_NUMBER() OVER (
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
ROW_NUMBER() OVER (
    ORDER BY Revenue DESC
) AS Row_Num
FROM Employee_Sales;
```

### Result

| Employee | Revenue | Row_Num |
| -------- | ------- | ------- |
| Priya    | 15000   | 1       |
| Aman     | 15000   | 2       |
| Rahul    | 10000   | 3       |
| Neha     | 5000    | 4       |

---

## Visual Explanation

```text
Revenue Ranking

15000 → 1
15000 → 2
10000 → 3
5000  → 4
```

Even though Priya and Aman have the same revenue, they receive different row numbers.

---

## Using PARTITION BY

Assign row numbers within each department.

```sql
SELECT
Department,
Employee,
Revenue,
ROW_NUMBER() OVER (
    PARTITION BY Department
    ORDER BY Revenue DESC
) AS Department_Row_Number
FROM Employee_Sales;
```

### Example Output

Sales Department

| Employee | Row Number |
| -------- | ---------- |
| Priya    | 1          |
| Rahul    | 2          |

Marketing Department

| Employee | Row Number |
| -------- | ---------- |
| Neha     | 1          |
| Aman     | 2          |

---

## Finding Top Records

Find the highest revenue employee.

```sql
WITH RankedEmployees AS
(
    SELECT
    Employee,
    Revenue,
    ROW_NUMBER() OVER (
        ORDER BY Revenue DESC
    ) AS Row_Num
    FROM Employee_Sales
)
SELECT *
FROM RankedEmployees
WHERE Row_Num = 1;
```

---

## Removing Duplicate Records

A common interview question.

```sql
WITH DuplicateCheck AS
(
    SELECT *,
    ROW_NUMBER() OVER (
        PARTITION BY Customer_ID
        ORDER BY Order_Date
    ) AS Row_Num
    FROM Orders
)
SELECT *
FROM DuplicateCheck
WHERE Row_Num = 1;
```

This keeps only the first occurrence.

---

## ROW_NUMBER vs RANK vs DENSE_RANK

### ROW_NUMBER()

```text
15000 → 1
15000 → 2
10000 → 3
5000  → 4
```

Unique numbering.

---

### RANK()

```text
15000 → 1
15000 → 1
10000 → 3
5000  → 4
```

Ranking gaps exist.

---

### DENSE_RANK()

```text
15000 → 1
15000 → 1
10000 → 2
5000  → 3
```

No ranking gaps.

---

## Business Use Cases

### Top N Customers

```sql
SELECT
Customer_ID,
Revenue,
ROW_NUMBER() OVER (
    ORDER BY Revenue DESC
) AS Customer_Rank
FROM Customers;
```

### First Order Per Customer

```sql
SELECT
Customer_ID,
Order_Date,
ROW_NUMBER() OVER (
    PARTITION BY Customer_ID
    ORDER BY Order_Date
) AS Order_Number
FROM Orders;
```

---

## Common Mistakes

### Assuming ROW_NUMBER Handles Ties

Incorrect assumption:

Two rows with the same value get the same rank.

Actual behavior:

Each row receives a unique number.

---

## Interview Questions

### What does ROW_NUMBER() do?

Assigns a unique sequential number to each row.

### Can two rows have the same ROW_NUMBER?

No.

### What is PARTITION BY used for?

To restart numbering within groups.

### Difference between ROW_NUMBER and RANK?

ROW_NUMBER always assigns unique numbers.

RANK allows ties.

---

## Practice Questions

1. Rank employees by salary.
2. Find top 5 customers by revenue.
3. Find first order of every customer.
4. Remove duplicate records using ROW_NUMBER().

---

## Key Takeaways

* ROW_NUMBER() assigns unique sequential numbers.
* No duplicate rankings are allowed.
* Useful for ranking and deduplication.
* Frequently asked in SQL interviews.
* One of the most important Window Functions.

