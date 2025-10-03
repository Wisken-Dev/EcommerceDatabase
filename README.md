# 📚 Database Management System Assignment

## 🎯 Objective
The objective of this assignment is to **design and implement a relational database** using **MySQL** for a real-world use case.  
I chose an **E-commerce Store** as the case study, focusing on managing **users, products, orders, and order items**.

## 🗂 Database Schema
The database is named **`ecommerce_db`** and includes the following tables:

1. **users**  
   - Stores customer login details and basic account info.  
   - Constraints: `PRIMARY KEY (user_id)`, `UNIQUE (email)`.  

2. **products**  
   - Stores product catalog information (name, SKU, price, etc.).  
   - Constraints: `PRIMARY KEY (product_id)`, `UNIQUE (sku)`, `CHECK (price >= 0)`.  

3. **orders**  
   - Represents a purchase order made by a user.  
   - Relationships: One user → many orders.  
   - Constraints: `PRIMARY KEY (order_id)`, `FOREIGN KEY (user_id)` references `users`.  

4. **order_items**  
   - Stores items that belong to an order (product, quantity, unit price).  
   - Relationships: One order → many items; many items → reference products.  
   - Constraints: `PRIMARY KEY (order_item_id)`, `FOREIGN KEY (order_id)`, `FOREIGN KEY (product_id)`.  

## 🔑 Relationships
- **One-to-Many**: A user can place many orders (`users → orders`).  
- **One-to-Many**: An order can contain many items (`orders → order_items`).  
- **Many-to-One**: Each order item references a single product (`order_items → products`).  

## 📝 Constraints
- **PRIMARY KEY**: Ensures each record is uniquely identifiable.  
- **FOREIGN KEY**: Enforces referential integrity between related tables.  
- **UNIQUE**: Prevents duplicate emails and product SKUs.  
- **NOT NULL**: Ensures required fields must be provided.  
- **CHECK**: Ensures valid data ranges (e.g., `price >= 0`, `quantity > 0`).  

## ⚙️ How to Run
1. Save the provided SQL file as `ecommerce_minimal.sql`.  
2. Open MySQL and execute:  
   ```bash
   mysql -u root -p < ecommerce_minimal.sql
