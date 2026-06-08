# LIMIT Clause

## Overview

The `LIMIT` clause is used to restrict the number of rows returned by a query.

Instead of displaying all records, LIMIT allows you to retrieve only a specific number of rows.

## Why It Matters

Data Analysts use LIMIT to:

- Preview datasets
- Check query outputs quickly
- Retrieve top records
- Improve query readability

---

## Sample Dataset

### Products Table

| Product_ID | Product_Name | Price |
|------------|-------------|--------|
| 1 | Laptop | 50000 |
| 2 | Mobile | 25000 |
| 3 | Tablet | 18000 |
| 4 | Keyboard | 1500 |
| 5 | Mouse | 800 |

---

## Basic Syntax

```sql
SELECT column_name
FROM table_name
LIMIT number;
```

---

## Example

```sql
SELECT *
FROM Products
LIMIT 3;
```

### Result

| Product_ID | Product_Name | Price |
|------------|-------------|--------|
| 1 | Laptop | 50000 |
| 2 | Mobile | 25000 |
| 3 | Tablet | 18000 |

---

## Combining ORDER BY and LIMIT

Find the 3 most expensive products.

```sql
SELECT *
FROM Products
ORDER BY Price DESC
LIMIT 3;
```

### Result

| Product_Name | Price |
|-------------|--------|
| Laptop | 50000 |
| Mobile | 25000 |
| Tablet | 18000 |

---

## Business Use Case

Find the top 5 customers generating the highest revenue.

```sql
SELECT Customer_ID, Revenue
FROM Customers
ORDER BY Revenue DESC
LIMIT 5;
```

---

## Common Mistakes

### Forgetting ORDER BY

Incorrect:

```sql
SELECT *
FROM Products
LIMIT 3;
```

This returns random first 3 rows.

Better:

```sql
SELECT *
FROM Products
ORDER BY Price DESC
LIMIT 3;
```

---

## Interview Questions

### What does LIMIT do?

It restricts the number of rows returned by a query.

### Can LIMIT be used with ORDER BY?

Yes. They are frequently used together.

---

## Practice Questions

1. Display first 2 products.
2. Display top 3 expensive products.
3. Display top 5 customers by revenue.

---

## Key Takeaways

- LIMIT restricts rows returned.
- Commonly used with ORDER BY.
- Useful for previews and top-N analysis.
