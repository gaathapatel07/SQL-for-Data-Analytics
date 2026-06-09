# AND Operator

## Overview

The AND operator is used to combine multiple conditions in a WHERE clause.

A row is returned only if all conditions evaluate to TRUE.

## Why It Matters

Data Analysts use AND to:

- Filter customers from a specific city and age group
- Identify high-value orders
- Segment users based on multiple criteria
- Create precise business reports

---

## Sample Dataset

### Customers Table

| Customer_ID | Name | City | Age |
|------------|------|------|-----|
| 1 | Rahul | Mumbai | 22 |
| 2 | Priya | Delhi | 25 |
| 3 | Aman | Mumbai | 28 |
| 4 | Neha | Pune | 24 |

---

## Syntax

```sql
SELECT column_name
FROM table_name
WHERE condition1 AND condition2;
```

---

## Example

Find customers from Mumbai who are older than 25.

```sql
SELECT *
FROM Customers
WHERE City = 'Mumbai'
AND Age > 25;
```

### Result

| Customer_ID | Name | City | Age |
|------------|------|------|-----|
| 3 | Aman | Mumbai | 28 |

---

## Visual Explanation

```text
City = Mumbai
      AND
Age > 25

↓

Only rows satisfying BOTH conditions
```

---

## Business Use Case

Find premium customers.

```sql
SELECT *
FROM Customers
WHERE City = 'Mumbai'
AND Age >= 25;
```

This helps businesses target specific customer segments.

---

## Common Mistakes

### Using OR instead of AND

Incorrect:

```sql
SELECT *
FROM Customers
WHERE City = 'Mumbai'
OR Age > 25;
```

This returns more rows than expected.

---

## Interview Questions

### What does AND do?

AND returns rows only when all conditions are TRUE.

### Can AND combine more than two conditions?

Yes.

```sql
SELECT *
FROM Customers
WHERE City = 'Mumbai'
AND Age > 20
AND Customer_ID > 1;
```

---

## Practice Questions

1. Display customers from Delhi who are older than 20.
2. Display customers from Mumbai who are younger than 30.
3. Display customers from Pune who are older than 23.

---

## Key Takeaways

- AND combines multiple conditions.
- Every condition must be TRUE.
- Frequently used in business filtering.
