# JDBC executeQuery() and executeUpdate() – Complete Notes

# 1. What is JDBC?

JDBC stands for **Java Database Connectivity**.

JDBC is used to connect Java applications with databases like:

* MySQL
* Oracle
* PostgreSQL
* SQL Server

Using JDBC we can:

* Insert data
* Retrieve data
* Update data
* Delete data

---

# 2. Important JDBC Steps

## Step 1: Import Packages

```java
import java.sql.*;
```

---

## Step 2: Load Driver

```java
Class.forName("com.mysql.cj.jdbc.Driver");
```

This loads MySQL JDBC Driver.

---

## Step 3: Create Connection

```java
Connection con = DriverManager.getConnection(
    "jdbc:mysql://localhost:3306/studentdb",
    "root",
    "password"
);
```

### Explanation

* `localhost` → Database running in same system
* `3306` → MySQL port number
* `studentdb` → Database name
* `root` → Username
* `password` → MySQL password

---

## Step 4: Create Statement

```java
Statement st = con.createStatement();
```

Statement is used to execute SQL queries.

---

# 3. executeQuery()

## Definition

`executeQuery()` is used to retrieve data from database.

It is mainly used with:

* SELECT query

---

# Syntax

```java
ResultSet rs = st.executeQuery("SELECT * FROM students");
```

---

# Important Point

`executeQuery()` always returns a:

```java
ResultSet
```

Object.

---

# What is ResultSet?

`ResultSet` stores data returned from database.

Think like:

Database table data comes into Java and is stored inside ResultSet.

---

# Example Table

## students

| id | name | marks |
| -- | ---- | ----- |
| 1  | Ram  | 90    |
| 2  | Sita | 85    |
| 3  | Ravi | 70    |

When query executes:

```sql
SELECT * FROM students
```

All rows are stored inside `ResultSet rs`.

---

# Full Program Using executeQuery()

```java
import java.sql.*;

public class SelectDemo {
    public static void main(String[] args) {

        try {

            // Load Driver
            Class.forName("com.mysql.cj.jdbc.Driver");

            // Create Connection
            Connection con = DriverManager.getConnection(
                "jdbc:mysql://localhost:3306/studentdb",
                "root",
                "password"
            );

            // Create Statement
            Statement st = con.createStatement();

            // Execute Query
            ResultSet rs = st.executeQuery("SELECT * FROM students");

            // Fetch Data
            while(rs.next()) {

                int id = rs.getInt("id");
                String name = rs.getString("name");
                int marks = rs.getInt("marks");

                System.out.println(id + " " + name + " " + marks);
            }

            // Close Connection
            con.close();

        } catch(Exception e) {
            System.out.println(e);
        }
    }
}
```

---

# 4. Understanding while(rs.next())

This is MOST IMPORTANT.

```java
while(rs.next())
```

---

# What does rs.next() do?

`rs.next()` moves cursor to next row.

It checks:

* Is next row available?
* If available → returns TRUE
* If no rows → returns FALSE

---

# Cursor Concept

Initially cursor is before first row.

| Cursor Position |
| --------------- |
| Before Row 1    |

---

## First rs.next()

Cursor moves to Row 1

| id | name | marks |
| -- | ---- | ----- |
| 1  | Ram  | 90    |

Returns:

```java
true
```

---

## Second rs.next()

Cursor moves to Row 2

| id | name | marks |
| -- | ---- | ----- |
| 2  | Sita | 85    |

Returns:

```java
true
```

---

## Third rs.next()

Cursor moves to Row 3

Returns:

```java
true
```

---

## Fourth rs.next()

No more rows.

Returns:

```java
false
```

Loop stops.

---

# Visualization

```java
while(rs.next())
```

Means:

```java
Move to next row
If row exists:
    execute code
Else:
    stop loop
```

---

# Fetching Data from ResultSet

## Integer Data

```java
rs.getInt("id");
```

---

## String Data

```java
rs.getString("name");
```

---

## Float Data

```java
rs.getFloat("salary");
```

---

# We can also use column index

```java
rs.getInt(1);
rs.getString(2);
```

But column names are better and readable.

---

# 5. executeUpdate()

## Definition

`executeUpdate()` is used for:

* INSERT
* UPDATE
* DELETE

---

# Important Point

`executeUpdate()` returns integer value.

That integer represents:

```java
Number of rows affected
```

---

# Syntax

```java
int rows = st.executeUpdate(query);
```

---

# 6. INSERT Example

## SQL Query

```sql
INSERT INTO students VALUES(4, 'Kiran', 88)
```

---

# Java Program

```java
import java.sql.*;

public class InsertDemo {

    public static void main(String[] args) {

        try {

            // Load Driver
            Class.forName("com.mysql.cj.jdbc.Driver");

            // Connection
            Connection con = DriverManager.getConnection(
                "jdbc:mysql://localhost:3306/studentdb",
                "root",
                "password"
            );

            // Statement
            Statement st = con.createStatement();

            // Insert Query
            String query = "INSERT INTO students VALUES(4, 'Kiran', 88)";

            // Execute Update
            int rows = st.executeUpdate(query);

            // Output
            System.out.println(rows + " row inserted");

            con.close();

        } catch(Exception e) {
            System.out.println(e);
        }
    }
}
```

---

# Output

```java
1 row inserted
```

---

# Why output is 1?

Because:

* One row inserted into database.

---

# 7. UPDATE Example

## SQL Query

```sql
UPDATE students SET marks = 95 WHERE id = 1
```

---

# Java Program

```java
import java.sql.*;

public class UpdateDemo {

    public static void main(String[] args) {

        try {

            Class.forName("com.mysql.cj.jdbc.Driver");

            Connection con = DriverManager.getConnection(
                "jdbc:mysql://localhost:3306/studentdb",
                "root",
                "password"
            );

            Statement st = con.createStatement();

            String query =
                "UPDATE students SET marks = 95 WHERE id = 1";

            int rows = st.executeUpdate(query);

            System.out.println(rows + " row updated");

            con.close();

        } catch(Exception e) {
            System.out.println(e);
        }
    }
}
```

---

# Output

```java
1 row updated
```

---

# 8. DELETE Example

## SQL Query

```sql
DELETE FROM students WHERE id = 3
```

---

# Java Program

```java
import java.sql.*;

public class DeleteDemo {

    public static void main(String[] args) {

        try {

            Class.forName("com.mysql.cj.jdbc.Driver");

            Connection con = DriverManager.getConnection(
                "jdbc:mysql://localhost:3306/studentdb",
                "root",
                "password"
            );

            Statement st = con.createStatement();

            String query =
                "DELETE FROM students WHERE id = 3";

            int rows = st.executeUpdate(query);

            System.out.println(rows + " row deleted");

            con.close();

        } catch(Exception e) {
            System.out.println(e);
        }
    }
}
```

---

# Output

```java
1 row deleted
```

---

# Difference Between executeQuery() and executeUpdate()

| executeQuery()         | executeUpdate()                 |
| ---------------------- | ------------------------------- |
| Used for SELECT        | Used for INSERT, UPDATE, DELETE |
| Returns ResultSet      | Returns int                     |
| Retrieves data         | Modifies data                   |
| Used with SELECT query | Used with non-select queries    |

---

# Important Interview Questions

## Q1. What does executeQuery() return?

Answer:

```java
ResultSet
```

---

## Q2. What does executeUpdate() return?

Answer:

```java
int
```

(Number of rows affected)

---

## Q3. Why do we use rs.next()?

Answer:
To move cursor to next row and check whether row exists or not.

---

## Q4. What happens if rs.next() is not used?

Answer:
Cursor stays before first row and data cannot be accessed.

---

# Real Time Flow

```java
Database Table
        ↓
executeQuery()
        ↓
ResultSet rs
        ↓
while(rs.next())
        ↓
Fetch each row data
        ↓
Display Output
```

---

# Simple Memory Trick

## executeQuery()

Q → Query → SELECT → Returns ResultSet

---

## executeUpdate()

U → Update Database → INSERT/UPDATE/DELETE → Returns int

---

# Final Summary

## executeQuery()

* Used for SELECT
* Returns ResultSet
* Data retrieval operation

---

## ResultSet

* Stores database records
* rs.next() moves row by row

---

## executeUpdate()

* Used for INSERT
* Used for UPDATE
* Used for DELETE
* Returns number of rows affected

---

