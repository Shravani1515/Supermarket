# Supermarket Management System

This is a desktop-based Supermarket Management System built using Java Swing and MySQL. 
It is designed to help administrators and staff efficiently manage product inventory, categories, and billing operations in a retail environment.

## Project Overview

This system includes the following major modules:

1. **Admin Login**
2. **Product Management**
3. **Category Management**
4. **Billing System**

Each module is accessible via a clean and user-friendly GUI built using Java Swing. The database is connected via JDBC and runs on MySQL.

## Key Features

### 1. Admin Panel
- Secure login screen for administrators
- Only authenticated users can access system functionality

### 2. Product Management
- Add new products (name, price, quantity, category)
- Update and delete existing products
- View product list with search and filter options

### 3. Category Management
- Add, update, delete categories
- Associate categories with products

### 4. Billing System
- Add multiple products to a bill with quantity selection
- Auto calculation of price, subtotal, tax (GST), and total
- Deduct stock quantity on successful purchase
- Generate printable customer bill

## Technologies Used

- **Frontend GUI**: Java Swing
- **Backend**: Java + JDBC
- **Database**: MySQL
- **IDE**: NetBeans / IntelliJ IDEA / VS Code
- **JARs Used**: MySQL Connector/J

## MySQL Database Setup

### Step 1: Create Database

CREATE DATABASE supermarket;
USE supermarket;

Step 2: Create Tables
Categories Table
CREATE TABLE categories (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL
);

Products Table
CREATE TABLE products (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    category_id INT,
    price DECIMAL(10,2),
    quantity INT,
    FOREIGN KEY (category_id) REFERENCES categories(id)
);

Admin Table
CREATE TABLE admin (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) NOT NULL,
    password VARCHAR(100) NOT NULL
);
Bills Table
sql
Copy
Edit
CREATE TABLE bills (
    id INT AUTO_INCREMENT PRIMARY KEY,
    date DATETIME DEFAULT CURRENT_TIMESTAMP,
    total_amount DECIMAL(10,2)
);
Note: Create table as per requirements.

Step 3: Insert Sample Admin (Optional)
INSERT INTO admin (username, password) VALUES ('admin', 'admin123');
You can use MD5() or SHA() to hash passwords for better security.

How to Run:
Open the project in your Java IDE.
Ensure the MySQL JDBC driver .jar is added to your classpath.
Configure your DB connection in DBConnection.java:

String url = "jdbc:mysql://localhost:3306/supermarket";
String user = "root";
String password = "";
Compile and run Main.java.

Use admin login → manage products and categories → generate bills.
