# Subqueries

## Overview

A subquery is a query nested inside another SQL query.

The inner query executes first, and its result is used by the outer query.

## Why It Matters

Data Analysts use subqueries to:

- Find top-performing customers
- Compare values against averages
- Create advanced reports
- Perform multi-step analysis

---

## Syntax

```sql
SELECT column_name
FROM table_name
WHERE column_name operator
(
    SELECT column_name
    FROM table_name
);
```

---

## Sample Dataset

### Employees

| Employee_ID | Name | Salary |
|------------|------|---------|
| 1 | Rahul | 40000 |
| 2 | Priya | 70000 |
| 3 | Aman | 55000 |
| 4 | Neha | 80000 |

---

## Example

Find employees earning more than the average salary.

```sql
SELECT Name,
       Salary
FROM Employees
WHERE Salary >
(
    SELECT AVG(Salary)
    FROM Employees
);
```

### Result

| Name | Salary |
|------|---------|
| Priya | 70000 |
| Neha | 80000 |

---

## How It Works

Step 1:

```sql
SELECT AVG(Salary)
FROM Employees;
```

Result:

```text
61250
```

Step 2:

```sql
SELECT Name,
       Salary
FROM Employees
WHERE Salary > 61250;
```

---

## Business Use Case

Find customers spending more than the average customer.

```sql
SELECT *
FROM Customers
WHERE Revenue >
(
    SELECT AVG(Revenue)
    FROM Customers
);
```

---

## Types of Subqueries

### Single Row Subquery

Returns one value.

```sql
SELECT *
FROM Employees
WHERE Salary >
(
    SELECT AVG(Salary)
    FROM Employees
);
```

---

### Multiple Row Subquery

Returns multiple values.

```sql
SELECT *
FROM Customers
WHERE City IN
(
    SELECT City
    FROM Branches
);
```

---

## Common Mistakes

### Returning Multiple Values with =

Incorrect:

```sql
SELECT *
FROM Customers
WHERE City =
(
    SELECT City
    FROM Branches
);
```

Correct:

```sql
SELECT *
FROM Customers
WHERE City IN
(
    SELECT City
    FROM Branches
);
```

---

## Interview Questions

### What is a subquery?

A query inside another query.

### Which query executes first?

The inner query executes first.

### Can subqueries return multiple rows?

Yes.

---

## Practice Questions

1. Find employees earning above average salary.
2. Find customers spending above average revenue.
3. Find products with prices above average price.

---

## Key Takeaways

- A subquery is a query inside another query.
- The inner query executes first.
- Useful for advanced filtering and analysis.
- Frequently asked in SQL interviews.
