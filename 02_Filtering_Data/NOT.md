# NOT Operator

## Overview

The NOT operator is used to exclude rows that satisfy a condition.

It returns records where the specified condition is FALSE.

## Why It Matters

Data Analysts use NOT to:

- Exclude specific cities
- Ignore unwanted categories
- Remove test data
- Filter out inactive users

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
SELECT *
FROM table_name
WHERE NOT condition;
```

## Example

```sql
SELECT *
FROM Customers
WHERE NOT City = 'Mumbai';
```

### Result

| Customer_ID | Name | City |
|------------|------|------|
| 2 | Priya | Delhi |
| 3 | Aman | Pune |

---

## Business Use Case

Find customers who are not from Mumbai.

```sql
SELECT *
FROM Customers
WHERE NOT City = 'Mumbai';
```

---

## Common Mistakes

Incorrect:

```sql
SELECT *
FROM Customers
WHERE City NOT 'Mumbai';
```

Correct:

```sql
SELECT *
FROM Customers
WHERE NOT City = 'Mumbai';
```

---

## Interview Questions

### What does NOT do?

It reverses a condition.

### Can NOT be combined with IN?

Yes.

```sql
SELECT *
FROM Customers
WHERE City NOT IN ('Mumbai', 'Delhi');
```

---

## Practice Questions

1. Display customers not from Pune.
2. Display customers not from Delhi.
3. Display customers not from Mumbai.

---

## Key Takeaways

- NOT excludes matching records.
- Often used with IN and LIKE.
- Useful for removing unwanted data.
