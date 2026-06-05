
# JDBC INSERT OPERATION

## What is JDBC?

**JDBC (Java Database Connectivity)** is an API that allows Java applications to communicate with databases.

Using JDBC we can:

* Insert Data
* Read Data
* Update Data
* Delete Data

These operations are called **CRUD Operations**.

* C → Create (Insert)
* R → Read (Select)
* U → Update
* D → Delete

---

# Steps to Insert Data into MySQL

### Step 1: Import Package

```java
import java.sql.*;
```

Used to access JDBC classes.

---

### Step 2: Load Driver

```java
Class.forName("com.mysql.cj.jdbc.Driver");
```

Loads MySQL JDBC Driver into memory.

---

### Step 3: Establish Connection

```java
Connection con = DriverManager.getConnection(
    "jdbc:mysql://localhost:3306/studentdb",
    "root",
    "root"
);
```

Creates connection between Java Application and MySQL Database.

---

### Step 4: Create Statement

```java
Statement st = con.createStatement();
```

Statement object sends SQL queries to database.

---

### Step 5: Execute Query

```java
int rows = st.executeUpdate(sql);
```

Used for:

* INSERT
* UPDATE
* DELETE

Returns number of affected rows.

---

### Step 6: Close Resources

```java
con.close();
```

Closes database connection.

---

# Example 1: Insert Data Without Scanner

### Database Table

```sql
CREATE TABLE student(
    id INT,
    name VARCHAR(50),
    city VARCHAR(50)
);
```

---

### Java Program

```java
import java.sql.*;

public class InsertDemo {

    public static void main(String[] args) {

        try {

            // Load Driver
            Class.forName("com.mysql.cj.jdbc.Driver");

            // Create Connection
            Connection con = DriverManager.getConnection(
                    "jdbc:mysql://localhost:3306/studentdb",
                    "root",
                    "root");

            // Create Statement
            Statement st = con.createStatement();

            // SQL Query
            String sql =
                    "insert into student values(101,'Mahesh','Vijayawada')";

            // Execute Query
            int rows = st.executeUpdate(sql);

            System.out.println(rows + " Record Inserted Successfully");

            // Close Connection
            con.close();

        } catch(Exception e) {
            System.out.println(e);
        }
    }
}
```

---

# Output

```text
1 Record Inserted Successfully
```

---

# Flow Diagram

```text
Java Program
      ↓
Load Driver
      ↓
Create Connection
      ↓
Create Statement
      ↓
Execute INSERT Query
      ↓
Data Stored in MySQL
      ↓
Close Connection
```

---

# Example 2: Insert Data Using Scanner

Now data will be taken from the user at runtime.

---

### Java Program

```java
import java.sql.*;
import java.util.Scanner;

public class InsertScanner {

    public static void main(String[] args) {

        try {

            Scanner sc = new Scanner(System.in);

            System.out.print("Enter Id : ");
            int id = sc.nextInt();

            sc.nextLine();

            System.out.print("Enter Name : ");
            String name = sc.nextLine();

            System.out.print("Enter City : ");
            String city = sc.nextLine();

            // Load Driver
            Class.forName("com.mysql.cj.jdbc.Driver");

            // Create Connection
            Connection con = DriverManager.getConnection(
                    "jdbc:mysql://localhost:3306/studentdb",
                    "root",
                    "root");

            // Create Statement
            Statement st = con.createStatement();

            // SQL Query
            String sql =
                    "insert into student values(" +
                    id +
                    ",'" +
                    name +
                    "','" +
                    city +
                    "')";

            // Execute Query
            int rows = st.executeUpdate(sql);

            System.out.println(rows + " Record Inserted Successfully");

            // Close Connection
            con.close();

        } catch(Exception e) {
            System.out.println(e);
        }
    }
}
```

---

# Sample Output

```text
Enter Id : 102
Enter Name : Ravi
Enter City : Hyderabad

1 Record Inserted Successfully
```

---

# Important Interview Questions

### What is JDBC?

JDBC is a Java API used to connect Java applications with databases.

---

### Why do we use executeUpdate()?

Used for:

* INSERT
* UPDATE
* DELETE

Returns number of affected rows.

---

### Why do we use executeQuery()?

Used for:

```sql
SELECT
```

Returns ResultSet object.

---

### What is Connection?

Connection interface establishes communication between Java application and database.

---

### What is Statement?

Statement interface is used to execute SQL queries.

---

### Which method inserts data?

```java
executeUpdate()
```

---

### Return type of executeUpdate()?

```java
int
```

It returns number of affected rows.

---

### One-line Definition for Class

**JDBC:** JDBC is an API used to establish communication between Java applications and databases.

**Driver:** Driver is software that enables communication between Java and a database.

**Connection:** Connection represents a session between Java application and database.

**Statement:** Statement is used to execute SQL queries.

**executeUpdate():** Executes INSERT, UPDATE, DELETE queries and returns affected row count.


**Driver → Connection → Statement → SQL Query → executeUpdate() → Database**.

