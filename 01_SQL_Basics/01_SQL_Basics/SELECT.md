# SELECT Statement

## Overview

The `SELECT` statement is used to retrieve data from a database table. It is the most fundamental SQL command and serves as the starting point for almost every data analysis task.

## Why It Matters

Data Analysts use the SELECT statement to:

- Retrieve specific information from a dataset
- Explore and understand data
- Create reports and dashboards
- Perform business analysis

---

## Sample Dataset

### Customers Table

| Customer_ID | Name  | City      | Age |
|------------|--------|-----------|-----|
| 1 | Rahul | Mumbai | 22 |
| 2 | Priya | Delhi | 25 |
| 3 | Aman | Pune | 21 |
| 4 | Neha | Bangalore | 24 |

---

## Basic Syntax

```sql
SELECT column_name
FROM table_name;
```

### Example

```sql
SELECT Name
FROM Customers;
```

### Result

| Name |
|------|
| Rahul |
| Priya |
| Aman |
| Neha |

---

## Selecting Multiple Columns

### Query

```sql
SELECT Name, City
FROM Customers;
```

### Result

| Name | City |
|------|------|
| Rahul | Mumbai |
| Priya | Delhi |
| Aman | Pune |
| Neha | Bangalore |

---

## Selecting All Columns

The asterisk (*) represents all columns.

### Query

```sql
SELECT *
FROM Customers;
```

### Result

| Customer_ID | Name | City | Age |
|------------|------|------|-----|
| 1 | Rahul | Mumbai | 22 |
| 2 | Priya | Delhi | 25 |
| 3 | Aman | Pune | 21 |
| 4 | Neha | Bangalore | 24 |

---

## Visual Explanation

```text
Customers Table
│
├── Customer_ID
├── Name
├── City
└── Age

SELECT Name

↓

Name
-----
Rahul
Priya
Aman
Neha
```

---

## Business Use Case

Suppose you work as a Data Analyst for an e-commerce company.

Your manager asks:

"Show the names and cities of all customers."

SQL Query:

```sql
SELECT Name, City
FROM Customers;
```

This information can be used for:

- Customer segmentation
- Regional analysis
- Marketing campaigns

---

## Common Mistakes

### Forgetting the FROM Clause

Incorrect:

```sql
SELECT Name;
```

Correct:

```sql
SELECT Name
FROM Customers;
```

---

### Typing the Wrong Column Name

Incorrect:

```sql
SELECT Nam
FROM Customers;
```

Correct:

```sql
SELECT Name
FROM Customers;
```

---

## Interview Questions

### What is the purpose of the SELECT statement?

The SELECT statement retrieves data from one or more database tables.

### What does the asterisk (*) represent?

It represents all columns in a table.

### Can SELECT retrieve multiple columns?

Yes.

Example:

```sql
SELECT Name, City
FROM Customers;
```

---

## Practice Questions

### Easy

Display all customer names.

### Medium

Display customer names and ages.

### Challenge

Display all columns from the Customers table.

---

## Key Takeaways

- SELECT is used to retrieve data from a database.
- It can return one column, multiple columns, or all columns.
- The asterisk (*) returns all columns.
- SELECT is one of the most frequently used SQL commands in Data Analytics.
