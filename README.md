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
- **CROSS JOIN** as an example of a full cartesian join (all combinations).

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
