# Supermarket-Inventory-management-and-billing-system-java
Supermarket Management System 🛒
A full-featured desktop-based Supermarket Management System built using Java Swing and MySQL. Designed with an attractive UI and animations, it includes features like product management, billing, login/signup, and more.

 Features
User login and signup system with MySQL integration
Product management: add, update, delete, and view products
Billing panel with live cart generation and total calculation
Interactive sidebar with icons and glowing animation on hover
Modern dark UI using a professional color palette (#0A1128, #001F54, #034078, #1282A2, #FEFCFB)
Organized using MVC structure: models, dao, ui packages
 Project Structure
src/
├── dao/             # Database Access Objects (UserDAO, ProductDAO)
├── db/              # DBConnection file for MySQL
├── icons/           # PNG icons used in the UI (home, billing, logout, etc.)
├── models/          # Product and User classes
└── ui/              # All user interface screens and windows
🧑‍💻 Technologies Used
Java 11
Swing for GUI
MySQL for backend database
IntelliJ IDEA (Recommended IDE)
image
🛠️ Setup Instructions
Clone this repository
git clone(https://github.com/Poojaasaste012719/Supermarket-Inventory-management-and-billing-system-java/)
Open the project in IntelliJ IDEA or any Java IDE

Make sure MySQL is installed and running

Create a database named supermarket and import the required tables

CREATE DATABASE IF NOT EXISTS supermarket;
USE supermarket;

CREATE TABLE IF NOT EXISTS users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    username VARCHAR(50) NOT NULL UNIQUE,
    password VARCHAR(100) NOT NULL
);

CREATE TABLE IF NOT EXISTS products (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    category VARCHAR(50),
    quantity INT DEFAULT 0,
    price DOUBLE NOT NULL
);

CREATE TABLE IF NOT EXISTS sales (
    id INT PRIMARY KEY AUTO_INCREMENT,
    product_id INT,
    quantity_sold INT,
    total_price DOUBLE,
    sale_date DATETIME DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (product_id) REFERENCES products(id)
        ON DELETE CASCADE
        ON UPDATE CASCADE
);

INSERT INTO products (name, category, quantity, price) VALUES
('Parle-G Biscuits', 'Snacks', 100, 5.00),
('Dairy Milk Chocolate', 'Confectionery', 50, 30.00),
('Dettol Soap', 'Personal Care', 80, 25.00),
('Aashirvaad Atta', 'Grocery', 40, 200.00);

INSERT INTO users (username, password)
VALUES ('admin', 'admin123');  -- You can change this as needed
Update your database credentials in the DBConnection.java file

Run the application from MainWindow.java
