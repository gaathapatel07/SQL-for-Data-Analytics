# OR Operator

## Overview

The OR operator is used to combine multiple conditions.

A row is returned if at least one condition evaluates to TRUE.

## Why It Matters

Data Analysts use OR to:

- Combine customer segments
- Analyze multiple regions
- Filter different product categories
- Build flexible reports

---

## Sample Dataset

### Customers Table

| Customer_ID | Name | City | Age |
|------------|------|------|-----|
| 1 | Rahul | Mumbai | 22 |
| 2 | Priya | Delhi | 25 |
| 3 | Aman | Mumbai | 28 |
| 4 | Neha | Pune | 24 |

---

## Syntax

```sql
SELECT column_name
FROM table_name
WHERE condition1 OR condition2;
```

---

## Example

Find customers from Mumbai or Delhi.

```sql
SELECT *
FROM Customers
WHERE City = 'Mumbai'
OR City = 'Delhi';
```

### Result

| Customer_ID | Name | City | Age |
|------------|------|------|-----|
| 1 | Rahul | Mumbai | 22 |
| 2 | Priya | Delhi | 25 |
| 3 | Aman | Mumbai | 28 |

---

## Visual Explanation

```text
City = Mumbai
      OR
City = Delhi

↓

Rows satisfying ANY condition
```

---

## Business Use Case

Find customers from major target markets.

```sql
SELECT *
FROM Customers
WHERE City = 'Mumbai'
OR City = 'Delhi';
```

This helps businesses focus on multiple regions simultaneously.

---

## Common Mistakes

### Confusing OR with AND

AND requires all conditions to be TRUE.

OR requires at least one condition to be TRUE.

---

## Interview Questions

### What does OR do?

OR returns rows when any condition evaluates to TRUE.

### Can OR combine multiple conditions?

Yes.

```sql
SELECT *
FROM Customers
WHERE City = 'Mumbai'
OR City = 'Delhi'
OR City = 'Pune';
```

---

## Practice Questions

1. Display customers from Mumbai or Pune.
2. Display customers from Delhi or Mumbai.
3. Display customers from Pune or Delhi.

---

## Key Takeaways

- OR combines multiple conditions.
- At least one condition must be TRUE.
- Useful for combining customer groups and business segments.
