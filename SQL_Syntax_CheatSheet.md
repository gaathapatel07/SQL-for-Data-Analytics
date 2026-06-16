# SQL Syntax Cheat Sheet

## SELECT

```sql id="cs1"
SELECT column_name
FROM table_name;
```

---

## WHERE

```sql id="cs2"
SELECT *
FROM Customers
WHERE City = 'Mumbai';
```

---

## ORDER BY

```sql id="cs3"
SELECT *
FROM Employees
ORDER BY Salary DESC;
```

---

## DISTINCT

```sql id="cs4"
SELECT DISTINCT City
FROM Customers;
```

---

## LIMIT

```sql id="cs5"
SELECT *
FROM Products
LIMIT 5;
```

---

## COUNT

```sql id="cs6"
SELECT COUNT(*)
FROM Orders;
```

---

## SUM

```sql id="cs7"
SELECT SUM(Revenue)
FROM Sales;
```

---

## AVG

```sql id="cs8"
SELECT AVG(Salary)
FROM Employees;
```

---

## GROUP BY

```sql id="cs9"
SELECT City,
COUNT(*)
FROM Customers
GROUP BY City;
```

---

## HAVING

```sql id="cs10"
SELECT City,
COUNT(*)
FROM Customers
GROUP BY City
HAVING COUNT(*) > 5;
```

---

## CASE WHEN

```sql id="cs11"
SELECT
Revenue,
CASE
WHEN Revenue > 10000 THEN 'Premium'
ELSE 'Regular'
END
FROM Customers;
```

---

## SUBQUERY

```sql id="cs12"
SELECT *
FROM Employees
WHERE Salary >
(
SELECT AVG(Salary)
FROM Employees
);
```

