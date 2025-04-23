# 📊 Northwind Database Project

## 🧾 Overview
The Northwind Database Project is centered around a simulated trading company dataset used extensively for learning relational database concepts and performing business analysis. Originally created by Microsoft, it showcases real-world relationships in a business context involving customers, suppliers, products, orders, and more. 

## 🎯 Objectives
- To explore and understand the structure of a normalized relational database.
- To perform SQL-based data extraction and analysis.
- To generate business insights using aggregation, joins, and advanced SQL queries.
- To provide a basis for business intelligence reporting and dashboarding.

## 📚 Dataset
The Northwind database includes multiple interlinked tables that mimic the operations of a trading company:
- **Customers**
- **Orders**
- **Order Details**
- **Employees**
- **Shippers**
- **Invoices**
- **Suppliers**
- **Products**
- **Categories**
- **Regions** and **Territories**

Each table contains detailed information that supports comprehensive business analysis.

## 🛠 Tools and Technologies
- **Database**: MySQL / PostgreSQL / SQLite
- **SQL Editor**: DBeaver, pgAdmin, or MySQL Workbench
- **Data Visualization**: Power BI, Tableau (optional)
- **Languages**: SQL

## 🔄 Project Workflow
1. **Database Setup**: Install and configure Northwind database.
2. **Schema Understanding**: Analyze relationships among tables.
3. **Query Development**: Execute SQL queries to extract data.
4. **Data Analysis**: Use aggregations and joins to generate insights.
5. **Visualization (Optional)**: Display key metrics using Power BI/Tableau.
6. **Reporting**: Document findings and recommendations.
![northwind db](https://github.com/user-attachments/assets/418312d1-d6d8-4d8b-a122-443b3b4757b5)

## 📌 Key Insights
- **Top Customers**: Identified customers with the highest number of orders.
- **Revenue Drivers**: Categorized products based on revenue contribution.
- **Monthly Trends**: Analyzed sales trends over months to detect seasonality.
- **Employee Performance**: Monitored order handling per employee.
- **Shipping Performance**: Compared delivery trends across shippers.

## 📍 Findings
- The **top 5 customers** contribute significantly to the overall sales.
- **Beverages** and **Confections** are among the most profitable categories.
- Peak sales occur during the **4th and 12th months**, showing strong end-of-year demand.
- A small group of employees are responsible for the majority of the sales.
- Some shippers are consistently faster, offering a competitive advantage.

## 🧪 Example Queries with Output
### 1. Top 5 Customers by Total Orders
```sql
SELECT c.ContactName, COUNT(o.OrderID) AS TotalOrders
FROM Customers c
JOIN Orders o ON c.CustomerID = o.CustomerID
GROUP BY c.ContactName
ORDER BY TotalOrders DESC
LIMIT 5;
```

### 2. Total Sales per Product Category
```sql
SELECT ct.CategoryName, SUM(od.Quantity * od.UnitPrice) AS TotalSales
FROM OrderDetails od
JOIN Products p ON od.ProductID = p.ProductID
JOIN Categories ct ON p.CategoryID = ct.CategoryID
GROUP BY ct.CategoryName
ORDER BY TotalSales DESC;
```

### 3. Monthly Sales Trends
```sql
SELECT MONTH(o.OrderDate) AS Month, SUM(od.Quantity * od.UnitPrice) AS MonthlySales
FROM Orders o
JOIN OrderDetails od ON o.OrderID = od.OrderID
GROUP BY MONTH(o.OrderDate)
ORDER BY Month;
```

---



# 🌟 Analytical Summary of the `world_db` SQL Database

## 🌐 Overview
The `world_db` is a comprehensive SQL database that contains global data about countries, cities, and languages. It enables analysis of demographics, economies, urban planning, and more.

## 🎯 Objectives
- Analyze global city and country data.
- Extract key demographic, economic, and geographic insights.
- Support educational, investment, and governmental planning.

## 🗃️ Dataset
The dataset is composed of the following key tables:
- `city`: Includes city-level data such as population and country codes.
- `country`: Contains details like country names, population, GDP (GNP), life expectancy, etc.
- `countrylanguage`: Lists languages spoken in each country and their percentage of use.

## 🛠️ Tools and Technologies
- **MySQL**: Used to host and query the relational database.
- **SQL**: Query language to interact with the database.
- **Data Visualization Tools** (optional): For generating charts and graphs.

## 🔁 Project Workflow
1. **Database Setup**: Importing `world_db` into a SQL environment.
2. **Exploratory Data Analysis**: Running queries to understand structure and content.
3. **Analytical Queries**: Executing specific SQL queries to derive insights.
4. **Documentation**: Compiling findings, syntax, and results.
5. **Presentation**: Formatting for stakeholders or educational use.

## 🧠 Key Insights
- Cities like New York and Shanghai rank among the most populated.
- Countries such as Japan exhibit high life expectancies, signaling strong healthcare systems.
- Mid-size cities between 500,000 and 1 million population are ripe for infrastructure development.
- Cities in Europe and those with culturally significant names (like starting with 'Be') support thematic studies.

## 🔍 Findings
- **USA** has a large number of cities, confirming its urban diversity.
- **Highest Life Expectancy**: Japan or similar countries top this metric.
- **Most Populated City**: Found using population descending order.
- **Capital Cities**: Useful in both tourism and geopolitical studies.
- **High GDP Cities**: Identify wealth hubs with above-average GNP.

---

## 💡 Demographic Insights
- **Total Cities in USA**: A baseline for analyzing urban sprawl.
- **Most and Least Populated Cities**: For contrast in development.
- **Mid-size Cities**: Infrastructure and economic planning potential.

## 🏙️ Urban Distribution Patterns
- **Cities Named with 'New' or Starting with 'Be'**: Valuable for thematic travel or cultural analysis.
- **Top 10 Populous Cities**: Key targets for economic and urban development.
- **Cities in Europe**: Ideal for cultural exchange programs.

## 📈 Economic & Statistical Analysis
- **Life Expectancy & Population**: Benchmarking development and public health.
- **High GDP per Capita**: Investment hotspot identification.
- **Average Population**: Reveals size and distribution per country.

## 🏛️ Political and Administrative Data
- **Capital City Populations**: Strategic for governance and tourism.
- **Capital of Spain**: Demonstrates direct information retrieval.

## 🧠 Educational Applications
- **City Name Frequency**: Geography learning support.
- **Alphabetical City Lists**: For sorting and recognition training.

---

## 🗂️ Use Cases and Applications
| Use Case                     | Database Utility                                   |
|-----------------------------|----------------------------------------------------|
| Urban Planning              | City population size and trends                    |
| Travel & Tourism            | Capital city data, city name filters               |
| Public Health               | Life expectancy, population density                |
| Economic Development        | GDP-based region analysis                          |
| Education                   | Geography exercises, name frequency insights       |
| Business Expansion          | Identify potential city markets by population data |

---

## 🔒 Conclusion
The `world_db` SQL database is a rich resource for extracting critical global insights across sectors. Whether for analysis, education, investment, or planning, it supports a wide range of real-world applications through structured, relational queries.

![world db](https://github.com/user-attachments/assets/e1144071-7cc3-464b-8640-4ef2a7f3038f)

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
![image](https://github.com/user-attachments/assets/341c7c61-5bd1-4f9c-b6d2-b91b83f6b56a)



## 3. Cities with 'New' in the Name
- **Purpose**: Curate destinations for New Year promotions.
- **Insight**: Lists modern and historically renamed cities.
- **Value**: Supports marketing and tourism content creation.

SELECT Name 
FROM city 
WHERE Name LIKE '%New%';
![image](https://github.com/user-attachments/assets/49b2d3cc-94a7-4421-a26c-ce5c6f632f03)



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

