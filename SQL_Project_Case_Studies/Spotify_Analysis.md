# Spotify Analysis

## Project Overview

Spotify is one of the world's largest music streaming platforms. This project analyzes Spotify track data to understand artist performance, music popularity, listener preferences, genre trends, and audio characteristics.

The objective is to derive business insights that can help improve recommendation systems and content strategy.

---

# Business Objectives

* Identify top-performing artists.
* Analyze track popularity.
* Understand genre trends.
* Study audio feature distributions.
* Discover listener preferences.
* Support music recommendation strategies.

---

# Dataset Description

| Column Name      | Description          |
| ---------------- | -------------------- |
| Track_Name       | Song Name            |
| Artist           | Artist Name          |
| Album            | Album Name           |
| Popularity       | Popularity Score     |
| Danceability     | Danceability Score   |
| Energy           | Energy Level         |
| Loudness         | Track Loudness       |
| Speechiness      | Speech Content       |
| Acousticness     | Acoustic Content     |
| Instrumentalness | Instrumental Content |
| Valence          | Musical Positivity   |
| Tempo            | Song Tempo           |
| Genre            | Music Genre          |

---

# Key Performance Indicators

## Total Tracks

```sql
SELECT COUNT(*) AS Total_Tracks
FROM Spotify;
```

---

## Total Artists

```sql
SELECT COUNT(DISTINCT Artist) AS Total_Artists
FROM Spotify;
```

---

## Average Popularity

```sql
SELECT AVG(Popularity) AS Average_Popularity
FROM Spotify;
```

---

## Top 10 Most Popular Songs

```sql
SELECT
Track_Name,
Artist,
Popularity
FROM Spotify
ORDER BY Popularity DESC
LIMIT 10;
```

---

## Top Artists by Number of Tracks

```sql
SELECT
Artist,
COUNT(*) AS Total_Tracks
FROM Spotify
GROUP BY Artist
ORDER BY Total_Tracks DESC
LIMIT 10;
```

---

# Genre Analysis

## Most Popular Genres

```sql
SELECT
Genre,
COUNT(*) AS Track_Count
FROM Spotify
GROUP BY Genre
ORDER BY Track_Count DESC;
```

---

## Average Popularity by Genre

```sql
SELECT
Genre,
AVG(Popularity) AS Avg_Popularity
FROM Spotify
GROUP BY Genre
ORDER BY Avg_Popularity DESC;
```

---

# Audio Feature Analysis

## Average Danceability

```sql
SELECT
AVG(Danceability) AS Avg_Danceability
FROM Spotify;
```

---

## Average Energy

```sql
SELECT
AVG(Energy) AS Avg_Energy
FROM Spotify;
```

---

## Most Energetic Songs

```sql
SELECT
Track_Name,
Artist,
Energy
FROM Spotify
ORDER BY Energy DESC
LIMIT 10;
```

---

# Advanced SQL Analysis

## Rank Artists by Popularity

```sql
SELECT
Artist,
AVG(Popularity) AS Avg_Popularity,
RANK() OVER (
ORDER BY AVG(Popularity) DESC
) AS Artist_Rank
FROM Spotify
GROUP BY Artist;
```

---

## Popularity Distribution

```sql
SELECT
NTILE(4) OVER (
ORDER BY Popularity DESC
) AS Popularity_Group,
Popularity
FROM Spotify;
```

---

# Business Insights

1. Pop and Hip-Hop dominate streaming.
2. Highly danceable songs receive more engagement.
3. A small group of artists contributes most streams.
4. Popular tracks usually have high energy levels.
5. Listener preferences vary significantly by genre.

---

# Recommendations

1. Promote top-performing artists.
2. Invest in high-engagement genres.
3. Improve recommendation systems using audio features.
4. Build playlists around popular song characteristics.

---

# Dashboard Design

## KPI Cards

* Total Tracks
* Total Artists
* Average Popularity
* Top Genre

## Visualizations

* Top Artists
* Genre Distribution
* Popularity Trends
* Audio Feature Analysis
* Top Songs

---

# Skills Demonstrated

* SQL Aggregations
* Window Functions
* Ranking Analysis
* Music Analytics
* KPI Analysis
* Data Visualization Planning

---

# Conclusion

This project demonstrates how SQL can be used to analyze music streaming data, identify trends, and generate actionable business insights for content strategy and recommendation systems.

