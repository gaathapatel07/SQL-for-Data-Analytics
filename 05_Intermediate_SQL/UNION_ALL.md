# UNION ALL Operator

## Overview

The UNION ALL operator combines the results of two or more SELECT statements.

Unlike UNION, it does not remove duplicate rows.

## Why It Matters

Data Analysts use UNION ALL to:

- Combine datasets quickly
- Preserve transaction records
- Merge sales data from multiple sources
- Improve query performance

---

## Syntax

```sql
SELECT column_name
FROM table1

UNION ALL

SELECT column_name
FROM table2;
```

---

## Sample Dataset

### Customers_2024

| Customer |
|----------|
| Rahul |
| Priya |

### Customers_2025

| Customer |
|----------|
| Priya |
| Aman |

---

## Example

```sql
SELECT Customer
FROM Customers_2024

UNION ALL

SELECT Customer
FROM Customers_2025;
```

### Result

| Customer |
|----------|
| Rahul |
| Priya |
| Priya |
| Aman |

Notice that Priya appears twice.

---

## UNION vs UNION ALL

### UNION

Removes duplicates.

```sql
SELECT Customer
FROM Customers_2024

UNION

SELECT Customer
FROM Customers_2025;
```

Result:

| Customer |
|----------|
| Rahul |
| Priya |
| Aman |

---

### UNION ALL

Keeps duplicates.

```sql
SELECT Customer
FROM Customers_2024

UNION ALL

SELECT Customer
FROM Customers_2025;
```

Result:

| Customer |
|----------|
| Rahul |
| Priya |
| Priya |
| Aman |

---

## Business Use Case

Combine sales records from multiple stores while keeping all transactions.

```sql
SELECT *
FROM Store_A_Sales

UNION ALL

SELECT *
FROM Store_B_Sales;
```

---

## Interview Questions

### What is the difference between UNION and UNION ALL?

UNION removes duplicates.

UNION ALL keeps duplicates.

### Which is faster?

UNION ALL is generally faster because it does not perform duplicate removal.

---

## Practice Questions

1. Combine customer records from two years.
2. Merge sales data from two branches.
3. Compare UNION and UNION ALL outputs.

---

## Key Takeaways

- UNION ALL combines query results.
- Duplicate rows are preserved.
- Usually faster than UNION.
- Commonly used for transaction data.
