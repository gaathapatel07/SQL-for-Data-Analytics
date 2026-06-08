
# DISTINCT Keyword

## Overview

The `DISTINCT` keyword is used to remove duplicate values from query results.

It returns only unique records.

## Why It Matters

Data Analysts use DISTINCT to:

- Count unique customers
- Identify unique cities
- Analyze unique products
- Remove duplicate values from reports

---

## Sample Dataset

### Customers Table

| Customer_ID | Name | City |
|------------|------|------|
| 1 | Rahul | Mumbai |
| 2 | Priya | Delhi |
| 3 | Aman | Mumbai |
| 4 | Neha | Pune |

---

## Basic Syntax

```sql
SELECT DISTINCT column_name
FROM table_name;
```

---

## Example

```sql
SELECT DISTINCT City
FROM Customers;
```

### Result

| City |
|------|
| Mumbai |
| Delhi |
| Pune |

Notice that Mumbai appears only once.

---

## DISTINCT on Multiple Columns

```sql
SELECT DISTINCT City, Name
FROM Customers;
```

SQL checks the combination of both columns for uniqueness.

---

## Visual Explanation

Without DISTINCT:

```text
Mumbai
Delhi
Mumbai
Pune
```

With DISTINCT:

```text
Mumbai
Delhi
Pune
```

---

## Business Use Case

Find all unique customer cities:

```sql
SELECT DISTINCT City
FROM Customers;
```

This can help businesses identify the locations they serve.

---

## Common Mistakes

### Expecting DISTINCT to Remove All Duplicate Rows

DISTINCT only removes duplicates from the selected columns.

---

## Interview Questions

### What does DISTINCT do?

It removes duplicate values and returns unique records.

### Can DISTINCT be used with multiple columns?

Yes.

```sql
SELECT DISTINCT City, Name
FROM Customers;
```

---

## Practice Questions

1. Display all unique cities.
2. Display all unique customer names.
3. Display all unique city-name combinations.

---

## Key Takeaways

- DISTINCT removes duplicate values.
- It returns unique records.
- It can be used on one or multiple columns.
- Frequently used in business reporting and analytics.
