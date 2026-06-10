# LIKE Operator

## Overview

The LIKE operator is used to search for patterns within text values.

It is commonly used when exact values are not known.

## Why It Matters

Data Analysts use LIKE to:

- Search customer names
- Analyze products
- Find email domains
- Filter text-based information

---

## Sample Dataset

### Customers Table

| Customer_ID | Name |
|------------|------|
| 1 | Rahul |
| 2 | Priya |
| 3 | Rohan |
| 4 | Neha |

---

## Wildcards

| Symbol | Meaning |
|----------|----------|
| % | Any number of characters |
| _ | Exactly one character |

---

## Syntax

```sql
SELECT column_name
FROM table_name
WHERE column_name LIKE pattern;
```

---

## Example 1

Names starting with R.

```sql
SELECT *
FROM Customers
WHERE Name LIKE 'R%';
```

### Result

| Customer_ID | Name |
|------------|------|
| 1 | Rahul |
| 3 | Rohan |

---

## Example 2

Names ending with a.

```sql
SELECT *
FROM Customers
WHERE Name LIKE '%a';
```

### Result

| Customer_ID | Name |
|------------|------|
| 2 | Priya |
| 4 | Neha |

---

## Example 3

Names containing "oh".

```sql
SELECT *
FROM Customers
WHERE Name LIKE '%oh%';
```

### Result

| Customer_ID | Name |
|------------|------|
| 3 | Rohan |

---

## Visual Explanation

```text
R%

R + anything

↓

Rahul
Rohan
```

---

## Business Use Case

Find all customers whose names start with a specific letter.

```sql
SELECT *
FROM Customers
WHERE Name LIKE 'A%';
```

Useful for customer search systems.

---

## Common Mistakes

### Forgetting Quotes

Incorrect:

```sql
SELECT *
FROM Customers
WHERE Name LIKE R%;
```

Correct:

```sql
SELECT *
FROM Customers
WHERE Name LIKE 'R%';
```

---

## Interview Questions

### What does % mean?

It represents any number of characters.

### What does _ mean?

It represents exactly one character.

---

## Practice Questions

1. Find names starting with P.
2. Find names ending with l.
3. Find names containing "ha".

---

## Key Takeaways

- LIKE is used for pattern matching.
- % represents multiple characters.
- _ represents a single character.
- Frequently used in search and filtering operations.
