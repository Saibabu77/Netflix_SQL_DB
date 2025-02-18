# Netflix_SQL_DB
This project involves designing and implementing a structured SQL database for Netflix. The goal is to store, manage, and query data related to Netflix content, including movies, TV shows, user interactions, and ratings. The database is designed to support data retrieval, analytics, and insights generation.
![2DHC1ogkymTA2fKi-generated_image](https://github.com/user-attachments/assets/0a1f5cf8-c83e-4491-9cc7-2c60fbc29c5c)
## Dataset: Business Intelligence Data Analysis

### Schema
The SQL script (`Business Intelligence Data Analysis SQL code.sql`) defines the necessary tables and performs various data analysis tasks. Ensure your database schema aligns with the queries provided.

### Business Problems and Solutions

#### 1. Handling NULL Values
```sql
SELECT * 
FROM table_name
WHERE column_name IS NULL;
```
**Objective:** Identify missing values in critical columns to maintain data integrity.

#### 2. Count Entries by Category
```sql
SELECT category, COUNT(*) 
FROM table_name
GROUP BY category;
```
**Objective:** Determine the distribution of records across different categories.

#### 3. Identify Most Frequent Entries
```sql
SELECT column_name, COUNT(*) AS frequency
FROM table_name
GROUP BY column_name
ORDER BY frequency DESC
LIMIT 1;
```
**Objective:** Find the most frequently occurring value in a given column.

#### 4. Extract Data for a Specific Year
```sql
SELECT * 
FROM table_name
WHERE YEAR(date_column) = 2020;
```
**Objective:** Retrieve all records corresponding to a specific year.

#### 5. Top 5 Records by a Metric
```sql
SELECT * 
FROM table_name
ORDER BY metric_column DESC
LIMIT 5;
```
**Objective:** Identify the top 5 records based on a key performance metric.

#### 6. Find All Entries with a Specific Keyword
```sql
SELECT * 
FROM table_name
WHERE column_name LIKE '%keyword%';
```
**Objective:** Retrieve all records containing a specific keyword in a given column.

#### 7. Rank Records Based on Count
```sql
WITH RankedData AS (
    SELECT category, COUNT(*) AS total_count,
           RANK() OVER (ORDER BY COUNT(*) DESC) AS rank
    FROM table_name
    GROUP BY category
)
SELECT * 
FROM RankedData
WHERE rank <= 5;
```
**Objective:** Rank categories based on the number of records and extract the top 5.

#### 8. Data Segmentation Based on Keywords
```sql
SELECT 
    CASE 
        WHEN description LIKE '%keyword1%' OR description LIKE '%keyword2%' THEN 'Segment A'
        ELSE 'Segment B'
    END AS category,
    COUNT(*) AS count
FROM table_name
GROUP BY category;
```
**Objective:** Categorize records based on keyword presence and analyze distribution.

#### 9. Calculate Average Value for a Specific Column
```sql
SELECT AVG(numeric_column) AS average_value
FROM table_name;
```
**Objective:** Compute the average value of a numeric column for trend analysis.

#### 10. Identify Records Updated in the Last 30 Days
```sql
SELECT * 
FROM table_name
WHERE updated_at >= NOW() - INTERVAL '30 days';
```
**Objective:** Retrieve records that have been updated within the last 30 days for monitoring recent changes.

### Findings and Conclusion
- **Data Integrity:** The presence of NULL values highlights areas requiring data cleaning.
- **Category Distribution:** The dataset contains diverse categories, with varying record counts.
- **Top Records:** Identifying frequent values and ranking data helps understand key trends.
- **Keyword Analysis:** Extracting records based on keywords assists in content filtering and segmentation.
- **Trend Insights:** Computing averages and monitoring recent updates support business intelligence strategies.

This analysis provides actionable insights for business intelligence and data-driven decision-making.
