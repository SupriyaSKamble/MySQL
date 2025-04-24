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
- **Database**: MySQL
- **SQL Editor**:  MySQL Workbench
- **Data Visualization**: Power BI, Tableau
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



# 🌟  `world_db` SQL Database Project

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

## 🛠 Tools and Technologies
- **Database**: MySQL
- **SQL Editor**:  MySQL Workbench
- **Data Visualization**: Power BI, Tableau
- **Languages**: SQL

## 🔁 Project Workflow
1. **Database Setup**: Importing `world_db` into a SQL environment.
2. **Exploratory Data Analysis**: Running queries to understand structure and content.
3. **Analytical Queries**: Executing specific SQL queries to derive insights.
4. **Documentation**: Compiling findings, syntax, and results.
5. **Presentation**: Formatting for stakeholders or educational use.

   
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

![image](https://github.com/user-attachments/assets/cbdc0a79-cbe6-4661-8925-1fcc8f0c85a5)




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

![image](https://github.com/user-attachments/assets/9298cf9a-8ac7-4146-a3ba-5d2752f0f6ae)



## 5. Cities with Population > 2 Million
- **Purpose**: Identify target cities for real estate or services.
- **Insight**: Spotlights economically significant cities.
- **Value**: Assists with investment targeting and scalability planning.

SELECT * 
FROM city 
WHERE Population > 2000000;

![image](https://github.com/user-attachments/assets/fb562cd9-4e78-4540-b8b4-10a253da3837)


## 6. Cities Beginning with 'Be'
- **Purpose**: Help bloggers identify unique cities.
- **Insight**: Fun way to explore patterns in city naming.
- **Value**: Enhances storytelling and thematic travel content.

SELECT * 
FROM city 
WHERE Name LIKE 'Be%';

![image](https://github.com/user-attachments/assets/25ff4660-fa3c-4844-8a81-330e32609bc3)


## 7. Cities with Population 500k–1M
- **Purpose**: Identify mid-sized cities for infrastructure planning.
- **Insight**: Focuses on growing but manageable urban areas.
- **Value**: Supports regional planning and development prioritization.

SELECT * 
FROM city 
WHERE Population BETWEEN 500000 AND 1000000;

![image](https://github.com/user-attachments/assets/f3e55e5b-3c59-4cd9-80d7-623bb7a44e9f)


## 8. Cities Sorted Alphabetically
- **Purpose**: Provide a reference for geography education.
- **Insight**: Simplifies city lookup and navigation.
- **Value**: Aids teaching and presentation preparation.

SELECT * 
FROM city 
ORDER BY Name ASC;

![image](https://github.com/user-attachments/assets/ec7e1eec-3b73-4199-a188-253ac29da34c)

## 9. Most Populated City
- **Purpose**: Locate the densest city by population.
- **Insight**: Reveals top-tier urban agglomeration.
- **Value**: Essential for mega-city policy, infrastructure, and analysis.

SELECT Name, Population 
FROM city 
ORDER BY Population DESC 
LIMIT 1;

![image](https://github.com/user-attachments/assets/9e1f00f7-fe9c-43ec-9852-953624ce0374)


## 10. City Name Frequency
- **Purpose**: Count recurring city names globally.
- **Insight**: Identifies naming trends and duplicates.
- **Value**: Useful in data cleansing and cultural studies.

SELECT Name, COUNT(*) AS NoOfOccurrence 
FROM city 
GROUP BY Name 
HAVING COUNT(*) > 1 
ORDER BY Name;

![image](https://github.com/user-attachments/assets/1ec0fe20-7632-4e67-ad22-64e4e7eea9ab)

## 11. City with Lowest Population
- **Purpose**: Find the least populated urban entity.
- **Insight**: Represents anomalies or special jurisdictions.
- **Value**: Important for niche research and case studies.

SELECT Name, Population 
FROM city 
ORDER BY Population ASC 
LIMIT 1;

![image](https://github.com/user-attachments/assets/6e625254-6017-4320-88ff-845bfbc55485)

## 12. Country with Largest Population
- **Purpose**: Determine the most populous country.
- **Insight**: Aligns with economic and geopolitical power.
- **Value**: Used in strategic analysis and resource allocation.

SELECT Name, Population 
FROM country 
ORDER BY Population DESC 
LIMIT 1;

![image](https://github.com/user-attachments/assets/ad8cfa06-56ef-438a-a319-31cb43e5e1a7)

## 13. Capital of Spain
- **Purpose**: Retrieve key political/geographical data.
- **Insight**: Validates database integrity and relations.
- **Value**: Assists in itinerary planning and education.

SELECT Name, Capital 
FROM country 
WHERE Name = 'Spain';


![image](https://github.com/user-attachments/assets/b9096fda-7170-4479-a01b-3ae7e92927a6)

## 14. Cities in Europe
- **Purpose**: Build a list of European urban locations.
- **Insight**: Supports cross-border collaboration and studies.
- **Value**: Ideal for programs like Erasmus or cultural exchange.

SELECT c.Name AS City, cn.Name AS Country 
FROM city c 
JOIN country cn ON c.CountryCode = cn.Code 
WHERE cn.Continent = 'Europe';

![image](https://github.com/user-attachments/assets/6cba9e0a-7118-4bbb-b7ac-15b2ac6c89a3)

## 15. Average Population by Country
- **Purpose**: Evaluate urban distribution at national level.
- **Insight**: Countries with high averages may have few, large cities.
- **Value**: Useful for national urban planning and investment focus.

SELECT Name, AVG(Population) AS AveragePopulation 
FROM country 
GROUP BY Name;

![image](https://github.com/user-attachments/assets/542d8fc9-e91d-4e19-811a-10ddd8202d1f)


## 16. Capital Cities Population Comparison
- **Purpose**: Compare capitals’ population sizes.
- **Insight**: Some capitals are symbolic vs. economic centers.
- **Value**: Informs governance and decentralization discussions.

SELECT cn.Name AS Country, c.Name AS Capital, c.Population 
FROM city c 
JOIN country cn ON c.ID = cn.Capital 
ORDER BY c.Population DESC;

![image](https://github.com/user-attachments/assets/38307721-ebf7-477f-a603-f6f4fc07a10a)

## 17. Countries with Lowest Population
- **Purpose**: Find sparsely populated countries.
- **Insight**: Highlights microstates or remote regions.
- **Value**: Useful for development aid, tourism, or ecological study.

SELECT Name, Population 
FROM country 
WHERE Population = (SELECT MIN(Population) FROM country);

![image](https://github.com/user-attachments/assets/de1343de-dae3-4468-84bf-698b1901243c)

## 18. Cities with High GDP per Capita
- **Purpose**: Identify wealthy cities for economic planning.
- **Insight**: Points to potential for investment and luxury markets.
- **Value**: Informs business expansion and global market entry.

SELECT c.Name AS City, cn.Name AS Country, cn.GNP AS HighGNP 
FROM city c 
JOIN country cn ON c.CountryCode = cn.Code 
WHERE cn.GNP > (SELECT AVG(GNP) FROM country);

![image](https://github.com/user-attachments/assets/3c7ff179-1800-4b67-be0a-62dfa914e25b)

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

![image](https://github.com/user-attachments/assets/e8bf1b0f-e474-482d-972a-31805e447a09)

![world db](https://github.com/user-attachments/assets/e1144071-7cc3-464b-8640-4ef2a7f3038f)
## 🧠 Key Insights
- Cities like Mumbai and Shanghai rank among the most populated.
- Countries such as Arrora exhibit high life expectancies, signaling strong healthcare systems.
- Mid-size cities between 500,000 and 1 million population are fit for infrastructure development.
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



---

---

