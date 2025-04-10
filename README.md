# E-commerce Database Project - Task 3

This project involves an e-commerce database system built using MySQL. The SQL dump file (`ecommerce_task3.sql`) contains the schema and data for the system, which includes tables for products, orders, users, and more. This is part of a data analysis and reporting task using MySQL Workbench.

## 📁 File Structure

- `ecommerce_task3.sql`: SQL dump containing the full database schema and data for the e-commerce platform.

## 🧩 Database Overview

The database contains the following key tables:

- `products` - Stores information about the products listed for sale.
- `orders` - Contains customer orders.
- `orderdetails` - Contains details for each product in an order.
- `users` - Stores customer/user details.
- `productcategories` - Contains product category metadata.
- *(Additional tables may be present depending on the schema.)*

## 🛠️ Getting Started

### Prerequisites

- MySQL Server (e.g., MySQL 8.0+)
- MySQL Workbench or any other SQL client
- phpMyAdmin (optional)

### Importing the Database

1. Open **MySQL Workbench**.
2. Create a new schema (e.g., `ecommerce_db`).
3. Open the `ecommerce_task3.sql` file and run the SQL script to import the database.

### Using phpMyAdmin

1. Open phpMyAdmin.
2. Create a new database.
3. Use the **Import** tab to upload and run the `ecommerce_task3.sql` file.

## 🎯 Use Cases

This database is designed to support:

- Sales and performance analysis
- Customer segmentation
- Order management tracking
- Inventory control
- Dashboard development (e.g., in Power BI)

## 📊 Example Queries

```sql
-- Top 5 selling products
SELECT p.ProductName, SUM(od.Quantity) AS TotalSold
FROM orderdetails od
JOIN products p ON od.ProductID = p.ProductID
GROUP BY p.ProductName
ORDER BY TotalSold DESC
LIMIT 5;

-- Monthly revenue
SELECT DATE_FORMAT(o.OrderDate, '%Y-%m') AS Month, SUM(od.Quantity * od.UnitPrice) AS Revenue
FROM orders o
JOIN orderdetails od ON o.OrderID = od.OrderID
GROUP BY Month
ORDER BY Month;
