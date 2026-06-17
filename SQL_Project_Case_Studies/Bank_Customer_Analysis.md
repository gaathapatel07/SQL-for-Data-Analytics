# Bank Customer Analysis

## Project Overview

Banks generate massive amounts of customer transaction and account data every day. This project analyzes customer demographics, account balances, transactions, loans, and churn behavior to help improve customer retention and profitability.

The objective is to leverage SQL for customer analytics, risk analysis, and business intelligence.

---

# Business Objectives

* Analyze customer demographics.
* Identify high-value customers.
* Understand account balance distribution.
* Analyze loan performance.
* Detect customer churn.
* Improve customer retention strategies.

---

# Dataset Description

| Column Name        | Description        |
| ------------------ | ------------------ |
| Customer_ID        | Unique Customer ID |
| Customer_Name      | Customer Name      |
| Age                | Customer Age       |
| Gender             | Customer Gender    |
| City               | Customer City      |
| Account_Type       | Savings / Current  |
| Account_Balance    | Current Balance    |
| Loan_Amount        | Loan Value         |
| Credit_Score       | Credit Rating      |
| Transaction_Amount | Transaction Value  |
| Churn_Status       | Active / Inactive  |
| Join_Date          | Customer Join Date |

---

# Key Performance Indicators

## Total Customers

```sql
SELECT COUNT(*) AS Total_Customers
FROM Customers;
```

---

## Total Account Balance

```sql
SELECT
SUM(Account_Balance) AS Total_Balance
FROM Customers;
```

---

## Average Account Balance

```sql
SELECT
AVG(Account_Balance) AS Average_Balance
FROM Customers;
```

---

## Total Loans Issued

```sql
SELECT
SUM(Loan_Amount) AS Total_Loans
FROM Customers;
```

---

# Customer Demographics Analysis

## Customers by Gender

```sql
SELECT
Gender,
COUNT(*) AS Customer_Count
FROM Customers
GROUP BY Gender;
```

---

## Customers by City

```sql
SELECT
City,
COUNT(*) AS Customer_Count
FROM Customers
GROUP BY City
ORDER BY Customer_Count DESC;
```

---

# Account Analysis

## Balance by Account Type

```sql
SELECT
Account_Type,
SUM(Account_Balance) AS Total_Balance
FROM Customers
GROUP BY Account_Type;
```

---

## Top 10 Customers by Balance

```sql
SELECT
Customer_Name,
Account_Balance
FROM Customers
ORDER BY Account_Balance DESC
LIMIT 10;
```

---

# Loan Analysis

## Average Loan Amount

```sql
SELECT
AVG(Loan_Amount) AS Average_Loan
FROM Customers;
```

---

## Top Customers by Loan Amount

```sql
SELECT
Customer_Name,
Loan_Amount
FROM Customers
ORDER BY Loan_Amount DESC
LIMIT 10;
```

---

## Loan Distribution by City

```sql
SELECT
City,
SUM(Loan_Amount) AS Total_Loan
FROM Customers
GROUP BY City
ORDER BY Total_Loan DESC;
```

---

# Credit Score Analysis

## Average Credit Score

```sql
SELECT
AVG(Credit_Score) AS Average_Credit_Score
FROM Customers;
```

---

## Customers with Low Credit Scores

```sql
SELECT
Customer_Name,
Credit_Score
FROM Customers
WHERE Credit_Score < 600;
```

---

# Transaction Analysis

## Total Transaction Amount

```sql
SELECT
SUM(Transaction_Amount) AS Total_Transactions
FROM Customers;
```

---

## Average Transaction Value

```sql
SELECT
AVG(Transaction_Amount) AS Average_Transaction
FROM Customers;
```

---

## Top Customers by Transaction Volume

```sql
SELECT
Customer_Name,
SUM(Transaction_Amount) AS Total_Transactions
FROM Customers
GROUP BY Customer_Name
ORDER BY Total_Transactions DESC
LIMIT 10;
```

---

# Customer Churn Analysis

## Churn Count

```sql
SELECT
COUNT(*) AS Churned_Customers
FROM Customers
WHERE Churn_Status='Inactive';
```

---

## Churn Rate

```sql
SELECT
ROUND(
COUNT(CASE WHEN Churn_Status='Inactive' THEN 1 END)
* 100.0 /
COUNT(*),
2
) AS Churn_Rate;
```

---

## Churn by City

```sql
SELECT
City,
COUNT(*) AS Churn_Count
FROM Customers
WHERE Churn_Status='Inactive'
GROUP BY City;
```

---

# Advanced SQL Analysis

## Rank Customers by Balance

```sql
SELECT
Customer_Name,
Account_Balance,
RANK() OVER (
ORDER BY Account_Balance DESC
) AS Balance_Rank
FROM Customers;
```

---

## Customer Segmentation

```sql
SELECT
Customer_Name,
Account_Balance,
CASE
WHEN Account_Balance >= 100000 THEN 'Premium'
WHEN Account_Balance >= 50000 THEN 'Regular'
ELSE 'Basic'
END AS Customer_Segment
FROM Customers;
```

---

## Running Balance Analysis

```sql
SELECT
Customer_ID,
Account_Balance,
SUM(Account_Balance)
OVER (
ORDER BY Customer_ID
) AS Running_Balance
FROM Customers;
```

---

# Business Insights

1. Premium customers contribute most of the deposits.
2. Certain cities generate higher loan demand.
3. Customers with low credit scores present higher risk.
4. A small percentage of customers hold a large percentage of total balances.
5. Churn is concentrated in specific customer groups.

---

# Recommendations

## Recommendation 1

Develop loyalty programs for premium customers.

---

## Recommendation 2

Offer personalized loan products.

---

## Recommendation 3

Monitor high-risk customers proactively.

---

## Recommendation 4

Improve customer engagement to reduce churn.

---

## Recommendation 5

Create targeted financial products for different customer segments.

---

# Dashboard Design

## KPI Cards

* Total Customers
* Total Deposits
* Total Loans
* Churn Rate

---

## Visualizations

* Customer Segmentation
* Loan Distribution
* Credit Score Distribution
* Churn Analysis
* Top Customers

---

# Skills Demonstrated

* SQL Aggregations
* Window Functions
* Customer Analytics
* Churn Analysis
* Risk Analytics
* KPI Development
* Banking Analytics

---

# Conclusion

This project demonstrates how SQL can be used to analyze banking customer data, identify high-value customers, monitor risk, and improve retention strategies through data-driven insights.

