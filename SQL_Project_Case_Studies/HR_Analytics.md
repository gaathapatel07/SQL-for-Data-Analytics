# HR Analytics

## Project Overview

Human Resources Analytics helps organizations understand employee performance, retention, attrition, and workforce trends.

This project uses SQL to analyze employee data and generate actionable insights for improving employee satisfaction and reducing attrition.

---

# Business Objectives

* Analyze employee attrition.
* Identify factors affecting employee turnover.
* Evaluate department performance.
* Analyze salary distribution.
* Understand workforce demographics.
* Improve employee retention.

---

# Dataset Description

| Column Name        | Description        |
| ------------------ | ------------------ |
| Employee_ID        | Unique Employee ID |
| Employee_Name      | Employee Name      |
| Age                | Employee Age       |
| Gender             | Employee Gender    |
| Department         | Department Name    |
| Job_Role           | Employee Role      |
| Salary             | Annual Salary      |
| Years_At_Company   | Tenure             |
| Job_Satisfaction   | Satisfaction Score |
| Performance_Rating | Performance Score  |
| Attrition          | Yes/No             |
| Education          | Education Level    |

---

# Key Performance Indicators

## Total Employees

```sql
SELECT COUNT(*) AS Total_Employees
FROM Employees;
```

---

## Attrition Count

```sql
SELECT COUNT(*) AS Attrition_Count
FROM Employees
WHERE Attrition = 'Yes';
```

---

## Attrition Rate

```sql
SELECT
ROUND(
COUNT(CASE WHEN Attrition='Yes' THEN 1 END)
* 100.0 /
COUNT(*),
2
) AS Attrition_Rate
FROM Employees;
```

---

## Average Salary

```sql
SELECT
AVG(Salary) AS Average_Salary
FROM Employees;
```

---

# Department Analysis

## Employee Count by Department

```sql
SELECT
Department,
COUNT(*) AS Employee_Count
FROM Employees
GROUP BY Department
ORDER BY Employee_Count DESC;
```

---

## Average Salary by Department

```sql
SELECT
Department,
AVG(Salary) AS Average_Salary
FROM Employees
GROUP BY Department
ORDER BY Average_Salary DESC;
```

---

## Attrition by Department

```sql
SELECT
Department,
COUNT(*) AS Attrition_Count
FROM Employees
WHERE Attrition='Yes'
GROUP BY Department
ORDER BY Attrition_Count DESC;
```

---

# Salary Analysis

## Salary Distribution

```sql
SELECT
MIN(Salary) AS Minimum_Salary,
MAX(Salary) AS Maximum_Salary,
AVG(Salary) AS Average_Salary
FROM Employees;
```

---

## Top 10 Highest Paid Employees

```sql
SELECT
Employee_Name,
Salary
FROM Employees
ORDER BY Salary DESC
LIMIT 10;
```

---

# Performance Analysis

## Average Performance by Department

```sql
SELECT
Department,
AVG(Performance_Rating) AS Avg_Performance
FROM Employees
GROUP BY Department;
```

---

## Top Performing Employees

```sql
SELECT
Employee_Name,
Performance_Rating
FROM Employees
ORDER BY Performance_Rating DESC
LIMIT 10;
```

---

# Experience Analysis

## Employees by Tenure

```sql
SELECT
Years_At_Company,
COUNT(*) AS Employee_Count
FROM Employees
GROUP BY Years_At_Company
ORDER BY Years_At_Company;
```

---

## Attrition by Tenure

```sql
SELECT
Years_At_Company,
COUNT(*) AS Attrition_Count
FROM Employees
WHERE Attrition='Yes'
GROUP BY Years_At_Company;
```

---

# Job Satisfaction Analysis

## Average Satisfaction by Department

```sql
SELECT
Department,
AVG(Job_Satisfaction) AS Avg_Satisfaction
FROM Employees
GROUP BY Department;
```

---

## Low Satisfaction Employees

```sql
SELECT
Employee_Name,
Department,
Job_Satisfaction
FROM Employees
WHERE Job_Satisfaction <= 2;
```

---

# Advanced SQL Analysis

## Rank Employees by Salary

```sql
SELECT
Employee_Name,
Salary,
RANK() OVER (
ORDER BY Salary DESC
) AS Salary_Rank
FROM Employees;
```

---

## Rank Employees Within Departments

```sql
SELECT
Department,
Employee_Name,
Salary,
ROW_NUMBER() OVER (
PARTITION BY Department
ORDER BY Salary DESC
) AS Department_Rank
FROM Employees;
```

---

## Running Salary Total

```sql
SELECT
Employee_ID,
Salary,
SUM(Salary)
OVER (
ORDER BY Employee_ID
) AS Running_Total
FROM Employees;
```

---

# Business Insights

1. Certain departments experience higher attrition.
2. Employees with lower satisfaction scores are more likely to leave.
3. Salary differences exist across departments.
4. Longer tenure employees generally have lower attrition rates.
5. Performance and satisfaction show positive correlation.

---

# Recommendations

## Recommendation 1

Improve employee engagement programs.

---

## Recommendation 2

Conduct regular satisfaction surveys.

---

## Recommendation 3

Review compensation structures.

---

## Recommendation 4

Focus retention efforts on high-attrition departments.

---

## Recommendation 5

Create career growth opportunities for employees.

---

# Dashboard Design

## KPI Cards

* Total Employees
* Attrition Rate
* Average Salary
* Average Satisfaction

---

## Visualizations

* Attrition by Department
* Salary Distribution
* Employee Count by Department
* Satisfaction Analysis
* Performance Analysis

---

# Skills Demonstrated

* SQL Aggregations
* Window Functions
* HR Analytics
* Attrition Analysis
* Employee Performance Analysis
* KPI Development
* Business Intelligence

---

# Conclusion

This project demonstrates how SQL can be used to analyze workforce data, identify attrition drivers, improve employee retention, and support strategic HR decision-making.

