# IS NULL Operator

## Overview

NULL represents missing or unknown values in a database.

The IS NULL operator is used to find rows where a column contains NULL values.

## Why It Matters

Data Analysts use IS NULL to:

- Detect missing data
- Clean datasets
- Validate records
- Improve data quality

---

## Sample Dataset

### Employees Table

| Employee_ID | Name | Email |
|------------|------|--------|
| 1 | Rahul | rahul@gmail.com |
| 2 | Priya | NULL |
| 3 | Aman | aman@gmail.com |
| 4 | Neha | NULL |

---

## Syntax

```sql
SELECT *
FROM table_name
WHERE column_name IS NULL;
```

---

## Example

```sql
SELECT *
FROM Employees
WHERE Email IS NULL;
```

### Result

| Employee_ID | Name |
|------------|------|
| 2 | Priya |
| 4 | Neha |

---

## IS NOT NULL

Find records where values exist.

```sql
SELECT *
FROM Employees
WHERE Email IS NOT NULL;
```

---

## Business Use Case

Identify customers who have not provided an email address.

```sql
SELECT *
FROM Customers
WHERE Email IS NULL;
```

This helps businesses improve customer records.

---

## Common Mistakes

Incorrect:

```sql
SELECT *
FROM Employees
WHERE Email = NULL;
```

Correct:

```sql
SELECT *
FROM Employees
WHERE Email IS NULL;
```

---

## Interview Questions

### What is NULL?

A missing or unknown value.

### Why can't we use = NULL?

Because NULL must be checked using IS NULL or IS NOT NULL.

---

## Practice Questions

1. Find customers with missing phone numbers.
2. Find employees without email addresses.
3. Find records where address is NULL.

---

## Key Takeaways

- NULL represents missing data.
- Use IS NULL to find missing values.
- Use IS NOT NULL to find existing values.
- Important for data cleaning and quality checks.
