# SELF JOIN

## Overview

A SELF JOIN is a join in which a table is joined with itself.

It is useful when rows within the same table are related to one another.

## Why It Matters

Data Analysts use SELF JOIN to:

- Analyze employee-manager relationships
- Compare records within the same table
- Build organizational hierarchies
- Find related products or customers

---

## Sample Dataset

### Employees

| Employee_ID | Employee_Name | Manager_ID |
|------------|--------------|-----------|
| 1 | Rahul | NULL |
| 2 | Priya | 1 |
| 3 | Aman | 1 |
| 4 | Neha | 2 |

---

## Syntax

```sql
SELECT
A.column_name,
B.column_name
FROM table_name A
JOIN table_name B
ON A.column_name = B.column_name;
```

---

## Example

Display employees and their managers.

```sql
SELECT
E.Employee_Name AS Employee,
M.Employee_Name AS Manager
FROM Employees E
LEFT JOIN Employees M
ON E.Manager_ID = M.Employee_ID;
```

### Result

| Employee | Manager |
|----------|----------|
| Rahul | NULL |
| Priya | Rahul |
| Aman | Rahul |
| Neha | Priya |

---

## Visual Explanation

```text
Employees Table

Rahul
│
├── Priya
│   └── Neha
│
└── Aman
```

---

## Business Use Case

Find reporting hierarchy in an organization.

```sql
SELECT
E.Employee_Name,
M.Employee_Name AS Manager
FROM Employees E
LEFT JOIN Employees M
ON E.Manager_ID = M.Employee_ID;
```

---

## Common Mistakes

### Forgetting Aliases

Incorrect:

```sql
SELECT *
FROM Employees
JOIN Employees;
```

Correct:

```sql
SELECT *
FROM Employees E
JOIN Employees M;
```

---

## Interview Questions

### What is a SELF JOIN?

A join where a table is joined with itself.

### Why are aliases required?

To differentiate between the two instances of the same table.

---

## Practice Questions

1. Display employees and managers.
2. Display students and mentors.
3. Display products and parent products.

---

## Key Takeaways

- SELF JOIN joins a table to itself.
- Aliases are required.
- Useful for hierarchical relationships.
- Commonly used in organizational data.
