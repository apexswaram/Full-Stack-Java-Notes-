
# Project 2 - READ Operation

## Objective

Display all registered users from MySQL in an HTML table.

### Flow

```text
Database
   ↓
ViewUsersServlet
   ↓
executeQuery()
   ↓
ResultSet
   ↓
while(rs.next())
   ↓
HTML Table
   ↓
Browser
```

---

# Database Table
 you have already created this no need to create it agian
```sql
CREATE TABLE INSTAGRAM_USERS
(
    ID INT PRIMARY KEY AUTO_INCREMENT,

    USERNAME VARCHAR(50),

    EMAIL VARCHAR(100),

    PHONE VARCHAR(20),

    PASSWORD VARCHAR(50)
);
```

---

# Project Structure

```text
InstagramRegistration

src/main/java

 com.instagram

   -- DBConnect.java

   -- RegistrationServlet.java

   -- ViewUsersServlet.java

src/main/webapp

   -- Regester.html

   -- ViewUsers.html

WEB-INF

web.xml
```

---

# DBConnect.java

```java
package com.instagram;

import java.sql.Connection;
import java.sql.DriverManager;

public class DBConnect {

    public static Connection getConnection() {

        Connection con = null;

        try {

            Class.forName("com.mysql.cj.jdbc.Driver");

            con = DriverManager.getConnection(
                    "jdbc:mysql://localhost:3306/INSTAGRAM",
                    "root",
                    "Subbu@2004");

        }

        catch(Exception e) {

            e.printStackTrace();
        }

        return con;
    }
}
```

---

# ViewUsers.html

```html
<!DOCTYPE html>
<html>

<head>
<meta charset="UTF-8">
<title>View Users</title>
</head>

<body>

<h1>Instagram Users</h1>

<a href="viewusers">
    View All Users
</a>

</body>

</html>
```

---

# ViewUsersServlet.java

```java
package com.instagram;

import java.io.IOException;
import java.io.PrintWriter;

import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;

import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

@WebServlet("/viewusers")

public class ViewUsersServlet extends HttpServlet {

    private static final long serialVersionUID = 1L;

    @Override

    protected void doGet(
            HttpServletRequest request,
            HttpServletResponse response)

            throws ServletException,
                   IOException {

        response.setContentType("text/html");

        PrintWriter out =
                response.getWriter();

        out.println("<html>");
        out.println("<body>");

        out.println("<h1>Instagram Users</h1>");

        out.println("<table border='1'>");

        out.println(
                "<tr>"
              + "<th>ID</th>"
              + "<th>USERNAME</th>"
              + "<th>EMAIL</th>"
              + "<th>PHONE</th>"
              + "</tr>");

        try {

            Connection con =
                    DBConnect.getConnection();

            String sql =
                    "SELECT * FROM INSTAGRAM_USERS";

            PreparedStatement ps =
                    con.prepareStatement(sql);

            ResultSet rs =
                    ps.executeQuery();

            while(rs.next()) {

                out.println("<tr>");

                out.println(
                        "<td>"
                        + rs.getInt("id")
                        + "</td>");

                out.println(
                        "<td>"
                        + rs.getString("username")
                        + "</td>");

                out.println(
                        "<td>"
                        + rs.getString("email")
                        + "</td>");

                out.println(
                        "<td>"
                        + rs.getString("phone")
                        + "</td>");

                out.println("</tr>");
            }

            con.close();

        }

        catch(Exception e) {

            e.printStackTrace();
        }

        out.println("</table>");

        out.println("</body>");
        out.println("</html>");
    }
}
```

---

# How executeQuery Works

```java
ResultSet rs =
        ps.executeQuery();
```

Purpose:

```text
Fetch records
from database
```

Used with:

```sql
SELECT
```

---

# How ResultSet Works

```java
ResultSet rs
```

Stores all rows returned from database.

Example:

```text
ID  USERNAME

1   Mahesh

2   Sai

3   Nikhil
```

All rows stored inside:

```java
rs
```

---

# How while(rs.next()) Works

```java
while(rs.next())
```

Moves row by row.

### First Iteration

```text
ID = 1

USERNAME = Mahesh
```

### Second Iteration

```text
ID = 2

USERNAME = Sai
```

### Third Iteration

```text
ID = 3

USERNAME = Nikhil
```

### Fourth Iteration

No row exists

Returns:

```text
false
```

Loop stops.

---

# Reading Values

```java
rs.getInt("id")
```

Reads ID.

---

```java
rs.getString("username")
```

Reads username.

---

```java
rs.getString("email")
```

Reads email.

---

```java
rs.getString("phone")
```

Reads phone.

---

# Run

Open:

```text
http://localhost:8080/InstagramRegistration/ViewUsers.html
```

Click:

```text
View All Users
```

---

# Output

```text
------------------------------------
ID   USERNAME   EMAIL       PHONE
------------------------------------

1    Mahesh     abc@gmail   987654

2    Sai        sai@gmail   999999

3    Nikhil     nik@gmail   888888
```

---


Flow :

```text
Frontend
    ↓
Servlet
    ↓
SELECT Query
    ↓
executeQuery()
    ↓
ResultSet
    ↓
while(rs.next())
    ↓
HTML Table
```
