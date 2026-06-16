# Window Functions Cheat Sheet

## ROW_NUMBER()

```sql id="wf1"
ROW_NUMBER() OVER (
ORDER BY Revenue DESC
)
```

Assigns unique numbers.

---

## RANK()

```sql id="wf2"
RANK() OVER (
ORDER BY Revenue DESC
)
```

Allows ties and skips ranks.

---

## DENSE_RANK()

```sql id="wf3"
DENSE_RANK() OVER (
ORDER BY Revenue DESC
)
```

Allows ties but does not skip ranks.

---

## LAG()

```sql id="wf4"
LAG(Revenue)
OVER (
ORDER BY Month
)
```

Returns previous row value.

---

## LEAD()

```sql id="wf5"
LEAD(Revenue)
OVER (
ORDER BY Month
)
```

Returns next row value.

---

## NTILE()

```sql id="wf6"
NTILE(4)
OVER (
ORDER BY Revenue DESC
)
```

Divides rows into groups.

---

## FIRST_VALUE()

```sql id="wf7"
FIRST_VALUE(Revenue)
OVER (
ORDER BY Revenue DESC
)
```

Returns first value.

---

## LAST_VALUE()

```sql id="wf8"
LAST_VALUE(Revenue)
OVER (
ORDER BY Revenue DESC
ROWS BETWEEN UNBOUNDED PRECEDING
AND UNBOUNDED FOLLOWING
)
```

Returns last value.

---

## Running Total

```sql id="wf9"
SUM(Revenue)
OVER (
ORDER BY Order_Date
)
```

---

## Partition Example

```sql id="wf10"
RANK() OVER (
PARTITION BY Department
ORDER BY Salary DESC
)
```

Ranks employees within departments.

---

## Most Important Interview Functions

1. ROW_NUMBER()
2. RANK()
3. DENSE_RANK()
4. LAG()
5. LEAD()

Master these 5 and you'll solve most SQL interview questions.

