# Netflix Content Analysis

## Project Overview

Netflix is one of the world's largest streaming platforms. This project analyzes Netflix content data to understand content distribution, genre popularity, country-wise production, ratings distribution, and release trends.

The objective is to extract business insights using SQL and support content strategy decisions.

---

# Business Objectives

* Analyze content distribution.
* Identify popular genres.
* Understand country-wise content production.
* Analyze ratings and audience targeting.
* Study release trends.
* Support content acquisition decisions.

---

# Dataset Description

| Column Name  | Description           |
| ------------ | --------------------- |
| Show_ID      | Unique Content ID     |
| Type         | Movie or TV Show      |
| Title        | Content Title         |
| Director     | Director Name         |
| Cast         | Cast Members          |
| Country      | Production Country    |
| Date_Added   | Date Added to Netflix |
| Release_Year | Release Year          |
| Rating       | Audience Rating       |
| Duration     | Content Duration      |
| Listed_In    | Genre                 |
| Description  | Content Description   |

---

# Key Performance Indicators

## Total Content

```sql id="n1"
SELECT COUNT(*) AS Total_Content
FROM Netflix;
```

---

## Movies vs TV Shows

```sql id="n2"
SELECT
Type,
COUNT(*) AS Total_Content
FROM Netflix
GROUP BY Type;
```

---

## Content by Rating

```sql id="n3"
SELECT
Rating,
COUNT(*) AS Total_Content
FROM Netflix
GROUP BY Rating
ORDER BY Total_Content DESC;
```

---

## Top 10 Content Producing Countries

```sql id="n4"
SELECT
Country,
COUNT(*) AS Total_Content
FROM Netflix
GROUP BY Country
ORDER BY Total_Content DESC
LIMIT 10;
```

---

# Genre Analysis

## Most Popular Genres

```sql id="n5"
SELECT
Listed_In,
COUNT(*) AS Total_Content
FROM Netflix
GROUP BY Listed_In
ORDER BY Total_Content DESC;
```

### Insight

Identifies genres preferred by Netflix audiences.

---

# Release Year Analysis

## Content Released Per Year

```sql id="n6"
SELECT
Release_Year,
COUNT(*) AS Total_Content
FROM Netflix
GROUP BY Release_Year
ORDER BY Release_Year;
```

### Insight

Shows growth in content production over time.

---

# Content Addition Analysis

## Content Added Per Year

```sql id="n7"
SELECT
YEAR(Date_Added) AS Added_Year,
COUNT(*) AS Content_Count
FROM Netflix
GROUP BY Added_Year
ORDER BY Added_Year;
```

---

# Director Analysis

## Top Directors

```sql id="n8"
SELECT
Director,
COUNT(*) AS Total_Content
FROM Netflix
WHERE Director IS NOT NULL
GROUP BY Director
ORDER BY Total_Content DESC
LIMIT 10;
```

---

# Rating Analysis

## Most Common Ratings

```sql id="n9"
SELECT
Rating,
COUNT(*) AS Total_Content
FROM Netflix
GROUP BY Rating
ORDER BY Total_Content DESC;
```

---

# Advanced SQL Analysis

## Rank Genres by Popularity

```sql id="n10"
SELECT
Listed_In,
COUNT(*) AS Total_Content,
RANK() OVER (
ORDER BY COUNT(*) DESC
) AS Genre_Rank
FROM Netflix
GROUP BY Listed_In;
```

---

## Running Total of Content Released

```sql id="n11"
SELECT
Release_Year,
COUNT(*) AS Total_Content,
SUM(COUNT(*))
OVER (
ORDER BY Release_Year
) AS Running_Total
FROM Netflix
GROUP BY Release_Year;
```

---

# Business Insights

1. Movies dominate the platform.
2. Drama and Comedy are the most common genres.
3. The United States contributes the highest content volume.
4. Content production has grown significantly since 2015.
5. TV-MA is among the most common ratings.

---

# Recommendations

1. Invest more in high-performing genres.
2. Expand content production in growing regions.
3. Acquire content targeting popular ratings.
4. Focus on genres with increasing audience demand.

---

# Dashboard Design

## KPI Cards

* Total Content
* Total Movies
* Total TV Shows
* Total Countries

## Charts

* Content by Genre
* Content by Country
* Content by Rating
* Release Year Trend
* Top Directors

---

# Skills Demonstrated

* SQL Aggregations
* Window Functions
* Ranking Functions
* Trend Analysis
* Content Analytics
* Business Intelligence

---

# Conclusion

This project demonstrates how SQL can be used to analyze streaming platform content and support strategic decisions regarding content production, acquisition, and audience engagement.

