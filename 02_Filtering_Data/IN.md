# IN Operator

## Overview

The IN operator allows you to specify multiple values in a WHERE clause.

Instead of writing multiple OR conditions, IN provides a cleaner and more readable solution.

## Why It Matters

Data Analysts use IN to:

- Filter multiple cities
- Analyze specific product categories
- Segment customers
- Create targeted reports

---

## Sample Dataset

### Customers Table

| Customer_ID | Name | City |
|------------|------|------|
| 1 | Rahul | Mumbai |
| 2 | Priya | Delhi |
| 3 | Aman | Pune |
| 4 | Neha | Mumbai |

---

## Syntax

```sql
SELECT column_name
FROM table_name
WHERE column_name IN (value1, value2, value3);
```

---

## Example

Find customers from Mumbai and Delhi.

```sql
SELECT *
FROM Customers
WHERE City IN ('Mumbai', 'Delhi');
```

### Result

| Customer_ID | Name | City |
|------------|------|------|
| 1 | Rahul | Mumbai |
| 2 | Priya | Delhi |
| 4 | Neha | Mumbai |

---

## Equivalent Query Using OR

```sql
SELECT *
FROM Customers
WHERE City = 'Mumbai'
OR City = 'Delhi';
```

The IN operator makes queries shorter and easier to read.

---

## Business Use Case

Find customers from major target markets.

```sql
SELECT *
FROM Customers
WHERE City IN ('Mumbai', 'Delhi', 'Bangalore');
```

---

## Common Mistakes

### Missing Parentheses

Incorrect:

```sql
SELECT *
FROM Customers
WHERE City IN 'Mumbai', 'Delhi';
```

Correct:

```sql
SELECT *
FROM Customers
WHERE City IN ('Mumbai', 'Delhi');
```

---

## Interview Questions

### Why use IN instead of OR?

IN improves readability when checking multiple values.

### Can IN work with numbers?

Yes.

```sql
SELECT *
FROM Customers
WHERE Customer_ID IN (1, 2, 3);
```

---

## Practice Questions

1. Display customers from Mumbai and Pune.
2. Display customers with IDs 1, 2 and 4.
3. Display customers from Delhi, Pune and Mumbai.

---

## Key Takeaways

- IN checks multiple values.
- It replaces long OR conditions.
- Improves query readability.
