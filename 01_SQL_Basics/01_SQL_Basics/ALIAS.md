# SQL Aliases (AS)

## Overview

Aliases are temporary names assigned to columns or tables.

They improve readability and make query results easier to understand.

## Why It Matters

Data Analysts use aliases to:

- Create cleaner reports
- Rename complex column names
- Improve query readability
- Simplify joins

---

## Sample Dataset

### Employees Table

| Employee_ID | Name | Salary |
|------------|------|--------|
| 1 | Rahul | 50000 |
| 2 | Priya | 70000 |
| 3 | Aman | 45000 |

---

## Basic Syntax

### Column Alias

```sql
SELECT column_name AS alias_name
FROM table_name;
```

### Example

```sql
SELECT Name AS Employee_Name
FROM Employees;
```

### Result

| Employee_Name |
|--------------|
| Rahul |
| Priya |
| Aman |

---

## Alias Without AS

```sql
SELECT Name Employee_Name
FROM Employees;
```

This also works in most SQL databases.

---

## Table Alias

```sql
SELECT e.Name
FROM Employees AS e;
```

Here, `e` is a table alias.

---

## Business Use Case

Generate a revenue report.

```sql
SELECT SUM(Sales) AS Total_Revenue
FROM Orders;
```

### Result

| Total_Revenue |
|--------------|
| 250000 |

This looks much more professional than showing:

```text
SUM(Sales)
```

---

## Common Mistakes

### Using Spaces Without Quotes

Incorrect:

```sql
SELECT Name AS Employee Name
FROM Employees;
```

Correct:

```sql
SELECT Name AS Employee_Name
FROM Employees;
```

---

## Interview Questions

### What is an alias?

A temporary name assigned to a column or table.

### Does alias change the database structure?

No. It only affects the query output.

---

## Practice Questions

1. Rename Name as Employee_Name.
2. Rename Salary as Monthly_Salary.
3. Create a table alias for Employees.

---

## Key Takeaways

- Aliases improve readability.
- AS keyword is commonly used.
- Aliases can be assigned to columns and tables.
- Frequently used in reports and dashboards.
