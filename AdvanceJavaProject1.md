# PROJECT NAME

**InstagramRegestration**

---

# PROJECT STRUCTURE

```text
InstagramRegestration
│
├── Java Resources
│   │
│   └── src/main/java
│       │
│       └── com.instagram
│           │
│           ├── DBConnection.java
│           │
│           └── RegistrationServlet.java
│
├── src/main/webapp
│   │
│   ├── Regester.html
│   │
│   └── WEB-INF
│       │
│       └── web.xml
│
└── mysql-connector-j-8.0.xx.jar
```

---

# STEP 1

# CREATE DATABASE

```sql
CREATE DATABASE instagramdb;
```

---

# USE DATABASE

```sql
USE instagramdb;
```

---

# CREATE TABLE

```sql
CREATE TABLE users
(
    id INT PRIMARY KEY AUTO_INCREMENT,

    username VARCHAR(50),

    email VARCHAR(100),

    phone VARCHAR(20),

    password VARCHAR(100)
);
```

---

# STEP 2

# Regester.html

Location

```text
src/main/webapp
```

Code

```html
<!DOCTYPE html>
<html>

<head>

<meta charset="UTF-8">

<title>Instagram Registration</title>

</head>

<body>

<h1>Create Instagram Account</h1>

<form action="Regester" method="post">

Username :

<input type="text"
       name="username">

<br><br>

Email :

<input type="email"
       name="email">

<br><br>

Phone :

<input type="text"
       name="phone">

<br><br>

Password :

<input type="password"
       name="password">

<br><br>

<input type="submit"
       value="Create Account">

</form>

</body>

</html>
```

---

# STEP 3

# DBConnection.java

Location

```text
com.instagram
```

Code

```java
package com.instagram;

import java.sql.Connection;
import java.sql.DriverManager;

public class DBConnection {

    public static Connection getConnection() {

        Connection con = null;

        try {

            Class.forName(
                    "com.mysql.cj.jdbc.Driver");

            con =
                DriverManager.getConnection(
                    "jdbc:mysql://localhost:3306/instagramdb",
                    "root",
                    "root");

        }

        catch(Exception e) {

            e.printStackTrace();

        }

        return con;
    }
}
```

**Change root/root according to your MySQL username and password**

---

# STEP 4

# RegistrationServlet.java

Location

```text
com.instagram
```

Code

```java
package com.instagram;

import java.io.IOException;

import java.sql.Connection;
import java.sql.PreparedStatement;

import javax.servlet.ServletException;

import javax.servlet.annotation.WebServlet;

import javax.servlet.http.HttpServlet;

import javax.servlet.http.HttpServletRequest;

import javax.servlet.http.HttpServletResponse;

@WebServlet("/Regester")

public class RegistrationServlet
       extends HttpServlet {

    private static final long serialVersionUID = 1L;

    @Override

    protected void doPost(
            HttpServletRequest request,
            HttpServletResponse response)

            throws ServletException,
                   IOException {

        String username =
                request.getParameter(
                        "username");

        String email =
                request.getParameter(
                        "email");

        String phone =
                request.getParameter(
                        "phone");

        String password =
                request.getParameter(
                        "password");

        System.out.println();

        System.out.println(
                "===== USER DATA =====");

        System.out.println(
                "Username : " + username);

        System.out.println(
                "Email : " + email);

        System.out.println(
                "Phone : " + phone);

        System.out.println(
                "Password : " + password);

        try {

            Connection con =
                    DBConnection
                    .getConnection();

            String sql =

                "INSERT INTO users"
              + "(username,email,phone,password)"
              + " VALUES(?,?,?,?)";

            PreparedStatement ps =
                    con.prepareStatement(
                            sql);

            ps.setString(
                    1,
                    username);

            ps.setString(
                    2,
                    email);

            ps.setString(
                    3,
                    phone);

            ps.setString(
                    4,
                    password);

            int rows =
                    ps.executeUpdate();

            if(rows > 0) {

                System.out.println(
                    "DATA INSERTED SUCCESSFULLY");

            }

            else {

                System.out.println(
                    "DATA INSERTION FAILED");
            }

            con.close();

        }

        catch(Exception e) {

            e.printStackTrace();
        }

        response.sendRedirect(
                "Regester.html");
    }
}
```

---

# STEP 5

# web.xml

Location

```text
WEB-INF
```

Code

```xml
<?xml version="1.0" encoding="UTF-8"?>

<web-app
xmlns="http://xmlns.jcp.org/xml/ns/javaee"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"

xsi:schemaLocation=
"http://xmlns.jcp.org/xml/ns/javaee
http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"

version="4.0">

<display-name>
InstagramRegestration
</display-name>

<welcome-file-list>

<welcome-file>
Regester.html
</welcome-file>

</welcome-file-list>

</web-app>
```

---

# STEP 6

# ADD MYSQL CONNECTOR

Download:

```text
mysql-connector-j-8.x.x.jar
```

Add to project:

```text
Project
 ↓
Properties
 ↓
Java Build Path
 ↓
Libraries
 ↓
Add External JARs
```

Select:

```text
mysql-connector-j-8.x.x.jar
```

---

# RUN PROJECT

Open

```text
http://localhost:8080/InstagramRegestration/
```

Because of welcome file it automatically loads:

```text
Regester.html
```

---

# FLOW

```text
User
 ↓
Regester.html
 ↓
Fill Form
 ↓
Submit
 ↓
RegistrationServlet
 ↓
request.getParameter()
 ↓
Java Variables
 ↓
PreparedStatement
 ↓
executeUpdate()
 ↓
MySQL Database
 ↓
users Table
```

---

# VERIFY DATA

```sql
SELECT * FROM users;
```

Output:

```text
+----+----------+------------------+------------+----------+
| id | username | email            | phone      | password |
+----+----------+------------------+------------+----------+
| 1  | Mahesh   | mahesh@gmail.com | 9876543210 | 12345    |
+----+----------+------------------+------------+----------+
```

