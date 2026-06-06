# WHERE Clause

## Overview

The `WHERE` clause is used to filter records and return only the rows that satisfy a specified condition.

Without a WHERE clause, SQL returns all rows from a table. With a WHERE clause, you can focus on only the data you need.

## Why It Matters

Data Analysts use the WHERE clause to:

- Filter customers by location
- Analyze specific products
- Find orders within a date range
- Investigate business problems
- Create targeted reports

---

## Sample Dataset

### Customers Table

| Customer_ID | Name | City | Age |
|------------|------|------|-----|
| 1 | Rahul | Mumbai | 22 |
| 2 | Priya | Delhi | 25 |
| 3 | Aman | Pune | 21 |
| 4 | Neha | Mumbai | 24 |

---

## Basic Syntax

```sql
SELECT column_name
FROM table_name
WHERE condition;
```

---

## Example 1: Filter by City

### Query

```sql
SELECT *
FROM Customers
WHERE City = 'Mumbai';
```

### Result

| Customer_ID | Name | City | Age |
|------------|------|------|-----|
| 1 | Rahul | Mumbai | 22 |
| 4 | Neha | Mumbai | 24 |

---

## Example 2: Filter by Age

### Query

```sql
SELECT *
FROM Customers
WHERE Age > 22;
```

### Result

| Customer_ID | Name | City | Age |
|------------|------|------|-----|
| 2 | Priya | Delhi | 25 |
| 4 | Neha | Mumbai | 24 |

---

## Comparison Operators

| Operator | Meaning |
|----------|----------|
| = | Equal to |
| > | Greater than |
| < | Less than |
| >= | Greater than or equal to |
| <= | Less than or equal to |
| <> | Not equal to |

### Example

```sql
SELECT *
FROM Customers
WHERE Age >= 24;
```

---

## Visual Explanation

```text
Customers Table
│
├── Rahul   Mumbai
├── Priya   Delhi
├── Aman    Pune
└── Neha    Mumbai

WHERE City = 'Mumbai'

↓

Rahul
Neha
```

---

## Business Use Case

Suppose your manager asks:

"Show all customers from Mumbai."

You can write:

```sql
SELECT *
FROM Customers
WHERE City = 'Mumbai';
```

This helps businesses create location-based marketing campaigns.

---

## Common Mistakes

### Missing Quotes Around Text Values

Incorrect:

```sql
SELECT *
FROM Customers
WHERE City = Mumbai;
```

Correct:

```sql
SELECT *
FROM Customers
WHERE City = 'Mumbai';
```

---

### Using Wrong Column Names

Incorrect:

```sql
SELECT *
FROM Customers
WHERE Cities = 'Mumbai';
```

Correct:

```sql
SELECT *
FROM Customers
WHERE City = 'Mumbai';
```

---

## Interview Questions

### What is the purpose of the WHERE clause?

The WHERE clause filters rows based on specified conditions.

### Can WHERE be used with SELECT?

Yes. It is commonly used with SELECT to retrieve only relevant data.

### What is the difference between WHERE and HAVING?

WHERE filters rows before grouping, while HAVING filters grouped results.

---

## Practice Questions

### Easy

Display all customers from Delhi.

### Medium

Display customers older than 23 years.

### Challenge

Display customers who are not from Mumbai.

---

## Key Takeaways

- WHERE is used to filter records.
- It works with comparison operators.
- It helps analysts focus on relevant data.
- It is one of the most frequently used SQL clauses.
