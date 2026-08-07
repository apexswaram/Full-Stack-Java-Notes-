# Project 
# ShopEasy — E-Commerce Product Management System
### Spring MVC + MySQL + HTML/CSS + Apache Tomcat

---

## Complete Project Structure

```
EcommerceApp/
├── src/main/java/com/ecommerce/
│   ├── controllers/
│   │   ├── UserController.java        → Register, Login, Logout
│   │   ├── ProductController.java     → View products, Admin CRUD
│   │   ├── CategoryController.java    → Admin category management
│   │   └── CartController.java        → Cart, Checkout, Orders, Dashboard
│   ├── dao/
│   │   ├── UserDAO.java               → register(), login(), emailExists()
│   │   ├── ProductDAO.java            → addProduct(), getAllProducts(), getById(), update(), delete()
│   │   ├── CategoryDAO.java           → addCategory(), getAllCategories(), delete()
│   │   ├── CartDAO.java               → addToCart(), getCartByUser(), removeFromCart(), clearCart()
│   │   └── OrderDAO.java              → placeOrder(), getOrdersByUser(), getAllOrders(), stats
│   └── models/
│       ├── User.java
│       ├── Product.java
│       ├── Category.java
│       ├── Cart.java
│       └── Order.java
├── src/main/webapp/
│   ├── WEB-INF/
│   │   ├── pages/
│   │   │   ├── index.jsp              → Home - product listing with filters
│   │   │   ├── register.jsp           → User registration form
│   │   │   ├── login.jsp              → Login form
│   │   │   ├── product-detail.jsp     → Single product detail view
│   │   │   ├── cart.jsp               → Shopping cart page
│   │   │   ├── checkout.jsp           → Order confirmation page
│   │   │   ├── order-success.jsp      → Order placed success page
│   │   │   ├── my-orders.jsp          → User order history
│   │   │   ├── admin-dashboard.jsp    → Admin stats dashboard
│   │   │   ├── manage-products.jsp    → Admin product list
│   │   │   ├── add-product.jsp        → Admin add product form
│   │   │   ├── edit-product.jsp       → Admin edit product form
│   │   │   ├── manage-categories.jsp  → Admin category list
│   │   │   ├── add-category.jsp       → Admin add category form
│   │   │   └── admin-orders.jsp       → Admin all orders view
│   │   ├── web.xml
│   │   └── spring-servlet.xml
│   └── resources/
│       ├── css/
│       │   └── style.css
│       └── images/                    ← Put product images here
├── database/
│   └── ecommerce.sql
└── pom.xml
```

---

## URL Mapping — All Routes

### User Routes:
| URL | Method | Controller | What it does |
|-----|--------|-----------|--------------|
| `/` | GET | UserController | Redirects to /products |
| `/products` | GET | ProductController | Home page — all products |
| `/products?categoryId=1` | GET | ProductController | Filter by category |
| `/product/{id}` | GET | ProductController | Product detail page |
| `/register` | GET | UserController | Show register form |
| `/register` | POST | UserController | Save new user |
| `/login` | GET | UserController | Show login form |
| `/logincheck` | POST | UserController | Validate credentials |
| `/logout` | GET | UserController | Destroy session |
| `/cart` | GET | CartController | View cart |
| `/cart/add/{productId}` | GET | CartController | Add product to cart |
| `/cart/remove/{cartId}` | GET | CartController | Remove item from cart |
| `/checkout` | GET | CartController | Checkout page |
| `/place-order` | POST | CartController | Place order |
| `/my-orders` | GET | CartController | User order history |

### Admin Routes (all require ADMIN role):
| URL | Method | What it does |
|-----|--------|--------------|
| `/admin/dashboard` | GET | Stats dashboard |
| `/admin/products` | GET | All products table |
| `/admin/add-product` | GET | Add product form |
| `/admin/save-product` | POST | Save new product |
| `/admin/edit-product/{id}` | GET | Edit form pre-filled |
| `/admin/update-product` | POST | Update product |
| `/admin/delete-product/{id}` | GET | Delete product |
| `/admin/categories` | GET | All categories table |
| `/admin/add-category` | GET | Add category form |
| `/admin/save-category` | POST | Save new category |
| `/admin/delete-category/{id}` | GET | Delete category |
| `/admin/orders` | GET | All orders table |

---

## Setup Instructions — Step by Step

### Step 1: Database Setup
```sql
-- Open MySQL Workbench or MySQL CLI
-- Run the file: database/ecommerce.sql
-- This creates database, all tables, and sample data
```

### Step 2: Update MySQL password in spring-servlet.xml
```xml
<property name="password" value="YOUR_MYSQL_PASSWORD_HERE" />
```

### Step 3: Create Maven project in Eclipse
- File → New → Maven Project
- groupId: com.ecommerce
- artifactId: EcommerceApp
- packaging: war

### Step 4: Copy all files into the project

### Step 5: Maven → Update Project
- Right click project → Maven → Update Project → OK

### Step 6: Add Tomcat server
- Window → Preferences → Server → Runtime Environments → Add Tomcat 9

### Step 7: Run on Server
- Right click project → Run As → Run on Server
- Open browser: http://localhost:8080/EcommerceApp/

---

## Test Credentials

| Role | Email | Password |
|------|-------|----------|
| Admin | admin@shop.com | admin123 |
| User | rahul@gmail.com | 1234 |

---

## Features Demonstrated (Spring Concepts Used)

| Feature | Spring Concept |
|---------|---------------|
| Login/Logout | HttpSession |
| Register | @ModelAttribute, @PostMapping |
| Product listing | @GetMapping, Model, JSTL c:forEach |
| Category filter | @RequestParam |
| Product detail | @PathVariable |
| Add to cart | HttpSession for user id |
| Place order | Multiple DAO operations |
| Admin security | Session role check in every controller |
| Category dropdown | Model with List passed to JSP |
| Edit form pre-fill | queryForObject + hidden field |
| Stock reduction | Update query after order |
| Cart total | SQL SUM aggregate function |

---

## What Students Learn From This Project

1. Full layered architecture — Controller → DAO → MySQL
2. Session management — Login, Logout, Role-based access
3. SQL JOIN queries — Products with category name
4. @ModelAttribute for complex form binding
5. @PathVariable for URL-based operations
6. Redirect vs Forward
7. JSTL c:forEach, c:choose, c:when, c:if
8. Expression Language ${} for displaying data
9. CSS Grid and Flexbox for responsive layout
10. Real-world database design with foreign keys

---
# Full Code 
---
## SQL 
```sql 

CREATE DATABASE IF NOT EXISTS ecommerce;
USE ecommerce;

CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    fullname VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    password VARCHAR(100) NOT NULL,
    address VARCHAR(255),
    role VARCHAR(20) DEFAULT 'USER'
);

CREATE TABLE categories (
    id INT AUTO_INCREMENT PRIMARY KEY,
    category_name VARCHAR(100) NOT NULL,
    description VARCHAR(255)
);

CREATE TABLE products (
    id INT AUTO_INCREMENT PRIMARY KEY,
    product_name VARCHAR(150) NOT NULL,
    description VARCHAR(500),
    price DOUBLE NOT NULL,
    stock INT NOT NULL,
    image_url VARCHAR(255),
    category_id INT,
    FOREIGN KEY (category_id) REFERENCES categories(id)
);

CREATE TABLE cart (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT NOT NULL,
    product_id INT NOT NULL,
    quantity INT NOT NULL DEFAULT 1,
    FOREIGN KEY (user_id) REFERENCES users(id),
    FOREIGN KEY (product_id) REFERENCES products(id)
);

CREATE TABLE orders (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT NOT NULL,
    total_amount DOUBLE NOT NULL,
    order_date DATETIME DEFAULT CURRENT_TIMESTAMP,
    status VARCHAR(50) DEFAULT 'PLACED',
    FOREIGN KEY (user_id) REFERENCES users(id)
);

CREATE TABLE order_items (
    id INT AUTO_INCREMENT PRIMARY KEY,
    order_id INT NOT NULL,
    product_id INT NOT NULL,
    quantity INT NOT NULL,
    price DOUBLE NOT NULL,
    FOREIGN KEY (order_id) REFERENCES orders(id),
    FOREIGN KEY (product_id) REFERENCES products(id)
);

-- Sample Data
INSERT INTO users (fullname, email, password, address, role) VALUES
('Admin User', 'admin@shop.com', 'admin123', 'Pune', 'ADMIN'),
('Rahul Kumar', 'rahul@gmail.com', '1234', 'Mumbai', 'USER');

INSERT INTO categories (category_name, description) VALUES
('Electronics', 'Mobiles, laptops, gadgets'),
('Clothing', 'Shirts, jeans, shoes'),
('Books', 'Educational and fiction books');

INSERT INTO products (product_name, description, price, stock, image_url, category_id) VALUES
('Smartphone X100', 'Latest 5G smartphone with 128GB storage', 15999, 50, 'phone.jpg', 1),
('Laptop Pro 15', 'Intel i5, 8GB RAM, 512GB SSD', 45999, 20, 'laptop.jpg', 1),
('Men T-Shirt', 'Cotton round neck t-shirt', 499, 100, 'tshirt.jpg', 2),
('Running Shoes', 'Lightweight sports shoes', 1999, 60, 'shoes.jpg', 2),
('Java Programming Book', 'Complete guide to Java for beginners', 599, 30, 'javabook.jpg', 3),
('Spring Framework Guide', 'Learn Spring MVC step by step', 799, 25, 'springbook.jpg', 3);
```
---
##  spring-servlet.xml
```xml 
<?xml version="1.0" encoding="UTF-8"?>
<beans
    xmlns="http://www.springframework.org/schema/beans"
    xmlns:mvc="http://www.springframework.org/schema/mvc"
    xmlns:context="http://www.springframework.org/schema/context"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="
        http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/context
        http://www.springframework.org/schema/context/spring-context.xsd
        http://www.springframework.org/schema/mvc
        http://www.springframework.org/schema/mvc/spring-mvc.xsd">

    <context:component-scan base-package="com.ecommerce.controllers" />

    <mvc:resources mapping="/resources/**" location="/resources/" />

    <bean class="org.springframework.web.servlet.view.InternalResourceViewResolver">
        <property name="prefix" value="/WEB-INF/pages/" />
        <property name="suffix" value=".jsp" />
    </bean>

    <!-- DataSource - UPDATE PASSWORD BEFORE RUNNING -->
    <bean id="dataSource"
        class="org.springframework.jdbc.datasource.DriverManagerDataSource">
        <property name="driverClassName" value="com.mysql.cj.jdbc.Driver" />
        <property name="url" value="jdbc:mysql://localhost:3306/ecommerce" />
        <property name="username" value="root" />
        <property name="password" value="Subbu@2004" />
    </bean>

    <bean id="jdbcTemplate"
        class="org.springframework.jdbc.core.JdbcTemplate">
        <property name="dataSource" ref="dataSource" />
    </bean>

    <bean id="userDAO" class="com.ecommerce.dao.UserDAO">
        <property name="template" ref="jdbcTemplate" />
    </bean>

    <bean id="categoryDAO" class="com.ecommerce.dao.CategoryDAO">
        <property name="template" ref="jdbcTemplate" />
    </bean>

    <bean id="productDAO" class="com.ecommerce.dao.ProductDAO">
        <property name="template" ref="jdbcTemplate" />
    </bean>

    <bean id="cartDAO" class="com.ecommerce.dao.CartDAO">
        <property name="template" ref="jdbcTemplate" />
    </bean>

    <bean id="orderDAO" class="com.ecommerce.dao.OrderDAO">
        <property name="template" ref="jdbcTemplate" />
    </bean>

    <mvc:annotation-driven />

</beans>
```
---

## web.xml
```xml 
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee" version="3.1">

    <servlet>
        <servlet-name>spring</servlet-name>
        <servlet-class>
            org.springframework.web.servlet.DispatcherServlet
        </servlet-class>
        <load-on-startup>1</load-on-startup>
    </servlet>

    <servlet-mapping>
        <servlet-name>spring</servlet-name>
        <url-pattern>/</url-pattern>
    </servlet-mapping>

    <session-config>
        <session-timeout>30</session-timeout>
    </session-config>

</web-app>
```
---
## pom.xml
```xml 
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
    https://maven.apache.org/xsd/maven-4.0.0.xsd">

    <modelVersion>4.0.0</modelVersion>
    <groupId>com.ecommerce</groupId>
    <artifactId>EcommerceApp</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <packaging>war</packaging>
    <name>ShopEasy Ecommerce App</name>

    <dependencies>

        <!-- Spring MVC -->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-webmvc</artifactId>
            <version>5.3.32</version>
        </dependency>

        <!-- Spring JDBC -->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-jdbc</artifactId>
            <version>5.3.32</version>
        </dependency>

        <!-- Servlet API — THIS IS THE FIX — version 4.0.1 for Tomcat 9 -->
        <dependency>
            <groupId>javax.servlet</groupId>
            <artifactId>javax.servlet-api</artifactId>
            <version>4.0.1</version>
            <scope>provided</scope>
        </dependency>

        <!-- JSP API — THIS IS THE FIX — needed for PageContext JspException errors -->
        <dependency>
            <groupId>javax.servlet.jsp</groupId>
            <artifactId>javax.servlet.jsp-api</artifactId>
            <version>2.3.3</version>
            <scope>provided</scope>
        </dependency>

        <!-- JSTL — THIS IS THE FIX — use both spec and impl together -->
        <dependency>
            <groupId>javax.servlet</groupId>
            <artifactId>jstl</artifactId>
            <version>1.2</version>
        </dependency>

        <!-- MySQL Connector -->
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>8.0.33</version>
        </dependency>

    </dependencies>

    <build>
        <finalName>EcommerceApp</finalName>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.11.0</version>
                <configuration>
                    <source>17</source>
                    <target>17</target>
                </configuration>
            </plugin>
        </plugins>
    </build>

</project>

```
---

### Cart.java
```java
package com.ecommerce.models;
public class Cart {
    private int id;
    private int userId;
    private int productId;
    private int quantity;
    private String productName;
    private double price;
    private String imageUrl;
    public int getId() { return id; }
    public int getUserId() { return userId; }
    public int getProductId() { return productId; }
    public int getQuantity() { return quantity; }
    public String getProductName() { return productName; }
    public double getPrice() { return price; }
    public String getImageUrl() { return imageUrl; }
    public void setId(int id) { this.id = id; }
    public void setUserId(int userId) { this.userId = userId; }
    public void setProductId(int productId) { this.productId = productId; }
    public void setQuantity(int quantity) { this.quantity = quantity; }
    public void setProductName(String productName) { this.productName = productName; }
    public void setPrice(double price) { this.price = price; }
    public void setImageUrl(String imageUrl) { this.imageUrl = imageUrl; }
    public double getTotalPrice() { return price * quantity; }
}
```
---

## Category.java
```java

package com.ecommerce.models;
public class Category {
    private int id;
    private String categoryName;
    private String description;
    public int getId() { return id; }
    public String getCategoryName() { return categoryName; }
    public String getDescription() { return description; }
    public void setId(int id) { this.id = id; }
    public void setCategoryName(String categoryName) { this.categoryName = categoryName; }
    public void setDescription(String description) { this.description = description; }
}

```
---

# Order.java
```java
package com.ecommerce.models;
import java.util.Date;
public class Order {
    private int id;
    private int userId;
    private double totalAmount;
    private Date orderDate;
    private String status;
    public int getId() { return id; }
    public int getUserId() { return userId; }
    public double getTotalAmount() { return totalAmount; }
    public Date getOrderDate() { return orderDate; }
    public String getStatus() { return status; }
    public void setId(int id) { this.id = id; }
    public void setUserId(int userId) { this.userId = userId; }
    public void setTotalAmount(double totalAmount) { this.totalAmount = totalAmount; }
    public void setOrderDate(Date orderDate) { this.orderDate = orderDate; }
    public void setStatus(String status) { this.status = status; }
}
```
---
## Product.java
```java
package com.ecommerce.models;
public class Product {
    private int id;
    private String productName;
    private String description;
    private double price;
    private int stock;
    private String imageUrl;
    private int categoryId;
    private String categoryName;
    public int getId() { return id; }
    public String getProductName() { return productName; }
    public String getDescription() { return description; }
    public double getPrice() { return price; }
    public int getStock() { return stock; }
    public String getImageUrl() { return imageUrl; }
    public int getCategoryId() { return categoryId; }
    public String getCategoryName() { return categoryName; }
    public void setId(int id) { this.id = id; }
    public void setProductName(String productName) { this.productName = productName; }
    public void setDescription(String description) { this.description = description; }
    public void setPrice(double price) { this.price = price; }
    public void setStock(int stock) { this.stock = stock; }
    public void setImageUrl(String imageUrl) { this.imageUrl = imageUrl; }
    public void setCategoryId(int categoryId) { this.categoryId = categoryId; }
    public void setCategoryName(String categoryName) { this.categoryName = categoryName; }
}

```
---

## Users.java
```java
package com.ecommerce.models;
public class User {
    private int id;
    private String fullname;
    private String email;
    private String password;
    private String address;
    private String role;
    public int getId() { return id; }
    public String getFullname() { return fullname; }
    public String getEmail() { return email; }
    public String getPassword() { return password; }
    public String getAddress() { return address; }
    public String getRole() { return role; }
    public void setId(int id) { this.id = id; }
    public void setFullname(String fullname) { this.fullname = fullname; }
    public void setEmail(String email) { this.email = email; }
    public void setPassword(String password) { this.password = password; }
    public void setAddress(String address) { this.address = address; }
    public void setRole(String role) { this.role = role; }
}
```

## CartDAO.java
```java 
package com.ecommerce.dao;
import java.util.List;
import org.springframework.jdbc.core.JdbcTemplate;
import com.ecommerce.models.Cart;
public class CartDAO {
    JdbcTemplate template;
    public void setTemplate(JdbcTemplate template) { this.template = template; }
    public boolean isProductInCart(int userId, int productId) {
        int count = template.queryForObject("SELECT COUNT(*) FROM cart WHERE user_id=? AND product_id=?", Integer.class, userId, productId);
        return count > 0;
    }
    public void addToCart(int userId, int productId, int quantity) {
        if (isProductInCart(userId, productId)) {
            template.update("UPDATE cart SET quantity=quantity+? WHERE user_id=? AND product_id=?", quantity, userId, productId);
        } else {
            template.update("INSERT INTO cart(user_id,product_id,quantity) VALUES(?,?,?)", userId, productId, quantity);
        }
    }
    public List<Cart> getCartByUser(int userId) {
        String sql = "SELECT c.*,p.product_name,p.price,p.image_url FROM cart c JOIN products p ON c.product_id=p.id WHERE c.user_id=?";
        return template.query(sql, (rs, rowNum) -> {
            Cart c = new Cart();
            c.setId(rs.getInt("id"));
            c.setUserId(rs.getInt("user_id"));
            c.setProductId(rs.getInt("product_id"));
            c.setQuantity(rs.getInt("quantity"));
            c.setProductName(rs.getString("product_name"));
            c.setPrice(rs.getDouble("price"));
            c.setImageUrl(rs.getString("image_url"));
            return c;
        }, userId);
    }
    public void removeFromCart(int cartId) { template.update("DELETE FROM cart WHERE id=?", cartId); }
    public void clearCart(int userId) { template.update("DELETE FROM cart WHERE user_id=?", userId); }
    public double getCartTotal(int userId) {
        Double total = template.queryForObject(
            "SELECT SUM(p.price*c.quantity) FROM cart c JOIN products p ON c.product_id=p.id WHERE c.user_id=?",
            Double.class, userId);
        return total == null ? 0.0 : total;
    }
}
```
---
## CategoryDAO.java 

```java 
package com.ecommerce.dao;
import java.util.List;
import org.springframework.jdbc.core.JdbcTemplate;
import com.ecommerce.models.Category;
public class CategoryDAO {
    JdbcTemplate template;
    public void setTemplate(JdbcTemplate template) { this.template = template; }
    public void addCategory(Category c) {
        template.update("INSERT INTO categories(category_name,description) VALUES(?,?)",
            c.getCategoryName(), c.getDescription());
    }
    public List<Category> getAllCategories() {
        return template.query("SELECT * FROM categories", (rs, rowNum) -> {
            Category c = new Category();
            c.setId(rs.getInt("id"));
            c.setCategoryName(rs.getString("category_name"));
            c.setDescription(rs.getString("description"));
            return c;
        });
    }
    public void deleteCategory(int id) {
        template.update("DELETE FROM categories WHERE id=?", id);
    }
}
```
--- 
## OrderDAO.java
```java 
package com.ecommerce.dao;

import java.util.List;
import org.springframework.jdbc.core.JdbcTemplate;
import org.springframework.jdbc.core.PreparedStatementCreator;
import org.springframework.jdbc.support.GeneratedKeyHolder;
import org.springframework.jdbc.support.KeyHolder;
import com.ecommerce.models.Cart;
import com.ecommerce.models.Order;
import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.SQLException;
import java.sql.Statement;

public class OrderDAO {

    JdbcTemplate template;

    public void setTemplate(JdbcTemplate template) {
        this.template = template;
    }

    // PLACE ORDER — fixed using KeyHolder to get generated order id
    public int placeOrder(int userId, double totalAmount, List<Cart> cartItems) {

        // Use KeyHolder to get auto-generated order id safely
        KeyHolder keyHolder = new GeneratedKeyHolder();

        template.update(new PreparedStatementCreator() {
            public PreparedStatement createPreparedStatement(Connection con) throws SQLException {
                PreparedStatement ps = con.prepareStatement(
                    "INSERT INTO orders(user_id, total_amount, status) VALUES(?,?,'PLACED')",
                    Statement.RETURN_GENERATED_KEYS);
                ps.setInt(1, userId);
                ps.setDouble(2, totalAmount);
                return ps;
            }
        }, keyHolder);

        // Get the generated order id
        int orderId = keyHolder.getKey().intValue();

        // Insert each cart item into order_items
        for (Cart item : cartItems) {
            template.update(
                "INSERT INTO order_items(order_id, product_id, quantity, price) VALUES(?,?,?,?)",
                orderId,
                item.getProductId(),
                item.getQuantity(),
                item.getPrice()
            );
        }

        return orderId;
    }

    // GET orders for one user
    public List<Order> getOrdersByUser(int userId) {
        String sql = "SELECT * FROM orders WHERE user_id=? ORDER BY order_date DESC";
        return template.query(sql, this::mapOrder, userId);
    }

    // GET all orders — admin
    public List<Order> getAllOrders() {
        String sql = "SELECT * FROM orders ORDER BY order_date DESC";
        return template.query(sql, this::mapOrder);
    }

    // Map ResultSet row to Order object
    private Order mapOrder(java.sql.ResultSet rs, int rowNum) throws java.sql.SQLException {
        Order o = new Order();
        o.setId(rs.getInt("id"));
        o.setUserId(rs.getInt("user_id"));
        o.setTotalAmount(rs.getDouble("total_amount"));
        o.setOrderDate(rs.getDate("order_date"));
        o.setStatus(rs.getString("status"));
        return o;
    }

    // Stats for admin dashboard
    public int getTotalOrders() {
        return template.queryForObject("SELECT COUNT(*) FROM orders", Integer.class);
    }

    public int getTotalUsers() {
        return template.queryForObject(
            "SELECT COUNT(*) FROM users WHERE role='USER'", Integer.class);
    }

    public int getTotalProducts() {
        return template.queryForObject("SELECT COUNT(*) FROM products", Integer.class);
    }
}
```
---
## ProductDAO.java

```java 
package com.ecommerce.dao;
import java.util.List;
import org.springframework.jdbc.core.JdbcTemplate;
import com.ecommerce.models.Product;
public class ProductDAO {
    JdbcTemplate template;
    public void setTemplate(JdbcTemplate template) { this.template = template; }
    private Product mapProduct(java.sql.ResultSet rs, int rowNum) throws java.sql.SQLException {
        Product p = new Product();
        p.setId(rs.getInt("id"));
        p.setProductName(rs.getString("product_name"));
        p.setDescription(rs.getString("description"));
        p.setPrice(rs.getDouble("price"));
        p.setStock(rs.getInt("stock"));
        p.setImageUrl(rs.getString("image_url"));
        p.setCategoryId(rs.getInt("category_id"));
        p.setCategoryName(rs.getString("category_name"));
        return p;
    }
    public void addProduct(Product p) {
        template.update("INSERT INTO products(product_name,description,price,stock,image_url,category_id) VALUES(?,?,?,?,?,?)",
            p.getProductName(), p.getDescription(), p.getPrice(), p.getStock(), p.getImageUrl(), p.getCategoryId());
    }
    public List<Product> getAllProducts() {
        String sql = "SELECT p.*, c.category_name FROM products p JOIN categories c ON p.category_id=c.id ORDER BY p.id DESC";
        return template.query(sql, this::mapProduct);
    }
    public List<Product> getProductsByCategory(int categoryId) {
        String sql = "SELECT p.*, c.category_name FROM products p JOIN categories c ON p.category_id=c.id WHERE p.category_id=?";
        return template.query(sql, this::mapProduct, categoryId);
    }
    public Product getProductById(int id) {
        String sql = "SELECT p.*, c.category_name FROM products p JOIN categories c ON p.category_id=c.id WHERE p.id=?";
        try { return template.queryForObject(sql, this::mapProduct, id); }
        catch (Exception e) { return null; }
    }
    public void updateProduct(Product p) {
        template.update("UPDATE products SET product_name=?,description=?,price=?,stock=?,image_url=?,category_id=? WHERE id=?",
            p.getProductName(), p.getDescription(), p.getPrice(), p.getStock(), p.getImageUrl(), p.getCategoryId(), p.getId());
    }
    public void deleteProduct(int id) { template.update("DELETE FROM products WHERE id=?", id); }
    public void reduceStock(int productId, int quantity) {
        template.update("UPDATE products SET stock=stock-? WHERE id=?", quantity, productId);
    }
}
```
---
## UserDAO.java

```java 
package com.ecommerce.dao;
import org.springframework.jdbc.core.JdbcTemplate;
import com.ecommerce.models.User;
public class UserDAO {
    JdbcTemplate template;
    public void setTemplate(JdbcTemplate template) { this.template = template; }
    public boolean register(User u) {
        String sql = "INSERT INTO users(fullname,email,password,address,role) VALUES(?,?,?,?,?)";
        template.update(sql, u.getFullname(), u.getEmail(), u.getPassword(), u.getAddress(), "USER");
        return true;
    }
    public boolean emailExists(String email) {
        String sql = "SELECT COUNT(*) FROM users WHERE email=?";
        int count = template.queryForObject(sql, Integer.class, email);
        return count > 0;
    }
    public User login(String email, String password) {
        String sql = "SELECT * FROM users WHERE email=? AND password=?";
        try {
            return template.queryForObject(sql, (rs, rowNum) -> {
                User u = new User();
                u.setId(rs.getInt("id"));
                u.setFullname(rs.getString("fullname"));
                u.setEmail(rs.getString("email"));
                u.setPassword(rs.getString("password"));
                u.setAddress(rs.getString("address"));
                u.setRole(rs.getString("role"));
                return u;
            }, email, password);
        } catch (Exception e) { return null; }
    }
}
```
---
## CartController.java
```java 
package com.ecommerce.controllers;

import java.util.List;
import javax.servlet.http.HttpSession;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.*;
import com.ecommerce.dao.CartDAO;
import com.ecommerce.dao.OrderDAO;
import com.ecommerce.dao.ProductDAO;
import com.ecommerce.models.Cart;
import com.ecommerce.models.User;

@Controller
public class CartController {

    @Autowired
    CartDAO cartDAO;

    @Autowired
    ProductDAO productDAO;

    @Autowired
    OrderDAO orderDAO;

    // ==========================================
    // ADD TO CART
    // ==========================================
    @GetMapping("/cart/add/{productId}")
    public String addToCart(@PathVariable int productId,
            HttpSession session) {

        // Must be logged in to add to cart
        User u = (User) session.getAttribute("loggedUser");
        if (u == null) {
            return "redirect:/login";
        }

        // Add 1 quantity by default
        cartDAO.addToCart(u.getId(), productId, 1);
        return "redirect:/cart";
    }

    // ==========================================
    // VIEW CART
    // ==========================================
    @GetMapping("/cart")
    public String viewCart(Model m, HttpSession session) {

        User u = (User) session.getAttribute("loggedUser");
        if (u == null) {
            return "redirect:/login";
        }

        List<Cart> cartItems = cartDAO.getCartByUser(u.getId());
        double total = cartDAO.getCartTotal(u.getId());

        m.addAttribute("cartItems", cartItems);
        m.addAttribute("total", total);
        return "cart";
    }

    // ==========================================
    // REMOVE FROM CART
    // ==========================================
    @GetMapping("/cart/remove/{cartId}")
    public String removeFromCart(@PathVariable int cartId,
            HttpSession session) {

        User u = (User) session.getAttribute("loggedUser");
        if (u == null) {
            return "redirect:/login";
        }

        cartDAO.removeFromCart(cartId);
        return "redirect:/cart";
    }

    // ==========================================
    // CHECKOUT - Place Order
    // ==========================================
    @GetMapping("/checkout")
    public String checkout(Model m, HttpSession session) {

        User u = (User) session.getAttribute("loggedUser");
        if (u == null) {
            return "redirect:/login";
        }

        List<Cart> cartItems = cartDAO.getCartByUser(u.getId());

        if (cartItems.isEmpty()) {
            return "redirect:/cart";
        }

        double total = cartDAO.getCartTotal(u.getId());
        m.addAttribute("cartItems", cartItems);
        m.addAttribute("total", total);
        m.addAttribute("user", u);
        return "checkout";
    }

    @PostMapping("/place-order")
    public String placeOrder(HttpSession session, Model m) {

        User u = (User) session.getAttribute("loggedUser");
        if (u == null) {
            return "redirect:/login";
        }

        List<Cart> cartItems = cartDAO.getCartByUser(u.getId());
        double total = cartDAO.getCartTotal(u.getId());

        // Place the order
        int orderId = orderDAO.placeOrder(u.getId(), total, cartItems);

        // Reduce stock for each product ordered
        for (Cart item : cartItems) {
            productDAO.reduceStock(item.getProductId(), item.getQuantity());
        }

        // Clear the cart after order placed
        cartDAO.clearCart(u.getId());

        m.addAttribute("orderId", orderId);
        m.addAttribute("total", total);
        return "order-success";
    }

    // ==========================================
    // MY ORDERS - User order history
    // ==========================================
    @GetMapping("/my-orders")
    public String myOrders(Model m, HttpSession session) {

        User u = (User) session.getAttribute("loggedUser");
        if (u == null) {
            return "redirect:/login";
        }

        m.addAttribute("orders", orderDAO.getOrdersByUser(u.getId()));
        return "my-orders";
    }

    // ==========================================
    // ADMIN - All orders
    // ==========================================
    @GetMapping("/admin/orders")
    public String allOrders(Model m, HttpSession session) {

        User u = (User) session.getAttribute("loggedUser");
        if (u == null || !u.getRole().equals("ADMIN")) {
            return "redirect:/login";
        }

        m.addAttribute("orders", orderDAO.getAllOrders());
        return "admin-orders";
    }

    // ==========================================
    // ADMIN - Dashboard stats
    // ==========================================
    @GetMapping("/admin/dashboard")
    public String adminDashboard(Model m, HttpSession session) {

        User u = (User) session.getAttribute("loggedUser");
        if (u == null || !u.getRole().equals("ADMIN")) {
            return "redirect:/login";
        }

        m.addAttribute("totalProducts", orderDAO.getTotalProducts());
        m.addAttribute("totalOrders", orderDAO.getTotalOrders());
        m.addAttribute("totalUsers", orderDAO.getTotalUsers());
        m.addAttribute("admin", u);
        return "admin-dashboard";
    }
}
```
---
## CategoryController.java
```java 
package com.ecommerce.controllers;

import javax.servlet.http.HttpSession;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.*;
import com.ecommerce.dao.CategoryDAO;
import com.ecommerce.models.Category;
import com.ecommerce.models.User;

@Controller
public class CategoryController {

    @Autowired
    CategoryDAO categoryDAO;

    // ==========================================
    // ADMIN - Manage categories
    // ==========================================
    @GetMapping("/admin/categories")
    public String manageCategories(Model m, HttpSession session) {

        User u = (User) session.getAttribute("loggedUser");
        if (u == null || !u.getRole().equals("ADMIN")) {
            return "redirect:/login";
        }

        m.addAttribute("categories", categoryDAO.getAllCategories());
        return "manage-categories";
    }

    // ==========================================
    // ADMIN - Add category form
    // ==========================================
    @GetMapping("/admin/add-category")
    public String addCategoryPage(HttpSession session) {

        User u = (User) session.getAttribute("loggedUser");
        if (u == null || !u.getRole().equals("ADMIN")) {
            return "redirect:/login";
        }

        return "add-category";
    }

    @PostMapping("/admin/save-category")
    public String saveCategory(@ModelAttribute Category c,
            HttpSession session) {

        User u = (User) session.getAttribute("loggedUser");
        if (u == null || !u.getRole().equals("ADMIN")) {
            return "redirect:/login";
        }

        categoryDAO.addCategory(c);
        return "redirect:/admin/categories";
    }

    // ==========================================
    // ADMIN - Delete category
    // ==========================================
    @GetMapping("/admin/delete-category/{id}")
    public String deleteCategory(@PathVariable int id,
            HttpSession session) {

        User u = (User) session.getAttribute("loggedUser");
        if (u == null || !u.getRole().equals("ADMIN")) {
            return "redirect:/login";
        }

        categoryDAO.deleteCategory(id);
        return "redirect:/admin/categories";
    }
}
```
---
## ProductController.java
```java
package com.ecommerce.controllers;

import java.util.List;
import javax.servlet.http.HttpSession;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.*;
import com.ecommerce.dao.CategoryDAO;
import com.ecommerce.dao.ProductDAO;
import com.ecommerce.models.Category;
import com.ecommerce.models.Product;
import com.ecommerce.models.User;

@Controller
public class ProductController {

    @Autowired
    ProductDAO productDAO;

    @Autowired
    CategoryDAO categoryDAO;

    // ==========================================
    // USER - View all products (Home Page)
    // ==========================================
    @GetMapping("/products")
    public String allProducts(Model m,
            @RequestParam(required = false) Integer categoryId) {

        List<Product> products;
        List<Category> categories = categoryDAO.getAllCategories();

        // If category filter applied - show filtered products
        if (categoryId != null) {
            products = productDAO.getProductsByCategory(categoryId);
            m.addAttribute("selectedCategory", categoryId);
        } else {
            products = productDAO.getAllProducts();
        }

        m.addAttribute("products", products);
        m.addAttribute("categories", categories);
        return "index";
    }

    // ==========================================
    // USER - Product detail page
    // ==========================================
    @GetMapping("/product/{id}")
    public String productDetail(@PathVariable int id, Model m,
            HttpSession session) {

        Product p = productDAO.getProductById(id);
        m.addAttribute("product", p);
        return "product-detail";
    }

    // ==========================================
    // ADMIN - Manage all products
    // ==========================================
    @GetMapping("/admin/products")
    public String manageProducts(Model m, HttpSession session) {

        // Security check - only admin allowed
        User u = (User) session.getAttribute("loggedUser");
        if (u == null || !u.getRole().equals("ADMIN")) {
            return "redirect:/login";
        }

        m.addAttribute("products", productDAO.getAllProducts());
        return "manage-products";
    }

    // ==========================================
    // ADMIN - Add product form
    // ==========================================
    @GetMapping("/admin/add-product")
    public String addProductPage(Model m, HttpSession session) {

        User u = (User) session.getAttribute("loggedUser");
        if (u == null || !u.getRole().equals("ADMIN")) {
            return "redirect:/login";
        }

        // Send categories to fill dropdown in form
        m.addAttribute("categories", categoryDAO.getAllCategories());
        return "add-product";
    }

    @PostMapping("/admin/save-product")
    public String saveProduct(@ModelAttribute Product p,
            HttpSession session) {

        User u = (User) session.getAttribute("loggedUser");
        if (u == null || !u.getRole().equals("ADMIN")) {
            return "redirect:/login";
        }

        productDAO.addProduct(p);
        return "redirect:/admin/products";
    }

    // ==========================================
    // ADMIN - Edit product form
    // ==========================================
    @GetMapping("/admin/edit-product/{id}")
    public String editProductPage(@PathVariable int id,
            Model m, HttpSession session) {

        User u = (User) session.getAttribute("loggedUser");
        if (u == null || !u.getRole().equals("ADMIN")) {
            return "redirect:/login";
        }

        m.addAttribute("product", productDAO.getProductById(id));
        m.addAttribute("categories", categoryDAO.getAllCategories());
        return "edit-product";
    }

    @PostMapping("/admin/update-product")
    public String updateProduct(@ModelAttribute Product p,
            HttpSession session) {

        User u = (User) session.getAttribute("loggedUser");
        if (u == null || !u.getRole().equals("ADMIN")) {
            return "redirect:/login";
        }

        productDAO.updateProduct(p);
        return "redirect:/admin/products";
    }

    // ==========================================
    // ADMIN - Delete product
    // ==========================================
    @GetMapping("/admin/delete-product/{id}")
    public String deleteProduct(@PathVariable int id,
            HttpSession session) {

        User u = (User) session.getAttribute("loggedUser");
        if (u == null || !u.getRole().equals("ADMIN")) {
            return "redirect:/login";
        }

        productDAO.deleteProduct(id);
        return "redirect:/admin/products";
    }
}
```
---
## UserController.java 
```java
package com.ecommerce.controllers;

import javax.servlet.http.HttpSession;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.*;
import com.ecommerce.dao.UserDAO;
import com.ecommerce.models.User;

@Controller
public class UserController {

    @Autowired
    UserDAO userDAO;

    // ==========================================
    // HOME - redirect to product listing
    // ==========================================
    @GetMapping("/")
    public String home() {
        return "redirect:/products";
    }

    // ==========================================
    // REGISTER
    // ==========================================
    @GetMapping("/register")
    public String registerPage() {
        return "register";
    }

    @PostMapping("/register")
    public String register(@ModelAttribute User u, Model m) {

        // Check if email already exists
        if (userDAO.emailExists(u.getEmail())) {
            m.addAttribute("error", "Email already registered. Please login.");
            return "register";
        }

        userDAO.register(u);
        m.addAttribute("success", "Registration successful! Please login.");
        return "login";
    }

    // ==========================================
    // LOGIN
    // ==========================================
    @GetMapping("/login")
    public String loginPage() {
        return "login";
    }

    @PostMapping("/logincheck")
    public String loginCheck(
            @RequestParam String email,
            @RequestParam String password,
            HttpSession session,
            Model m) {

        User u = userDAO.login(email, password);

        if (u != null) {
            // Store user in session
            session.setAttribute("loggedUser", u);

            // Admin goes to admin dashboard
            // User goes to product listing
            if (u.getRole().equals("ADMIN")) {
                return "redirect:/admin/dashboard";
            } else {
                return "redirect:/products";
            }
        } else {
            m.addAttribute("error", "Invalid email or password.");
            return "login";
        }
    }

    // ==========================================
    // LOGOUT
    // ==========================================
    @GetMapping("/logout")
    public String logout(HttpSession session) {
        session.invalidate();
        return "redirect:/login";
    }
}
```
---
## add-category.jsp
```jsp 
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
    <title>Add Category - Admin</title>
    <link rel="stylesheet" href="${pageContext.request.contextPath}/resources/css/style.css">
</head>
<body>

<nav class="navbar">
    <div class="logo">Shop<span>Easy</span> <span style="font-size:13px;color:#aaa;">Admin</span></div>
    <ul class="nav-links">
        <li><a href="${pageContext.request.contextPath}/products">View Store</a></li>
        <li><a href="${pageContext.request.contextPath}/logout">Logout</a></li>
    </ul>
</nav>

<div class="container">
    <h2 class="page-title">Add New Category</h2>

    <div class="admin-layout">

        <div class="admin-sidebar">
            <h3>Management</h3>
            <ul>
                <li><a href="${pageContext.request.contextPath}/admin/dashboard">Dashboard</a></li>
                <li><a href="${pageContext.request.contextPath}/admin/products">Manage Products</a></li>
                <li><a href="${pageContext.request.contextPath}/admin/add-product">Add Product</a></li>
                <li><a href="${pageContext.request.contextPath}/admin/categories">Manage Categories</a></li>
                <li><a href="${pageContext.request.contextPath}/admin/add-category" class="active">Add Category</a></li>
                <li><a href="${pageContext.request.contextPath}/admin/orders">All Orders</a></li>
            </ul>
        </div>

        <div class="admin-content">
            <div style="background:white; border-radius:12px; padding:30px;
                        box-shadow:0 3px 15px rgba(0,0,0,0.07); max-width:500px;">

                <form action="${pageContext.request.contextPath}/admin/save-category" method="post">

                    <div class="form-group">
                        <label>Category Name</label>
                        <input type="text" name="categoryName"
                               placeholder="e.g. Electronics" required />
                    </div>

                    <div class="form-group">
                        <label>Description</label>
                        <textarea name="description"
                                  placeholder="Brief description of this category"></textarea>
                    </div>

                    <div style="display:flex; gap:12px; margin-top:10px;">
                        <button type="submit" class="btn btn-primary"
                                style="padding:12px 28px;">
                            Save Category
                        </button>
                        <a href="${pageContext.request.contextPath}/admin/categories"
                           class="btn btn-secondary" style="padding:12px 28px;">
                            Cancel
                        </a>
                    </div>

                </form>
            </div>
        </div>
    </div>
</div>

</body>
</html>
```
---
## add-product.jsp
```jsp

<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<!DOCTYPE html>
<html>
<head>
    <title>Add Product - Admin</title>
    <link rel="stylesheet" href="${pageContext.request.contextPath}/resources/css/style.css">
</head>
<body>

<nav class="navbar">
    <div class="logo">Shop<span>Easy</span> <span style="font-size:13px;color:#aaa;">Admin</span></div>
    <ul class="nav-links">
        <li><a href="${pageContext.request.contextPath}/products">View Store</a></li>
        <li><a href="${pageContext.request.contextPath}/logout">Logout</a></li>
    </ul>
</nav>

<div class="container">
    <h2 class="page-title">Add New Product</h2>

    <div class="admin-layout">

        <!-- Sidebar -->
        <div class="admin-sidebar">
            <h3>Management</h3>
            <ul>
                <li><a href="${pageContext.request.contextPath}/admin/dashboard">Dashboard</a></li>
                <li><a href="${pageContext.request.contextPath}/admin/products">Manage Products</a></li>
                <li><a href="${pageContext.request.contextPath}/admin/add-product" class="active">Add Product</a></li>
                <li><a href="${pageContext.request.contextPath}/admin/categories">Manage Categories</a></li>
                <li><a href="${pageContext.request.contextPath}/admin/add-category">Add Category</a></li>
                <li><a href="${pageContext.request.contextPath}/admin/orders">All Orders</a></li>
            </ul>
        </div>

        <!-- Form -->
        <div class="admin-content">
            <div style="background:white; border-radius:12px; padding:30px;
                        box-shadow:0 3px 15px rgba(0,0,0,0.07); max-width:600px;">

                <form action="${pageContext.request.contextPath}/admin/save-product" method="post">

                    <div class="form-group">
                        <label>Product Name</label>
                        <input type="text" name="productName"
                               placeholder="Enter product name" required />
                    </div>

                    <div class="form-group">
                        <label>Description</label>
                        <textarea name="description"
                                  placeholder="Enter product description"
                                  style="min-height:80px;"></textarea>
                    </div>

                    <div style="display:grid; grid-template-columns:1fr 1fr; gap:15px;">
                        <div class="form-group">
                            <label>Price (₹)</label>
                            <input type="number" name="price"
                                   placeholder="e.g. 999" step="0.01" required />
                        </div>
                        <div class="form-group">
                            <label>Stock Quantity</label>
                            <input type="number" name="stock"
                                   placeholder="e.g. 50" required />
                        </div>
                    </div>

                    <div class="form-group">
                        <label>Image Filename</label>
                        <input type="text" name="imageUrl"
                               placeholder="e.g. phone.jpg" />
                        <small style="color:#888; font-size:11px;">
                            Place image in /resources/images/ folder
                        </small>
                    </div>

                    <div class="form-group">
                        <label>Category</label>
                        <select name="categoryId" required>
                            <option value="">-- Select Category --</option>
                            <c:forEach var="cat" items="${categories}">
                                <option value="${cat.id}">${cat.categoryName}</option>
                            </c:forEach>
                        </select>
                    </div>

                    <div style="display:flex; gap:12px; margin-top:10px;">
                        <button type="submit" class="btn btn-primary"
                                style="padding:12px 28px;">
                            Save Product
                        </button>
                        <a href="${pageContext.request.contextPath}/admin/products"
                           class="btn btn-secondary" style="padding:12px 28px;">
                            Cancel
                        </a>
                    </div>

                </form>
            </div>
        </div>
    </div>
</div>

</body>
</html>
```
---
## admin-dashboard.jsp
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<!DOCTYPE html>
<html>
<head>
    <title>Admin Dashboard - ShopEasy</title>
    <link rel="stylesheet" href="${pageContext.request.contextPath}/resources/css/style.css">
</head>
<body>

<nav class="navbar">
    <div class="logo">Shop<span>Easy</span> <span style="font-size:13px; color:#aaa;">Admin</span></div>
    <ul class="nav-links">
        <li><a href="${pageContext.request.contextPath}/products">View Store</a></li>
        <li><a href="${pageContext.request.contextPath}/logout">Logout</a></li>
    </ul>
</nav>

<div class="container">
    <h2 class="page-title">Admin Dashboard</h2>
    <p style="color:#888; margin-bottom:25px;">Welcome, ${admin.fullname}</p>

    <!-- Stats Cards -->
    <div class="stats-grid">
        <div class="stat-card products">
            <div class="stat-number">${totalProducts}</div>
            <div class="stat-label">Total Products</div>
        </div>
        <div class="stat-card orders">
            <div class="stat-number">${totalOrders}</div>
            <div class="stat-label">Total Orders</div>
        </div>
        <div class="stat-card users">
            <div class="stat-number">${totalUsers}</div>
            <div class="stat-label">Registered Users</div>
        </div>
    </div>

    <!-- Admin Layout -->
    <div class="admin-layout">

        <!-- Sidebar -->
        <div class="admin-sidebar">
            <h3>Management</h3>
            <ul>
                <li><a href="${pageContext.request.contextPath}/admin/dashboard" class="active">Dashboard</a></li>
                <li><a href="${pageContext.request.contextPath}/admin/products">Manage Products</a></li>
                <li><a href="${pageContext.request.contextPath}/admin/add-product">Add Product</a></li>
                <li><a href="${pageContext.request.contextPath}/admin/categories">Manage Categories</a></li>
                <li><a href="${pageContext.request.contextPath}/admin/add-category">Add Category</a></li>
                <li><a href="${pageContext.request.contextPath}/admin/orders">All Orders</a></li>
            </ul>
        </div>

        <!-- Main content -->
        <div class="admin-content">
            <div style="background:white; border-radius:12px; padding:30px;
                        box-shadow:0 3px 15px rgba(0,0,0,0.07);">
                <h3 style="margin-bottom:15px; color:#1a1a2e;">Quick Actions</h3>
                <div style="display:flex; gap:15px; flex-wrap:wrap;">
                    <a href="${pageContext.request.contextPath}/admin/add-product"
                       class="btn btn-primary" style="padding:12px 25px;">
                        + Add New Product
                    </a>
                    <a href="${pageContext.request.contextPath}/admin/add-category"
                       class="btn btn-secondary" style="padding:12px 25px;">
                        + Add Category
                    </a>
                    <a href="${pageContext.request.contextPath}/admin/orders"
                       class="btn btn-success" style="padding:12px 25px;">
                        View All Orders
                    </a>
                </div>
            </div>
        </div>
    </div>
</div>

</body>
</html>
```
---
## admin-orders.jsp
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<!DOCTYPE html>
<html>
<head>
    <title>All Orders - Admin</title>
    <link rel="stylesheet" href="${pageContext.request.contextPath}/resources/css/style.css">
</head>
<body>

<nav class="navbar">
    <div class="logo">Shop<span>Easy</span> <span style="font-size:13px;color:#aaa;">Admin</span></div>
    <ul class="nav-links">
        <li><a href="${pageContext.request.contextPath}/products">View Store</a></li>
        <li><a href="${pageContext.request.contextPath}/logout">Logout</a></li>
    </ul>
</nav>

<div class="container">
    <h2 class="page-title">All Orders</h2>

    <div class="admin-layout">

        <div class="admin-sidebar">
            <h3>Management</h3>
            <ul>
                <li><a href="${pageContext.request.contextPath}/admin/dashboard">Dashboard</a></li>
                <li><a href="${pageContext.request.contextPath}/admin/products">Manage Products</a></li>
                <li><a href="${pageContext.request.contextPath}/admin/add-product">Add Product</a></li>
                <li><a href="${pageContext.request.contextPath}/admin/categories">Manage Categories</a></li>
                <li><a href="${pageContext.request.contextPath}/admin/add-category">Add Category</a></li>
                <li><a href="${pageContext.request.contextPath}/admin/orders" class="active">All Orders</a></li>
            </ul>
        </div>

        <div class="admin-content">
            <table class="data-table">
                <tr>
                    <th>Order ID</th>
                    <th>User ID</th>
                    <th>Total Amount</th>
                    <th>Order Date</th>
                    <th>Status</th>
                </tr>

                <c:forEach var="order" items="${orders}">
                    <tr>
                        <td>#${order.id}</td>
                        <td>${order.userId}</td>
                        <td style="font-weight:600; color:#e94560;">
                            ₹${order.totalAmount}
                        </td>
                        <td>${order.orderDate}</td>
                        <td>
                            <span style="background:#d4edda; color:#155724;
                                         padding:3px 10px; border-radius:12px;
                                         font-size:12px; font-weight:600;">
                                ${order.status}
                            </span>
                        </td>
                    </tr>
                </c:forEach>
            </table>

            <c:if test="${empty orders}">
                <div style="text-align:center; padding:40px; color:#888;">
                    No orders placed yet.
                </div>
            </c:if>
        </div>
    </div>
</div>

</body>
</html>
```
---

## cart.jsp

```jsp
<%-- cart.jsp --%>
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<!DOCTYPE html>
<html>
<head>
    <title>My Cart - ShopEasy</title>
    <link rel="stylesheet" href="${pageContext.request.contextPath}/resources/css/style.css">
</head>
<body>

<nav class="navbar">
    <div class="logo">Shop<span>Easy</span></div>
    <ul class="nav-links">
        <li><a href="${pageContext.request.contextPath}/products">Home</a></li>
        <li><a href="${pageContext.request.contextPath}/my-orders">My Orders</a></li>
        <li><a href="${pageContext.request.contextPath}/logout">Logout</a></li>
        <li><a href="${pageContext.request.contextPath}/cart" class="cart-btn">🛒 Cart</a></li>
    </ul>
</nav>

<div class="container">
    <h2 class="page-title">My Cart</h2>

    <c:choose>
        <c:when test="${empty cartItems}">
            <!-- Empty cart message -->
            <div style="text-align:center; padding:60px; background:white;
                        border-radius:12px; box-shadow:0 3px 15px rgba(0,0,0,0.07);">
                <div style="font-size:60px; margin-bottom:15px;">🛒</div>
                <h3 style="color:#888; margin-bottom:15px;">Your cart is empty</h3>
                <a href="${pageContext.request.contextPath}/products"
                   class="btn btn-primary" style="padding:12px 30px;">
                    Continue Shopping
                </a>
            </div>
        </c:when>
        <c:otherwise>
            <div class="cart-layout">

                <!-- Cart Items List -->
                <div>
                    <c:forEach var="item" items="${cartItems}">
                        <div class="cart-item">
                            <img src="${pageContext.request.contextPath}/resources/images/${item.imageUrl}"
                                 onerror="this.src='https://via.placeholder.com/80x80?text=IMG'"
                                 alt="${item.productName}" />

                            <div class="cart-item-info">
                                <h3>${item.productName}</h3>
                                <div class="item-price">${item.price}</div>
                                <div class="item-qty">Quantity: ${item.quantity}</div>
                                <div style="font-size:13px; color:#e94560; font-weight:600;">
                                    Subtotal: ₹${item.totalPrice}
                                </div>
                            </div>

                            <!-- Remove button -->
                            <a href="${pageContext.request.contextPath}/cart/remove/${item.id}"
                               class="btn btn-danger" style="padding:6px 12px; font-size:12px;"
                               onclick="return confirm('Remove this item?')">
                                Remove
                            </a>
                        </div>
                    </c:forEach>

                    <a href="${pageContext.request.contextPath}/products"
                       style="color:#e94560; font-size:13px;">← Continue Shopping</a>
                </div>

                <!-- Order Summary -->
                <div class="order-summary">
                    <h3>Order Summary</h3>

                    <c:forEach var="item" items="${cartItems}">
                        <div class="summary-row">
                            <span>${item.productName} x${item.quantity}</span>
                            <span>₹${item.totalPrice}</span>
                        </div>
                    </c:forEach>

                    <div class="summary-row total">
                        <span>Total</span>
                        <span>₹${total}</span>
                    </div>

                    <a href="${pageContext.request.contextPath}/checkout"
                       class="btn btn-primary"
                       style="width:100%; text-align:center; padding:14px; margin-top:15px; display:block;">
                        Proceed to Checkout
                    </a>
                </div>
            </div>
        </c:otherwise>
    </c:choose>
</div>

</body>
</html>

```

---
## checkout.jsp
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<!DOCTYPE html>
<html>
<head>
    <title>Checkout - ShopEasy</title>
    <link rel="stylesheet" href="${pageContext.request.contextPath}/resources/css/style.css">
</head>
<body>

<nav class="navbar">
    <div class="logo">Shop<span>Easy</span></div>
    <ul class="nav-links">
        <li><a href="${pageContext.request.contextPath}/products">Home</a></li>
        <li><a href="${pageContext.request.contextPath}/cart" class="cart-btn">🛒 Cart</a></li>
    </ul>
</nav>

<div class="container">
    <h2 class="page-title">Checkout</h2>

    <div class="cart-layout">

        <!-- Delivery Address -->
        <div>
            <div style="background:white; border-radius:12px; padding:25px;
                        box-shadow:0 3px 15px rgba(0,0,0,0.07); margin-bottom:20px;">
                <h3 style="margin-bottom:18px; font-size:16px; color:#1a1a2e;">
                    Delivery Address
                </h3>
                <p style="font-size:14px; color:#555; line-height:1.8;">
                    <strong>${user.fullname}</strong><br/>
                    ${user.address}<br/>
                    ${user.email}
                </p>
            </div>

            <!-- Items in order -->
            <div style="background:white; border-radius:12px; padding:25px;
                        box-shadow:0 3px 15px rgba(0,0,0,0.07);">
                <h3 style="margin-bottom:18px; font-size:16px; color:#1a1a2e;">
                    Items in Your Order
                </h3>
                <c:forEach var="item" items="${cartItems}">
                    <div style="display:flex; justify-content:space-between;
                                padding:10px 0; border-bottom:1px solid #f0f0f0;
                                font-size:13px;">
                        <span>${item.productName} × ${item.quantity}</span>
                        <span style="font-weight:600;">₹${item.totalPrice}</span>
                    </div>
                </c:forEach>
            </div>
        </div>

        <!-- Payment Summary -->
        <div class="order-summary">
            <h3>Payment Summary</h3>

            <c:forEach var="item" items="${cartItems}">
                <div class="summary-row">
                    <span>${item.productName}</span>
                    <span>₹${item.price} × ${item.quantity}</span>
                </div>
            </c:forEach>

            <div class="summary-row total">
                <span>Total Amount</span>
                <span>₹${total}</span>
            </div>

            <!-- Place Order form - POST request -->
            <form action="${pageContext.request.contextPath}/place-order" method="post">
                <button type="submit" class="form-submit-btn"
                        style="margin-top:15px;"
                        onclick="return confirm('Confirm order placement?')">
                    Place Order ₹${total}
                </button>
            </form>

            <a href="${pageContext.request.contextPath}/cart"
               style="display:block; text-align:center; margin-top:12px;
                      font-size:13px; color:#888;">
                ← Back to Cart
            </a>
        </div>
    </div>
</div>

</body>
</html>
```
---
## edit-product.jsp
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<!DOCTYPE html>
<html>
<head>
    <title>Edit Product - Admin</title>
    <link rel="stylesheet" href="${pageContext.request.contextPath}/resources/css/style.css">
</head>
<body>

<nav class="navbar">
    <div class="logo">Shop<span>Easy</span> <span style="font-size:13px;color:#aaa;">Admin</span></div>
    <ul class="nav-links">
        <li><a href="${pageContext.request.contextPath}/products">View Store</a></li>
        <li><a href="${pageContext.request.contextPath}/logout">Logout</a></li>
    </ul>
</nav>

<div class="container">
    <h2 class="page-title">Edit Product</h2>

    <div class="admin-layout">

        <!-- Sidebar -->
        <div class="admin-sidebar">
            <h3>Management</h3>
            <ul>
                <li><a href="${pageContext.request.contextPath}/admin/dashboard">Dashboard</a></li>
                <li><a href="${pageContext.request.contextPath}/admin/products" class="active">Manage Products</a></li>
                <li><a href="${pageContext.request.contextPath}/admin/add-product">Add Product</a></li>
                <li><a href="${pageContext.request.contextPath}/admin/categories">Manage Categories</a></li>
                <li><a href="${pageContext.request.contextPath}/admin/add-category">Add Category</a></li>
                <li><a href="${pageContext.request.contextPath}/admin/orders">All Orders</a></li>
            </ul>
        </div>

        <!-- Edit Form -->
        <div class="admin-content">
            <div style="background:white; border-radius:12px; padding:30px;
                        box-shadow:0 3px 15px rgba(0,0,0,0.07); max-width:600px;">

                <form action="${pageContext.request.contextPath}/admin/update-product" method="post">

                    <!-- Hidden id field — MUST be present to know which product to update -->
                    <input type="hidden" name="id" value="${product.id}" />

                    <div class="form-group">
                        <label>Product Name</label>
                        <input type="text" name="productName"
                               value="${product.productName}" required />
                    </div>

                    <div class="form-group">
                        <label>Description</label>
                        <textarea name="description"
                                  style="min-height:80px;">${product.description}</textarea>
                    </div>

                    <div style="display:grid; grid-template-columns:1fr 1fr; gap:15px;">
                        <div class="form-group">
                            <label>Price (₹)</label>
                            <input type="number" name="price"
                                   value="${product.price}" step="0.01" required />
                        </div>
                        <div class="form-group">
                            <label>Stock Quantity</label>
                            <input type="number" name="stock"
                                   value="${product.stock}" required />
                        </div>
                    </div>

                    <div class="form-group">
                        <label>Image Filename</label>
                        <input type="text" name="imageUrl"
                               value="${product.imageUrl}" />
                    </div>

                    <div class="form-group">
                        <label>Category</label>
                        <select name="categoryId" required>
                            <c:forEach var="cat" items="${categories}">
                                <option value="${cat.id}"
                                    ${product.categoryId == cat.id ? 'selected' : ''}>
                                    ${cat.categoryName}
                                </option>
                            </c:forEach>
                        </select>
                    </div>

                    <div style="display:flex; gap:12px; margin-top:10px;">
                        <button type="submit" class="btn btn-success"
                                style="padding:12px 28px;">
                            Update Product
                        </button>
                        <a href="${pageContext.request.contextPath}/admin/products"
                           class="btn btn-secondary" style="padding:12px 28px;">
                            Cancel
                        </a>
                    </div>

                </form>
            </div>
        </div>
    </div>
</div>

</body>
</html>
```
---
## index.jsp 
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<!DOCTYPE html>
<html>
<head>
    <title>ShopEasy - Products</title>
    <link rel="stylesheet" href="${pageContext.request.contextPath}/resources/css/style.css">
</head>
<body>

<!-- NAVBAR -->
<nav class="navbar">
    <div class="logo">Shop<span>Easy</span></div>
    <ul class="nav-links">
        <li><a href="${pageContext.request.contextPath}/products">Home</a></li>

        <c:choose>
            <c:when test="${not empty sessionScope.loggedUser}">
                <!-- Logged in user links -->
                <li><a href="#">Hello, ${sessionScope.loggedUser.fullname}</a></li>
                <li><a href="${pageContext.request.contextPath}/my-orders">My Orders</a></li>

                <!-- Show admin link only if admin -->
                <c:if test="${sessionScope.loggedUser.role == 'ADMIN'}">
                    <li><a href="${pageContext.request.contextPath}/admin/dashboard">Admin Panel</a></li>
                </c:if>

                <li><a href="${pageContext.request.contextPath}/cart" class="cart-btn">🛒 Cart</a></li>
                <li><a href="${pageContext.request.contextPath}/logout">Logout</a></li>
            </c:when>
            <c:otherwise>
                <!-- Not logged in links -->
                <li><a href="${pageContext.request.contextPath}/login">Login</a></li>
                <li><a href="${pageContext.request.contextPath}/register">Register</a></li>
                <li><a href="${pageContext.request.contextPath}/cart" class="cart-btn">🛒 Cart</a></li>
            </c:otherwise>
        </c:choose>
    </ul>
</nav>

<!-- HERO BANNER -->
<div style="background: linear-gradient(135deg, #1a1a2e, #16213e);
            padding: 50px 40px; text-align: center; color: white;">
    <h1 style="font-size:36px; margin-bottom:10px;">
        Welcome to <span style="color:#e94560;">ShopEasy</span>
    </h1>
    <p style="font-size:16px; color:#ccc;">
        Discover amazing products at the best prices
    </p>
</div>

<div class="container">

    <!-- CATEGORY FILTER BAR -->
    <h2 class="page-title">All Products</h2>

    <div class="filter-bar">
        <!-- All products button -->
        <a href="${pageContext.request.contextPath}/products"
           class="filter-btn ${empty selectedCategory ? 'active' : ''}">
            All
        </a>

        <!-- One button per category -->
        <c:forEach var="cat" items="${categories}">
            <a href="${pageContext.request.contextPath}/products?categoryId=${cat.id}"
               class="filter-btn ${selectedCategory == cat.id ? 'active' : ''}">
                ${cat.categoryName}
            </a>
        </c:forEach>
    </div>

    <!-- PRODUCT GRID -->
    <div class="product-grid">
        <c:forEach var="p" items="${products}">
            <div class="product-card">

                <!-- Product image - use placeholder if no image -->
                <img src="${pageContext.request.contextPath}/resources/images/${p.imageUrl}"
                     onerror="this.src='https://via.placeholder.com/300x200?text=No+Image'"
                     alt="${p.productName}" />

                <div class="product-card-body">
                    <h3>${p.productName}</h3>
                    <span class="category-tag">${p.categoryName}</span>
                    <div class="price">${p.price}</div>

                    <!-- Stock status -->
                    <c:choose>
                        <c:when test="${p.stock > 0}">
                            <div class="stock">✓ In Stock (${p.stock} left)</div>
                        </c:when>
                        <c:otherwise>
                            <div class="stock out">✗ Out of Stock</div>
                        </c:otherwise>
                    </c:choose>

                    <!-- View detail + Add to cart buttons -->
                    <div style="display:flex; gap:8px;">
                        <a href="${pageContext.request.contextPath}/product/${p.id}"
                           class="btn btn-secondary" style="flex:1; text-align:center;">
                            View
                        </a>

                        <c:if test="${p.stock > 0}">
                            <a href="${pageContext.request.contextPath}/cart/add/${p.id}"
                               class="btn btn-primary" style="flex:1;">
                                Add to Cart
                            </a>
                        </c:if>
                    </div>
                </div>
            </div>
        </c:forEach>
    </div>

    <!-- No products message -->
    <c:if test="${empty products}">
        <div style="text-align:center; padding:60px; color:#888;">
            <h3>No products found in this category.</h3>
            <a href="${pageContext.request.contextPath}/products"
               style="color:#e94560;">View all products</a>
        </div>
    </c:if>

</div>

</body>
</html>

```
---
## login.jsp
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<!DOCTYPE html>
<html>
<head>
    <title>Login - ShopEasy</title>
    <link rel="stylesheet" href="${pageContext.request.contextPath}/resources/css/style.css">
</head>
<body>

<nav class="navbar">
    <div class="logo">Shop<span>Easy</span></div>
    <ul class="nav-links">
        <li><a href="${pageContext.request.contextPath}/products">Home</a></li>
        <li><a href="${pageContext.request.contextPath}/register">Register</a></li>
    </ul>
</nav>

<div class="container" style="padding-top:50px;">
    <div class="form-container">
        <h2>Welcome Back</h2>

        <c:if test="${not empty success}">
            <div class="alert alert-success">${success}</div>
        </c:if>

        <c:if test="${not empty error}">
            <div class="alert alert-error">${error}</div>
        </c:if>

        <form action="${pageContext.request.contextPath}/logincheck" method="post">

            <div class="form-group">
                <label>Email Address</label>
                <input type="email" name="email"
                       placeholder="Enter email" required />
            </div>

            <div class="form-group">
                <label>Password</label>
                <input type="password" name="password"
                       placeholder="Enter password" required />
            </div>

            <button type="submit" class="form-submit-btn">Login</button>
        </form>

        <div class="form-link">
            Don't have an account?
            <a href="${pageContext.request.contextPath}/register">Register here</a>
        </div>

        <div style="margin-top:20px; padding:12px; background:#f8f9fa;
                    border-radius:8px; font-size:12px; color:#666;">
            <strong>Test Admin:</strong> admin@shop.com / admin123<br/>
            <strong>Test User:</strong> rahul@gmail.com / 1234
        </div>
    </div>
</div>

</body>
</html>
```
---
## manage-categories.jsp
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<!DOCTYPE html>
<html>
<head>
    <title>Manage Categories - Admin</title>
    <link rel="stylesheet" href="${pageContext.request.contextPath}/resources/css/style.css">
</head>
<body>

<nav class="navbar">
    <div class="logo">Shop<span>Easy</span> <span style="font-size:13px;color:#aaa;">Admin</span></div>
    <ul class="nav-links">
        <li><a href="${pageContext.request.contextPath}/products">View Store</a></li>
        <li><a href="${pageContext.request.contextPath}/logout">Logout</a></li>
    </ul>
</nav>

<div class="container">
    <h2 class="page-title">Manage Categories</h2>

    <div class="admin-layout">

        <div class="admin-sidebar">
            <h3>Management</h3>
            <ul>
                <li><a href="${pageContext.request.contextPath}/admin/dashboard">Dashboard</a></li>
                <li><a href="${pageContext.request.contextPath}/admin/products">Manage Products</a></li>
                <li><a href="${pageContext.request.contextPath}/admin/add-product">Add Product</a></li>
                <li><a href="${pageContext.request.contextPath}/admin/categories" class="active">Manage Categories</a></li>
                <li><a href="${pageContext.request.contextPath}/admin/add-category">Add Category</a></li>
                <li><a href="${pageContext.request.contextPath}/admin/orders">All Orders</a></li>
            </ul>
        </div>

        <div class="admin-content">
            <div style="margin-bottom:18px;">
                <a href="${pageContext.request.contextPath}/admin/add-category"
                   class="btn btn-primary" style="padding:10px 22px;">
                    + Add New Category
                </a>
            </div>

            <table class="data-table">
                <tr>
                    <th>#</th>
                    <th>Category Name</th>
                    <th>Description</th>
                    <th>Action</th>
                </tr>
                <c:forEach var="cat" items="${categories}" varStatus="st">
                    <tr>
                        <td>${st.index + 1}</td>
                        <td>${cat.categoryName}</td>
                        <td>${cat.description}</td>
                        <td>
                            <a href="${pageContext.request.contextPath}/admin/delete-category/${cat.id}"
                               class="btn btn-danger" style="padding:5px 12px; font-size:12px;"
                               onclick="return confirm('Delete this category? All products under it may be affected.')">
                                Delete
                            </a>
                        </td>
                    </tr>
                </c:forEach>
            </table>
        </div>
    </div>
</div>

</body>
</html>
```
---
## manage-products.jsp
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<!DOCTYPE html>
<html>
<head>
    <title>Manage Products - Admin</title>
    <link rel="stylesheet" href="${pageContext.request.contextPath}/resources/css/style.css">
</head>
<body>

<nav class="navbar">
    <div class="logo">Shop<span>Easy</span> <span style="font-size:13px;color:#aaa;">Admin</span></div>
    <ul class="nav-links">
        <li><a href="${pageContext.request.contextPath}/products">View Store</a></li>
        <li><a href="${pageContext.request.contextPath}/logout">Logout</a></li>
    </ul>
</nav>

<div class="container">
    <h2 class="page-title">Manage Products</h2>

    <div class="admin-layout">

        <!-- Sidebar -->
        <div class="admin-sidebar">
            <h3>Management</h3>
            <ul>
                <li><a href="${pageContext.request.contextPath}/admin/dashboard">Dashboard</a></li>
                <li><a href="${pageContext.request.contextPath}/admin/products" class="active">Manage Products</a></li>
                <li><a href="${pageContext.request.contextPath}/admin/add-product">Add Product</a></li>
                <li><a href="${pageContext.request.contextPath}/admin/categories">Manage Categories</a></li>
                <li><a href="${pageContext.request.contextPath}/admin/add-category">Add Category</a></li>
                <li><a href="${pageContext.request.contextPath}/admin/orders">All Orders</a></li>
            </ul>
        </div>

        <!-- Main Content -->
        <div class="admin-content">

            <!-- Add product button -->
            <div style="margin-bottom:18px;">
                <a href="${pageContext.request.contextPath}/admin/add-product"
                   class="btn btn-primary" style="padding:10px 22px;">
                    + Add New Product
                </a>
            </div>

            <table class="data-table">
                <tr>
                    <th>#</th>
                    <th>Product Name</th>
                    <th>Category</th>
                    <th>Price (₹)</th>
                    <th>Stock</th>
                    <th>Actions</th>
                </tr>

                <c:forEach var="p" items="${products}" varStatus="st">
                    <tr>
                        <td>${st.index + 1}</td>
                        <td>${p.productName}</td>
                        <td>${p.categoryName}</td>
                        <td style="font-weight:600; color:#e94560;">₹${p.price}</td>
                        <td>
                            <c:choose>
                                <c:when test="${p.stock > 0}">
                                    <span style="color:#28a745;">${p.stock}</span>
                                </c:when>
                                <c:otherwise>
                                    <span style="color:#dc3545;">Out of Stock</span>
                                </c:otherwise>
                            </c:choose>
                        </td>
                        <td style="display:flex; gap:8px;">
                            <!-- Edit -->
                            <a href="${pageContext.request.contextPath}/admin/edit-product/${p.id}"
                               class="btn btn-warning" style="padding:5px 12px; font-size:12px;">
                                Edit
                            </a>
                            <!-- Delete -->
                            <a href="${pageContext.request.contextPath}/admin/delete-product/${p.id}"
                               class="btn btn-danger" style="padding:5px 12px; font-size:12px;"
                               onclick="return confirm('Delete this product?')">
                                Delete
                            </a>
                        </td>
                    </tr>
                </c:forEach>
            </table>

            <c:if test="${empty products}">
                <div style="text-align:center; padding:40px; color:#888;">
                    No products found.
                    <a href="${pageContext.request.contextPath}/admin/add-product"
                       style="color:#e94560;">Add one now</a>
                </div>
            </c:if>

        </div>
    </div>
</div>

</body>
</html>
```
---
## my-ordres.jsp
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<!DOCTYPE html>
<html>
<head>
    <title>My Orders - ShopEasy</title>
    <link rel="stylesheet" href="${pageContext.request.contextPath}/resources/css/style.css">
</head>
<body>

<nav class="navbar">
    <div class="logo">Shop<span>Easy</span></div>
    <ul class="nav-links">
        <li><a href="${pageContext.request.contextPath}/products">Home</a></li>
        <li><a href="${pageContext.request.contextPath}/my-orders">My Orders</a></li>
        <li><a href="${pageContext.request.contextPath}/cart" class="cart-btn">🛒 Cart</a></li>
        <li><a href="${pageContext.request.contextPath}/logout">Logout</a></li>
    </ul>
</nav>

<div class="container">
    <h2 class="page-title">My Orders</h2>

    <c:choose>
        <c:when test="${empty orders}">
            <div style="text-align:center; padding:60px; background:white;
                        border-radius:12px; box-shadow:0 3px 15px rgba(0,0,0,0.07);">
                <div style="font-size:50px; margin-bottom:15px;">📦</div>
                <h3 style="color:#888; margin-bottom:15px;">No orders yet</h3>
                <a href="${pageContext.request.contextPath}/products"
                   class="btn btn-primary" style="padding:12px 30px;">
                    Start Shopping
                </a>
            </div>
        </c:when>
        <c:otherwise>
            <table class="data-table">
                <tr>
                    <th>Order ID</th>
                    <th>Date</th>
                    <th>Total Amount</th>
                    <th>Status</th>
                </tr>
                <c:forEach var="order" items="${orders}">
                    <tr>
                        <td>#${order.id}</td>
                        <td>${order.orderDate}</td>
                        <td style="font-weight:600; color:#e94560;">₹${order.totalAmount}</td>
                        <td>
                            <span style="background:#d4edda; color:#155724;
                                         padding:3px 10px; border-radius:12px;
                                         font-size:12px; font-weight:600;">
                                ${order.status}
                            </span>
                        </td>
                    </tr>
                </c:forEach>
            </table>
        </c:otherwise>
    </c:choose>
</div>

</body>
</html>
```
---
## order-success.jsp
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<!DOCTYPE html>
<html>
<head>
    <title>Order Placed - ShopEasy</title>
    <link rel="stylesheet" href="${pageContext.request.contextPath}/resources/css/style.css">
</head>
<body>

<nav class="navbar">
    <div class="logo">Shop<span>Easy</span></div>
    <ul class="nav-links">
        <li><a href="${pageContext.request.contextPath}/products">Home</a></li>
        <li><a href="${pageContext.request.contextPath}/my-orders">My Orders</a></li>
    </ul>
</nav>

<div class="container" style="padding-top:50px;">
    <div class="success-box">
        <div class="checkmark">...</div>
        <h2>Order Placed Successfully!</h2>
        <p>Thank you for your purchase.</p>
        <p>Your Order ID: <span class="order-id">#${orderId}</span></p>
        <p style="margin-bottom:25px;">Total Paid: <strong style="color:#e94560;">₹${total}</strong></p>

        <div style="display:flex; gap:12px; justify-content:center;">
            <a href="${pageContext.request.contextPath}/my-orders"
               class="btn btn-secondary" style="padding:10px 22px;">
                View My Orders
            </a>
            <a href="${pageContext.request.contextPath}/products"
               class="btn btn-primary" style="padding:10px 22px;">
                Continue Shopping
            </a>
        </div>
    </div>
</div>

</body>
</html>
```
---
## product-details.jsp
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<!DOCTYPE html>
<html>
<head>
    <title>${product.productName} - ShopEasy</title>
    <link rel="stylesheet" href="${pageContext.request.contextPath}/resources/css/style.css">
</head>
<body>

<nav class="navbar">
    <div class="logo">Shop<span>Easy</span></div>
    <ul class="nav-links">
        <li><a href="${pageContext.request.contextPath}/products">Home</a></li>
        <c:if test="${not empty sessionScope.loggedUser}">
            <li><a href="${pageContext.request.contextPath}/my-orders">My Orders</a></li>
            <li><a href="${pageContext.request.contextPath}/logout">Logout</a></li>
        </c:if>
        <li><a href="${pageContext.request.contextPath}/cart" class="cart-btn">🛒 Cart</a></li>
    </ul>
</nav>

<div class="container">

    <!-- Breadcrumb -->
    <p style="font-size:13px; color:#888; margin-bottom:20px;">
        <a href="${pageContext.request.contextPath}/products" style="color:#e94560;">Home</a>
        &nbsp;›&nbsp; ${product.productName}
    </p>

    <div class="product-detail-layout">

        <!-- Product Image -->
        <img class="product-detail-img"
             src="${pageContext.request.contextPath}/resources/images/${product.imageUrl}"
             onerror="this.src='https://via.placeholder.com/400x350?text=No+Image'"
             alt="${product.productName}" />

        <!-- Product Info -->
        <div class="product-detail-info">
            <span class="category-tag">${product.categoryName}</span>
            <h2>${product.productName}</h2>
            <div class="detail-price">${product.price}</div>
            <p class="detail-desc">${product.description}</p>

            <c:choose>
                <c:when test="${product.stock > 0}">
                    <p class="detail-stock" style="color:#28a745;">
                        ✓ In Stock — ${product.stock} units available
                    </p>
                    <a href="${pageContext.request.contextPath}/cart/add/${product.id}"
                       class="btn btn-primary" style="padding:14px 30px; font-size:15px;">
                        🛒 Add to Cart
                    </a>
                </c:when>
                <c:otherwise>
                    <p class="detail-stock" style="color:#dc3545;">
                        ✗ Out of Stock
                    </p>
                    <button class="btn btn-secondary" disabled
                            style="padding:14px 30px; font-size:15px; opacity:0.6;">
                        Out of Stock
                    </button>
                </c:otherwise>
            </c:choose>

            <br/><br/>
            <a href="${pageContext.request.contextPath}/products"
               style="color:#888; font-size:13px;">← Back to products</a>
        </div>
    </div>
</div>

</body>
</html>
```
---
## register.jsp
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<!DOCTYPE html>
<html>
<head>
    <title>Register - ShopEasy</title>
    <link rel="stylesheet" href="${pageContext.request.contextPath}/resources/css/style.css">
</head>
<body>

<nav class="navbar">
    <div class="logo">Shop<span>Easy</span></div>
    <ul class="nav-links">
        <li><a href="${pageContext.request.contextPath}/products">Home</a></li>
        <li><a href="${pageContext.request.contextPath}/login">Login</a></li>
    </ul>
</nav>

<div class="container" style="padding-top:50px;">
    <div class="form-container">
        <h2>Create Account</h2>

        <c:if test="${not empty error}">
            <div class="alert alert-error">${error}</div>
        </c:if>

        <form action="${pageContext.request.contextPath}/register" method="post">

            <div class="form-group">
                <label>Full Name</label>
                <input type="text" name="fullname"
                       placeholder="Enter your full name" required />
            </div>

            <div class="form-group">
                <label>Email Address</label>
                <input type="email" name="email"
                       placeholder="Enter email" required />
            </div>

            <div class="form-group">
                <label>Password</label>
                <input type="password" name="password"
                       placeholder="Create password" required />
            </div>

            <div class="form-group">
                <label>Address</label>
                <textarea name="address"
                          placeholder="Enter your address"></textarea>
            </div>

            <button type="submit" class="form-submit-btn">Register</button>
        </form>

        <div class="form-link">
            Already have an account?
            <a href="${pageContext.request.contextPath}/login">Login here</a>
        </div>
    </div>
</div>

</body>
</html>
```
---
## style.css
```css
/* ============================================
   E-Commerce Product Management System
   style.css - Main Stylesheet
   ============================================ */

/* Reset & Base */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

body {
    background-color: #f4f6f9;
    color: #333;
}

a {
    text-decoration: none;
    color: inherit;
}

/* ============================================
   NAVBAR
   ============================================ */
.navbar {
    background-color: #1a1a2e;
    padding: 15px 40px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    position: sticky;
    top: 0;
    z-index: 1000;
    box-shadow: 0 2px 10px rgba(0,0,0,0.3);
}

.navbar .logo {
    font-size: 24px;
    font-weight: 700;
    color: #e94560;
    letter-spacing: 1px;
}

.navbar .logo span {
    color: #ffffff;
}

.nav-links {
    display: flex;
    gap: 25px;
    align-items: center;
    list-style: none;
}

.nav-links a {
    color: #ccc;
    font-size: 14px;
    transition: color 0.3s;
}

.nav-links a:hover {
    color: #e94560;
}

.nav-links .cart-btn {
    background: #e94560;
    color: white;
    padding: 8px 18px;
    border-radius: 20px;
    font-size: 13px;
}

.nav-links .cart-btn:hover {
    background: #c73652;
    color: white;
}

/* ============================================
   CONTAINER
   ============================================ */
.container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 30px 20px;
}

/* ============================================
   PAGE TITLE
   ============================================ */
.page-title {
    font-size: 26px;
    font-weight: 600;
    margin-bottom: 25px;
    color: #1a1a2e;
    border-left: 4px solid #e94560;
    padding-left: 12px;
}

/* ============================================
   PRODUCT GRID
   ============================================ */
.product-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
    gap: 25px;
    margin-top: 20px;
}

.product-card {
    background: white;
    border-radius: 12px;
    overflow: hidden;
    box-shadow: 0 3px 15px rgba(0,0,0,0.08);
    transition: transform 0.3s, box-shadow 0.3s;
}

.product-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 8px 25px rgba(0,0,0,0.15);
}

.product-card img {
    width: 100%;
    height: 200px;
    object-fit: cover;
    background: #f0f0f0;
}

.product-card-body {
    padding: 15px;
}

.product-card-body h3 {
    font-size: 16px;
    font-weight: 600;
    margin-bottom: 6px;
    color: #1a1a2e;
}

.product-card-body .category-tag {
    font-size: 11px;
    background: #e8f4ff;
    color: #0066cc;
    padding: 2px 8px;
    border-radius: 10px;
    display: inline-block;
    margin-bottom: 8px;
}

.product-card-body .price {
    font-size: 20px;
    font-weight: 700;
    color: #e94560;
    margin-bottom: 5px;
}

.product-card-body .price::before {
    content: "₹";
}

.product-card-body .stock {
    font-size: 12px;
    color: #28a745;
    margin-bottom: 12px;
}

.product-card-body .stock.out {
    color: #dc3545;
}

.btn {
    display: inline-block;
    padding: 8px 18px;
    border-radius: 6px;
    font-size: 13px;
    font-weight: 500;
    cursor: pointer;
    border: none;
    transition: all 0.3s;
}

.btn-primary {
    background: #e94560;
    color: white;
    width: 100%;
    text-align: center;
}

.btn-primary:hover {
    background: #c73652;
    color: white;
}

.btn-secondary {
    background: #1a1a2e;
    color: white;
}

.btn-secondary:hover {
    background: #16213e;
    color: white;
}

.btn-success {
    background: #28a745;
    color: white;
}

.btn-success:hover {
    background: #218838;
    color: white;
}

.btn-danger {
    background: #dc3545;
    color: white;
}

.btn-danger:hover {
    background: #c82333;
    color: white;
}

.btn-warning {
    background: #ffc107;
    color: #333;
}

.btn-warning:hover {
    background: #e0a800;
}

/* ============================================
   CATEGORY FILTER BAR
   ============================================ */
.filter-bar {
    display: flex;
    gap: 10px;
    flex-wrap: wrap;
    margin-bottom: 20px;
}

.filter-btn {
    padding: 7px 18px;
    border-radius: 20px;
    font-size: 13px;
    border: 2px solid #ddd;
    background: white;
    cursor: pointer;
    transition: all 0.3s;
    color: #333;
}

.filter-btn:hover,
.filter-btn.active {
    background: #1a1a2e;
    color: white;
    border-color: #1a1a2e;
}

/* ============================================
   FORMS
   ============================================ */
.form-container {
    background: white;
    padding: 35px;
    border-radius: 12px;
    box-shadow: 0 3px 20px rgba(0,0,0,0.08);
    max-width: 500px;
    margin: 0 auto;
}

.form-container h2 {
    font-size: 22px;
    margin-bottom: 25px;
    color: #1a1a2e;
    text-align: center;
}

.form-group {
    margin-bottom: 18px;
}

.form-group label {
    display: block;
    font-size: 13px;
    font-weight: 600;
    margin-bottom: 6px;
    color: #555;
}

.form-group input,
.form-group select,
.form-group textarea {
    width: 100%;
    padding: 10px 14px;
    border: 2px solid #e0e0e0;
    border-radius: 8px;
    font-size: 14px;
    transition: border-color 0.3s;
    outline: none;
}

.form-group input:focus,
.form-group select:focus,
.form-group textarea:focus {
    border-color: #e94560;
}

.form-group textarea {
    resize: vertical;
    min-height: 100px;
}

.form-submit-btn {
    width: 100%;
    padding: 12px;
    background: #e94560;
    color: white;
    border: none;
    border-radius: 8px;
    font-size: 15px;
    font-weight: 600;
    cursor: pointer;
    margin-top: 5px;
    transition: background 0.3s;
}

.form-submit-btn:hover {
    background: #c73652;
}

.form-link {
    text-align: center;
    margin-top: 15px;
    font-size: 13px;
    color: #666;
}

.form-link a {
    color: #e94560;
    font-weight: 600;
}

/* ============================================
   ALERTS
   ============================================ */
.alert {
    padding: 12px 18px;
    border-radius: 8px;
    margin-bottom: 18px;
    font-size: 14px;
}

.alert-success {
    background: #d4edda;
    color: #155724;
    border: 1px solid #c3e6cb;
}

.alert-error {
    background: #f8d7da;
    color: #721c24;
    border: 1px solid #f5c6cb;
}

/* ============================================
   TABLE (Admin panels)
   ============================================ */
.data-table {
    width: 100%;
    border-collapse: collapse;
    background: white;
    border-radius: 12px;
    overflow: hidden;
    box-shadow: 0 3px 15px rgba(0,0,0,0.07);
}

.data-table th {
    background: #1a1a2e;
    color: white;
    padding: 14px 16px;
    text-align: left;
    font-size: 13px;
    font-weight: 600;
}

.data-table td {
    padding: 12px 16px;
    font-size: 13px;
    border-bottom: 1px solid #f0f0f0;
    color: #444;
}

.data-table tr:hover td {
    background: #fafafa;
}

.data-table tr:last-child td {
    border-bottom: none;
}

/* ============================================
   ADMIN DASHBOARD STATS CARDS
   ============================================ */
.stats-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;
    margin-bottom: 35px;
}

.stat-card {
    background: white;
    border-radius: 12px;
    padding: 25px;
    text-align: center;
    box-shadow: 0 3px 15px rgba(0,0,0,0.07);
    border-top: 4px solid;
}

.stat-card.products { border-color: #007bff; }
.stat-card.orders   { border-color: #28a745; }
.stat-card.users    { border-color: #e94560; }

.stat-card .stat-number {
    font-size: 40px;
    font-weight: 700;
    margin-bottom: 5px;
}

.stat-card.products .stat-number { color: #007bff; }
.stat-card.orders   .stat-number { color: #28a745; }
.stat-card.users    .stat-number { color: #e94560; }

.stat-card .stat-label {
    font-size: 14px;
    color: #888;
    font-weight: 500;
}

/* ============================================
   ADMIN SIDEBAR NAVIGATION
   ============================================ */
.admin-layout {
    display: flex;
    gap: 25px;
}

.admin-sidebar {
    width: 220px;
    flex-shrink: 0;
    background: white;
    border-radius: 12px;
    padding: 20px;
    box-shadow: 0 3px 15px rgba(0,0,0,0.07);
    height: fit-content;
}

.admin-sidebar h3 {
    font-size: 13px;
    text-transform: uppercase;
    letter-spacing: 1px;
    color: #999;
    margin-bottom: 15px;
}

.admin-sidebar ul {
    list-style: none;
}

.admin-sidebar ul li {
    margin-bottom: 5px;
}

.admin-sidebar ul li a {
    display: block;
    padding: 10px 14px;
    border-radius: 8px;
    font-size: 14px;
    color: #444;
    transition: all 0.3s;
}

.admin-sidebar ul li a:hover,
.admin-sidebar ul li a.active {
    background: #1a1a2e;
    color: white;
}

.admin-content {
    flex: 1;
}

/* ============================================
   CART PAGE
   ============================================ */
.cart-layout {
    display: grid;
    grid-template-columns: 1fr 320px;
    gap: 25px;
    align-items: start;
}

.cart-item {
    display: flex;
    gap: 15px;
    padding: 18px;
    background: white;
    border-radius: 10px;
    margin-bottom: 12px;
    box-shadow: 0 2px 8px rgba(0,0,0,0.06);
    align-items: center;
}

.cart-item img {
    width: 80px;
    height: 80px;
    object-fit: cover;
    border-radius: 8px;
    background: #f0f0f0;
}

.cart-item-info {
    flex: 1;
}

.cart-item-info h3 {
    font-size: 15px;
    margin-bottom: 5px;
}

.cart-item-info .item-price {
    font-size: 16px;
    font-weight: 700;
    color: #e94560;
}

.cart-item-info .item-price::before {
    content: "₹";
}

.cart-item-info .item-qty {
    font-size: 12px;
    color: #888;
}

.order-summary {
    background: white;
    border-radius: 12px;
    padding: 25px;
    box-shadow: 0 3px 15px rgba(0,0,0,0.07);
}

.order-summary h3 {
    font-size: 16px;
    margin-bottom: 18px;
    padding-bottom: 12px;
    border-bottom: 1px solid #eee;
}

.summary-row {
    display: flex;
    justify-content: space-between;
    margin-bottom: 10px;
    font-size: 14px;
}

.summary-row.total {
    font-size: 18px;
    font-weight: 700;
    color: #e94560;
    border-top: 1px solid #eee;
    padding-top: 12px;
    margin-top: 12px;
}

/* ============================================
   PRODUCT DETAIL PAGE
   ============================================ */
.product-detail-layout {
    display: grid;
    grid-template-columns: 400px 1fr;
    gap: 35px;
    background: white;
    border-radius: 12px;
    padding: 30px;
    box-shadow: 0 3px 15px rgba(0,0,0,0.07);
}

.product-detail-img {
    width: 100%;
    height: 350px;
    object-fit: cover;
    border-radius: 10px;
    background: #f0f0f0;
}

.product-detail-info h2 {
    font-size: 24px;
    margin-bottom: 10px;
}

.product-detail-info .detail-price {
    font-size: 28px;
    font-weight: 700;
    color: #e94560;
    margin-bottom: 12px;
}

.product-detail-info .detail-price::before {
    content: "₹";
}

.product-detail-info .detail-desc {
    font-size: 14px;
    color: #666;
    line-height: 1.7;
    margin-bottom: 18px;
}

.product-detail-info .detail-stock {
    font-size: 13px;
    margin-bottom: 20px;
}

/* ============================================
   SUCCESS PAGE
   ============================================ */
.success-box {
    text-align: center;
    background: white;
    border-radius: 12px;
    padding: 50px 30px;
    box-shadow: 0 3px 15px rgba(0,0,0,0.07);
    max-width: 500px;
    margin: 0 auto;
}

.success-box .checkmark {
    font-size: 60px;
    color: #28a745;
    margin-bottom: 15px;
}

.success-box h2 {
    font-size: 24px;
    color: #1a1a2e;
    margin-bottom: 10px;
}

.success-box p {
    font-size: 14px;
    color: #666;
    margin-bottom: 6px;
}

.success-box .order-id {
    font-size: 18px;
    font-weight: 700;
    color: #e94560;
}

/* ============================================
   RESPONSIVE
   ============================================ */
@media (max-width: 768px) {
    .stats-grid { grid-template-columns: 1fr; }
    .cart-layout { grid-template-columns: 1fr; }
    .product-detail-layout { grid-template-columns: 1fr; }
    .admin-layout { flex-direction: column; }
    .admin-sidebar { width: 100%; }
    .navbar { padding: 15px 20px; }
}

```
---
