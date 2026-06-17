# Blinkit Sales Analysis

## Objective

Analyze sales performance across products, outlets, and categories.

## KPIs

- Total Sales
- Average Sales
- Top Products
- Outlet Performance

## SQL Questions

### Total Sales

SELECT SUM(Sales)
FROM Blinkit;

### Top 10 Products

SELECT Product_Name,
SUM(Sales)
FROM Blinkit
GROUP BY Product_Name
ORDER BY SUM(Sales) DESC
LIMIT 10;

## Insights

- Fruits generate highest sales.
- Tier 1 cities contribute most revenue.
