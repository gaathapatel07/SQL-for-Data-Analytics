# ORDER BY Clause

## Overview

The `ORDER BY` clause is used to sort query results in ascending or descending order.

Sorting data helps analysts identify trends, top performers, and outliers more easily.

## Why It Matters

Data Analysts use ORDER BY to:

- Find top-selling products
- Identify highest-paying customers
- Analyze lowest-performing regions
- Sort reports for better readability

---

## Sample Dataset

### Employees Table

| Employee_ID | Name | Salary |
|------------|------|---------|
| 1 | Rahul | 50000 |
| 2 | Priya | 70000 |
| 3 | Aman | 45000 |
| 4 | Neha | 65000 |

---

## Basic Syntax

```sql
SELECT column_name
FROM table_name
ORDER BY column_name;
```

---

## Ascending Order (Default)

```sql
SELECT *
FROM Employees
ORDER BY Salary;
```

### Result

| Name | Salary |
|------|---------|
| Aman | 45000 |
| Rahul | 50000 |
| Neha | 65000 |
| Priya | 70000 |

---

## Descending Order

```sql
SELECT *
FROM Employees
ORDER BY Salary DESC;
```

### Result

| Name | Salary |
|------|---------|
| Priya | 70000 |
| Neha | 65000 |
| Rahul | 50000 |
| Aman | 45000 |

---

## Multiple Columns

```sql
SELECT *
FROM Employees
ORDER BY Salary DESC, Name ASC;
```

---

## Business Use Case

Find the top earning employees:

```sql
SELECT *
FROM Employees
ORDER BY Salary DESC;
```

This is commonly used in HR and compensation analysis.

---

## Common Mistakes

### Misspelling Column Names

Incorrect:

```sql
SELECT *
FROM Employees
ORDER BY Salaries;
```

Correct:

```sql
SELECT *
FROM Employees
ORDER BY Salary;
```

---

## Interview Questions

### What is the default sorting order?

Ascending (ASC).

### How do you sort in descending order?

Using DESC.

---

## Practice Questions

1. Sort employees by salary in ascending order.
2. Sort employees by salary in descending order.
3. Sort employees by name alphabetically.

---

## Key Takeaways

- ORDER BY sorts query results.
- ASC is the default order.
- DESC sorts from highest to lowest.
- Multiple columns can be used for sorting.
