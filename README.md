# 📊 SQL Summary Report – Northwind Database

This document summarizes various SQL queries and techniques used to analyze the [Northwind database](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs), a classic dataset for learning relational databases.

---

## 📌 Objective

To practice SQL joins, aggregations, and grouping functions for generating business insights from the Northwind dataset using realistic scenarios such as order tracking, sales reporting, and customer profiling.

---

## 🧩 SQL Concepts Covered

### 🔗 Joins
- **INNER JOIN** between tables like `Orders` and `Customers`, `Products` and `Suppliers`, `Orders` and `Employees`.
- **LEFT JOIN** to find customers with no orders.
- **RIGHT JOIN** to include all employees, whether they handled orders or not.
- **CROSS JOIN** as an example of a full Cartesian join (all combinations).

### 📊 Aggregations & Grouping
- **COUNT, SUM** for calculating:
  - Number of customers per country
  - Number of orders per shipper
  - Total sales per product
  - Sales trends over time
  - Top 5 products by revenue

---

## 🧮 Key SQL Examples

### ✅ List Customer Names with Their Orders
```sql
SELECT Customers.CustomerName, Orders.OrderID
FROM Customers
LEFT JOIN Orders ON Customers.CustomerID = Orders.CustomerID;

## 🧠 Analytical Summary of SQL Practical Task (`world_db`)

---

## 1. Count of Cities in the USA
- **Purpose**: Establish a baseline number of cities for demographic analysis in the US.
- **Insight**: Helps gauge urban density and spread.
- **Value**: Useful for national planning and logistics.

✅ 1. Count Cities in the USA
Query:
SELECT COUNT(ID) AS TotalCities 
FROM city 
JOIN country ON city.CountryCode = country.Code 
WHERE country.Code = 'USA';

## 2. Country with the Highest Life Expectancy
- **Purpose**: Identify countries with top health indicators.
- **Insight**: Highlights successful healthcare and quality of life.
- **Value**: Crucial for global health policy comparison.

SELECT Name, LifeExpectancy 
FROM country 
WHERE LifeExpectancy = (SELECT MAX(LifeExpectancy) FROM country);

## 3. Cities with 'New' in the Name
- **Purpose**: Curate destinations for New Year promotions.
- **Insight**: Lists modern and historically renamed cities.
- **Value**: Supports marketing and tourism content creation.

SELECT Name 
FROM city 
WHERE Name LIKE '%New%';

## 4. Top 10 Most Populous Cities
- **Purpose**: Highlight major urban centers globally.
- **Insight**: Reflects global population hubs.
- **Value**: Used in urban studies, investment, and development.

SELECT * 
FROM city 
ORDER BY Population DESC 
LIMIT 10;


## 5. Cities with Population > 2 Million
- **Purpose**: Identify target cities for real estate or services.
- **Insight**: Spotlights economically significant cities.
- **Value**: Assists with investment targeting and scalability planning.

SELECT * 
FROM city 
WHERE Population > 2000000;

## 6. Cities Beginning with 'Be'
- **Purpose**: Help bloggers identify unique cities.
- **Insight**: Fun way to explore patterns in city naming.
- **Value**: Enhances storytelling and thematic travel content.

SELECT * 
FROM city 
WHERE Name LIKE 'Be%';

## 7. Cities with Population 500k–1M
- **Purpose**: Identify mid-sized cities for infrastructure planning.
- **Insight**: Focuses on growing but manageable urban areas.
- **Value**: Supports regional planning and development prioritization.

SELECT * 
FROM city 
WHERE Population BETWEEN 500000 AND 1000000;

## 8. Cities Sorted Alphabetically
- **Purpose**: Provide a reference for geography education.
- **Insight**: Simplifies city lookup and navigation.
- **Value**: Aids teaching and presentation preparation.

SELECT * 
FROM city 
ORDER BY Name ASC;

## 9. Most Populated City
- **Purpose**: Locate the densest city by population.
- **Insight**: Reveals top-tier urban agglomeration.
- **Value**: Essential for mega-city policy, infrastructure, and analysis.

SELECT Name, Population 
FROM city 
ORDER BY Population DESC 
LIMIT 1;

## 10. City Name Frequency
- **Purpose**: Count recurring city names globally.
- **Insight**: Identifies naming trends and duplicates.
- **Value**: Useful in data cleansing and cultural studies.

SELECT Name, COUNT(*) AS NoOfOccurrence 
FROM city 
GROUP BY Name 
HAVING COUNT(*) > 1 
ORDER BY Name;

## 11. City with Lowest Population
- **Purpose**: Find the least populated urban entity.
- **Insight**: Represents anomalies or special jurisdictions.
- **Value**: Important for niche research and case studies.

SELECT Name, Population 
FROM city 
ORDER BY Population ASC 
LIMIT 1;

## 12. Country with Largest Population
- **Purpose**: Determine the most populous country.
- **Insight**: Aligns with economic and geopolitical power.
- **Value**: Used in strategic analysis and resource allocation.

SELECT Name, Population 
FROM country 
ORDER BY Population DESC 
LIMIT 1;

## 13. Capital of Spain
- **Purpose**: Retrieve key political/geographical data.
- **Insight**: Validates database integrity and relations.
- **Value**: Assists in itinerary planning and education.

SELECT Name, Capital 
FROM country 
WHERE Name = 'Spain';

## 14. Cities in Europe
- **Purpose**: Build a list of European urban locations.
- **Insight**: Supports cross-border collaboration and studies.
- **Value**: Ideal for programs like Erasmus or cultural exchange.

SELECT c.Name AS City, cn.Name AS Country 
FROM city c 
JOIN country cn ON c.CountryCode = cn.Code 
WHERE cn.Continent = 'Europe';

## 15. Average Population by Country
- **Purpose**: Evaluate urban distribution at national level.
- **Insight**: Countries with high averages may have few, large cities.
- **Value**: Useful for national urban planning and investment focus.

SELECT Name, AVG(Population) AS AveragePopulation 
FROM country 
GROUP BY Name;

## 16. Capital Cities Population Comparison
- **Purpose**: Compare capitals’ population sizes.
- **Insight**: Some capitals are symbolic vs. economic centers.
- **Value**: Informs governance and decentralization discussions.

SELECT cn.Name AS Country, c.Name AS Capital, c.Population 
FROM city c 
JOIN country cn ON c.ID = cn.Capital 
ORDER BY c.Population DESC;

## 17. Countries with Lowest Population
- **Purpose**: Find sparsely populated countries.
- **Insight**: Highlights microstates or remote regions.
- **Value**: Useful for development aid, tourism, or ecological study.

SELECT Name, Population 
FROM country 
WHERE Population = (SELECT MIN(Population) FROM country);

## 18. Cities with High GDP per Capita
- **Purpose**: Identify wealthy cities for economic planning.
- **Insight**: Points to potential for investment and luxury markets.
- **Value**: Informs business expansion and global market entry.

SELECT c.Name AS City, cn.Name AS Country, cn.GNP AS HighGNP 
FROM city c 
JOIN country cn ON c.CountryCode = cn.Code 
WHERE cn.GNP > (SELECT AVG(GNP) FROM country);

## 19. Cities Ranked 31–40 by Population
- **Purpose**: Extend population analysis beyond the top 30.
- **Insight**: Reveals emerging hubs and secondary cities.
- **Value**: Enhances depth of urban demographic research.

WITH citypop AS (
    SELECT Name, Population, 
           ROW_NUMBER() OVER (ORDER BY Population DESC) AS RN 
    FROM city
)
SELECT Name, Population, RN 
FROM citypop 
WHERE RN BETWEEN 31 AND 40;


---

