# Day 7 — Hibernate Introduction (ORM, Architecture, JDBC vs Hibernate)

## Objectives
By the end of this class, students should be able to:
- Explain what ORM is and the problem it solves
- Compare JDBC and Hibernate with real code side by side
- Understand Hibernate's core architecture and the role of each component
- Understand the plan for the rest of the Hibernate module (Days 8–15)

## Quick Recap of the JSP Module (Days 1–6)
- Days 1–6 covered: JSP life cycle, scripting elements, implicit objects, directives, EL, JSTL, forms, forward/redirect, session tracking, and a full mini project (Student Portal) using `application` scope as a fake in-memory database.
- Today we start replacing that fake in-memory `List`/`Map` storage with a **real database**, using Hibernate instead of writing raw JDBC code.

---

## 1. The Problem: Why Do We Need Hibernate?

In the Day 6 mini project, we stored students in a `List<Map<String,String>>` inside `application` scope. This has serious real-world problems:
- **Data is lost when the server restarts** — nothing is saved permanently.
- **Doesn't scale** — can't handle real data volumes or multiple servers.
- **No relationships** — can't easily model "a student has many enrollments" etc.

The fix: store data in a **relational database** (MySQL, in our case). But talking to a database directly from Java has its own pain points — let's see this with JDBC first.

### 1.1 The JDBC Way (What We're Moving Away From)

**Full JDBC Example — inserting a student into a database:**

```java
import java.sql.*;

public class StudentJdbcDemo {
    public static void main(String[] args) {
        String url = "jdbc:mysql://localhost:3306/studentdb";
        String user = "root";
        String password = "root123";

        try {
            Class.forName("com.mysql.cj.jdbc.Driver");
            Connection con = DriverManager.getConnection(url, user, password);

            String sql = "INSERT INTO student (name, username, course) VALUES (?, ?, ?)";
            PreparedStatement ps = con.prepareStatement(sql);
            ps.setString(1, "Ravi Kumar");
            ps.setString(2, "ravi123");
            ps.setString(3, "Java Full Stack");

            int rows = ps.executeUpdate();
            System.out.println(rows + " row(s) inserted.");

            ps.close();
            con.close();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Problems with this approach (walk through each line and point these out):**
1. We manually write raw SQL as a `String` — no compile-time checking, easy to make typos that only fail at runtime.
2. We manually map each Java field to a `?` placeholder, in the exact right order — very error-prone as tables grow.
3. To fetch data back, we'd have to manually loop through a `ResultSet` and build Java objects field by field (show this briefly):

```java
String sql = "SELECT * FROM student";
Statement st = con.createStatement();
ResultSet rs = st.executeQuery(sql);
while (rs.next()) {
    String name = rs.getString("name");
    String username = rs.getString("username");
    String course = rs.getString("course");
    // manually build a Student object here...
}
```
4. Connection management, exception handling, and closing resources are all manual and repeated in every single class that talks to the database.
5. If we add a new column to the table, we must update SQL strings and mapping code **everywhere** in the project.

### 1.2 What ORM Means

**ORM = Object Relational Mapping.**
- It's a technique that automatically maps **Java objects (classes)** to **database tables**, and **object fields** to **table columns** — so we work with normal Java objects, and the ORM framework generates and runs the SQL for us behind the scenes.

| Java World | Database World |
|---|---|
| Class (e.g. `Student`) | Table (e.g. `student`) |
| Object (instance of `Student`) | Row in the table |
| Field (e.g. `name`) | Column (e.g. `name`) |

**Hibernate** is the most widely used ORM framework for Java. It sits between our Java application and the database, and converts our Java object operations (save, get, update, delete) into the correct SQL automatically.

---

## 2. JDBC vs Hibernate — Full Comparison

| Aspect | JDBC | Hibernate |
|---|---|---|
| SQL | Written manually by developer | Generated automatically by Hibernate |
| Object mapping | Manual (field by field) | Automatic, via annotations or XML mapping |
| Database independence | SQL is often database-specific | Same Java code works across databases (MySQL, Oracle, PostgreSQL, etc.) with minimal config change |
| Caching | Not built-in | Built-in first-level (and optional second-level) caching — improves performance |
| Boilerplate code | High (connections, statements, result sets, closing resources) | Low — Hibernate manages most of this internally |
| Relationships (one-to-many etc.) | Manual joins and manual object building | Declared via annotations, Hibernate handles the joins |

**Key teaching point:** Hibernate doesn't replace the database or SQL — it just **generates SQL for us** and **maps results back into Java objects automatically**, saving huge amounts of repetitive code.

---

## 3. Hibernate Architecture — Core Components

Draw this as a simple top-to-bottom diagram on the board while explaining:

```
Java Application
       │
       ▼
Configuration  (reads hibernate.cfg.xml — DB connection details, mapped classes)
       │
       ▼
SessionFactory  (heavyweight object, created ONCE per application, thread-safe)
       │
       ▼
Session  (lightweight, created per unit of work/request, NOT thread-safe)
       │
       ▼
Transaction  (begin/commit/rollback — wraps a set of operations)
       │
       ▼
Database (via JDBC underneath — Hibernate still uses JDBC internally, just hides it from us)
```

### 3.1 Component-by-Component Explanation

| Component | Role |
|---|---|
| **Configuration** | Reads settings from `hibernate.cfg.xml` — DB URL, username, password, driver class, dialect, and which entity classes to map. |
| **SessionFactory** | A heavyweight, thread-safe object built once from `Configuration`. Think of it as a factory that produces `Session` objects. Expensive to create — created only **once** when the application starts. |
| **Session** | A lightweight, single-threaded object representing **one unit of work** with the database (like one JDBC `Connection`, conceptually). We get a new `Session` per operation/request, use it, then close it. This is where we call `save()`, `get()`, `update()`, `delete()` (covered in detail Day 10). |
| **Transaction** | Represents a database transaction — wraps our operations so they either **all succeed** (commit) or **all fail together** (rollback), keeping data consistent. |
| **Query / Criteria** | Hibernate's own query mechanisms — HQL (Hibernate Query Language) and Criteria API — used for more complex data retrieval (covered Day 11). |

**Analogy to help students remember:** `SessionFactory` is like a water treatment plant (built once, expensive, produces clean water continuously). `Session` is like a glass of water poured from it (cheap, used once, then done/refilled). We'll build the actual `SessionFactory` code on Day 8.

---

## 4. Where Hibernate Fits in Our Full Stack

Connect this back to the whole course so far:

```
JSP (View)  →  Servlet (Controller)  →  Hibernate (Data Access / Model)  →  Database
```

- JSP (Days 1–6): displays data to the user.
- Servlet (covered earlier in the course, before this module): handles requests, contains business logic.
- **Hibernate (starting today)**: replaces raw JDBC in the data-access layer — this is exactly the layer that talked to the database in any Servlet-based project students have seen so far.
- By Day 14's mini project, students will rebuild something similar to the Day 6 "Student Portal" — but backed by a **real MySQL database via Hibernate**, instead of the temporary `application`-scope `List`.

---

## 5. Setting Up for Hibernate (Preview — Full Setup Happens Day 8)

Just show students what's coming, don't build it fully today:
- Add Hibernate + MySQL Connector dependencies (via Maven `pom.xml`)
- Create `hibernate.cfg.xml` (DB connection configuration)
- Create an **entity class** (a Java class mapped to a table, using annotations like `@Entity`, `@Table`, `@Id`)
- Build the `SessionFactory` and perform a first save operation

This keeps today focused purely on **why Hibernate exists and how it's structured**, so Day 8's setup makes immediate sense.

---

## 6. In-Class Activity (Discussion-Based, No Coding Today)
Split students into small groups and ask them to answer, then share with the class:
1. List 3 pain points of JDBC that Hibernate solves (referencing the code example in Section 1.1).
2. In your own words, explain the difference between `SessionFactory` and `Session`.
3. Where would Hibernate fit if you were rebuilding the Day 6 "Student Portal" project with a real database?

## 7. Recap Questions (End of Class)
1. What does ORM stand for, and what problem does it solve?
2. Name 3 differences between JDBC and Hibernate.
3. Which Hibernate component is created once per application, and which is created per unit of work?
4. What role does `hibernate.cfg.xml` play in the architecture?

## 8. Homework
- No coding homework today — instead, ask students to have MySQL installed and running before Day 8 (we'll connect to it live in the next class). Provide install instructions separately if needed.
- Optional reading: skim the term "dialect" in Hibernate (e.g. `MySQLDialect`) — we'll use it directly in `hibernate.cfg.xml` on Day 8.

---
*Prepared for JFS Batch 2 — Day 7 of 15 (JSP & Hibernate Module) — Start of Hibernate Section*
