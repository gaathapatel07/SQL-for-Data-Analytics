# BETWEEN Operator

## Overview

The BETWEEN operator is used to filter values within a specified range.

The starting and ending values are included in the result.

## Why It Matters

Data Analysts use BETWEEN to:

- Analyze date ranges
- Filter salaries
- Study sales periods
- Segment customers by age

---

## Sample Dataset

### Employees Table

| Employee_ID | Name | Salary |
|------------|------|---------|
| 1 | Rahul | 40000 |
| 2 | Priya | 55000 |
| 3 | Aman | 70000 |
| 4 | Neha | 85000 |

---

## Syntax

```sql
SELECT *
FROM table_name
WHERE column_name BETWEEN value1 AND value2;
```

---

## Example

```sql
SELECT *
FROM Employees
WHERE Salary BETWEEN 50000 AND 80000;
```

### Result

| Employee_ID | Name | Salary |
|------------|------|---------|
| 2 | Priya | 55000 |
| 3 | Aman | 70000 |

---

## Visual Explanation

```text
50000 -------------------- 80000

Included Range
```

---

## Business Use Case

Find employees earning between ₹50,000 and ₹80,000.

```sql
SELECT *
FROM Employees
WHERE Salary BETWEEN 50000 AND 80000;
```

---

## Common Mistakes

### Reversing Values

Incorrect:

```sql
SELECT *
FROM Employees
WHERE Salary BETWEEN 80000 AND 50000;
```

Correct:

```sql
SELECT *
FROM Employees
WHERE Salary BETWEEN 50000 AND 80000;
```

---

## Interview Questions

### Does BETWEEN include boundary values?

Yes.

### Can BETWEEN be used with dates?

Yes.

```sql
SELECT *
FROM Orders
WHERE Order_Date
BETWEEN '2025-01-01' AND '2025-01-31';
```

---

## Practice Questions

1. Find salaries between 40,000 and 70,000.
2. Find ages between 20 and 30.
3. Find orders placed during January.

---

## Key Takeaways

- BETWEEN filters values within a range.
- Start and end values are included.
- Commonly used with numbers and dates.
