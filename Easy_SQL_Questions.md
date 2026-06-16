# Easy SQL Interview Questions

## Question 1: Find All Customers From Mumbai

### Query

```sql
SELECT *
FROM Customers
WHERE City = 'Mumbai';
```

### Explanation

Returns all customers whose city is Mumbai.

---

## Question 2: Display Unique Cities

### Query

```sql
SELECT DISTINCT City
FROM Customers;
```

### Explanation

Removes duplicate city values.

---

## Question 3: Find Employees With Salary Greater Than ₹50,000

### Query

```sql
SELECT *
FROM Employees
WHERE Salary > 50000;
```

### Explanation

Filters employees earning more than ₹50,000.

---

## Question 4: Count Total Customers

### Query

```sql
SELECT COUNT(*) AS Total_Customers
FROM Customers;
```

### Explanation

Returns the total number of customers.

---

## Question 5: Find Highest Salary

### Query

```sql
SELECT MAX(Salary) AS Highest_Salary
FROM Employees;
```

### Explanation

Returns the maximum salary.

---

## Question 6: Find Lowest Salary

### Query

```sql
SELECT MIN(Salary) AS Lowest_Salary
FROM Employees;
```

### Explanation

Returns the minimum salary.

---

## Question 7: Find Average Salary

### Query

```sql
SELECT AVG(Salary) AS Average_Salary
FROM Employees;
```

### Explanation

Calculates average employee salary.

---

## Question 8: Display Top 5 Products

### Query

```sql
SELECT *
FROM Products
ORDER BY Revenue DESC
LIMIT 5;
```

### Explanation

Returns the top 5 products based on revenue.

---

## Question 9: Find Customers With NULL Emails

### Query

```sql
SELECT *
FROM Customers
WHERE Email IS NULL;
```

### Explanation

Returns customers who have not provided an email address.

---

## Question 10: Sort Customers By Revenue

### Query

```sql
SELECT *
FROM Customers
ORDER BY Revenue DESC;
```

### Explanation

Sorts customers from highest to lowest revenue.

---

## Key Takeaways

* Master SELECT, WHERE, ORDER BY, DISTINCT.
* Understand aggregate functions.
* Learn basic filtering techniques.
* These questions frequently appear in beginner SQL interviews.

