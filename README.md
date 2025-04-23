
# 📊 Northwind Database Project

Welcome to the **Northwind Database Project!** This repository contains the SQL script required to recreate the legendary **Northwind database** — a classic dataset widely used for learning relational database design, SQL querying, and business data analysis.


---

## 🧾 What is the Northwind Database?

The **Northwind database** is a sample dataset originally created by Microsoft to simulate the day-to-day operations of a trading company. It demonstrates complex relationships between various business entities such as:

- 🛍️ Customers  
- 📦 Orders  
- 👷 Employees  
- 🚚 Shippers  
- 🧾 Invoices  
- 🏭 Suppliers  
- 🛒 Products  
- 🗂️ Categories  
- 🌍 Regions & Territories

Its normalized schema makes it perfect for learning how to model, query, and analyze business operations through SQL.

---



---

## 💡 What Can You Build with This?

This project provides a powerful foundation for:

- 📈 SQL practice exercises (joins, aggregations, subqueries, etc.)
- 📊 Interactive dashboards (Power BI, Tableau, etc.)
- 🔄 ETL pipelines and backend data projects
- 🧮 Views and stored procedures for automated reporting
- 📉 Business intelligence case studies

---


🧪 Example Queries with Visual Output

1. Top 5 Customers by Total Orders

SELECT c.ContactName, COUNT(o.OrderID) AS TotalOrders
FROM Customers c
JOIN Orders o ON c.CustomerID = o.CustomerID
GROUP BY c.ContactName
ORDER BY TotalOrders DESC
LIMIT 5;



2. Total Sales per Product Category

SELECT ct.CategoryName, SUM(od.Quantity * od.UnitPrice) AS TotalSales
FROM OrderDetails od
JOIN Products p ON od.ProductID = p.ProductID
JOIN Categories ct ON p.CategoryID = ct.CategoryID
GROUP BY ct.CategoryName
ORDER BY TotalSales DESC;



3. Monthly Sales Trends

SELECT MONTH(o.OrderDate) AS Month, SUM(od.Quantity * od.UnitPrice) AS MonthlySales
FROM Orders o
JOIN OrderDetails od ON o.OrderID = od.OrderID
GROUP BY MONTH(o.OrderDate)
ORDER BY Month;

---

Project 2
🌍 World Database Overview

The World Database is another MySQL sample dataset that contains information about:

🌍 Countries

🏙️ Cities

🗣️ Languages

It’s ideal for practicing joins, subqueries, aggregation, filtering, and geographical data analysis.
---
## 🧩 World-db

---

## 1. Count of Cities in the USA
- **Purpose**: Establish a baseline number of cities for demographic analysis in the US.
- **Insight**: Helps gauge urban density and spread.
- **Value**: Useful for national planning and logistics.
  

SELECT COUNT(ID) AS TotalCities 
FROM city 
JOIN country ON city.CountryCode = country.Code                    
WHERE country.Code = 'USA';
![image](https://github.com/user-attachments/assets/1c948415-f2bc-418d-8ed2-91abaf003413)


## 2. Country with the Highest Life Expectancy
- **Purpose**: Identify countries with top health indicators.
- **Insight**: Highlights successful healthcare and quality of life.
- **Value**: Crucial for global health policy comparison.

SELECT Name, LifeExpectancy 
FROM country 
WHERE LifeExpectancy = (SELECT MAX(LifeExpectancy) FROM country);

[View the data](./2.csv)


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

