# Day 8 — Hibernate Setup (Complete, File-by-File)

## A Note Before We Start (Read This First)
Unlike JSP, where one `.jsp` file could show a full working concept, **Hibernate needs multiple files working together** before we see any result — a dependency file, a config file, an entity class, a utility class, and a main class that ties it all together. Today we build **all of these, one at a time, explaining exactly what each one does and why it exists**, before running anything. Do not skip a file thinking "it's just boilerplate" — each one is explained in full below because in Hibernate, understanding what each file's *job* is matters more than memorizing syntax.

## Objectives
By the end of this class, students should be able to:
- Explain the exact role of every file involved in a basic Hibernate setup
- Set up a Maven project with Hibernate + MySQL dependencies from scratch
- Write a correct `hibernate.cfg.xml`
- Write a properly annotated Entity class
- Write a `SessionFactory` utility class (the correct, reusable way — not repeated in every class)
- Run a first working Hibernate program that saves a row into a real MySQL database

## Quick Recap of Day 7
- ORM = mapping Java objects/classes to database tables/rows automatically
- Hibernate architecture: `Configuration` → `SessionFactory` (once) → `Session` (per operation) → `Transaction`
- Hibernate still uses JDBC internally — it just hides the repetitive parts from us
- Ask 2 students to explain `SessionFactory` vs `Session` in their own words before starting today.

---

## 1. Prerequisites Check (Do This First, Live, With the Whole Class)

Before writing a single line of Hibernate code, confirm every student has:
1. **MySQL Server installed and running** (via XAMPP, MySQL Workbench, or standalone MySQL service — whatever was set up for this batch).
2. **A database created** for today's demo:

```sql
CREATE DATABASE studentdb;
```

3. Run this and confirm it shows up:
```sql
SHOW DATABASES;
```

**Important:** We do NOT need to manually create the `student` table — Hibernate will auto-generate it for us today, based on our entity class. This is intentional and will be explained in Section 4 (`hibernate.cfg.xml`, `hbm2ddl.auto` setting) — flag this now so students aren't confused when no table exists yet.

---

## 2. Project Structure — The Big Picture First

Before diving into each file, show students the full folder structure so they know **where each piece lives** and can mentally map back to it as we go:

```
StudentHibernateDemo (Maven Project)
│
├── pom.xml                                  ← File 1: Dependencies
│
└── src/main/java
    ├── resources/
    │   └── hibernate.cfg.xml                ← File 2: Configuration
    │
    └── com/apexswaram/hibernate/
        ├── entity/
        │   └── Student.java                 ← File 3: Entity class
        ├── util/
        │   └── HibernateUtil.java           ← File 4: SessionFactory utility
        └── main/
            └── StudentSaveDemo.java         ← File 5: Main class — runs everything
```

**Why so many files?** Each file has exactly ONE job (this is a good moment to connect to "separation of concerns," a term students may already know from MVC in Servlets/JSP):
- `pom.xml` → tells Maven WHAT libraries to download
- `hibernate.cfg.xml` → tells Hibernate HOW to connect to the database
- `Student.java` → tells Hibernate WHAT Java class maps to WHAT table
- `HibernateUtil.java` → creates the `SessionFactory` ONCE and hands it out whenever needed
- `StudentSaveDemo.java` → actually USES all of the above to save data

Keep referring back to this list as we go through each file below.

---

## 3. File 1 — `pom.xml` (Maven Dependencies)

**Its job:** Tell Maven which JAR libraries our project needs, so Maven downloads them automatically instead of us manually hunting for `.jar` files (like we might have done for JDBC earlier in the course).

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
         http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.apexswaram</groupId>
    <artifactId>StudentHibernateDemo</artifactId>
    <version>1.0</version>
    <packaging>jar</packaging>

    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Hibernate Core -->
        <dependency>
            <groupId>org.hibernate.orm</groupId>
            <artifactId>hibernate-core</artifactId>
            <version>6.4.4.Final</version>
        </dependency>

        <!-- MySQL Connector/J -->
        <dependency>
            <groupId>com.mysql</groupId>
            <artifactId>mysql-connector-j</artifactId>
            <version>8.3.0</version>
        </dependency>
    </dependencies>
</project>
```

**Line-by-line explanation:**
- `<groupId>`, `<artifactId>`, `<version>` → identify OUR project (not a dependency) — students already know this pattern from earlier Maven projects in the course.
- `hibernate-core` → the actual Hibernate framework — gives us `Configuration`, `SessionFactory`, `Session`, annotations like `@Entity`, etc.
- `mysql-connector-j` → the JDBC driver for MySQL. **Important point to stress:** Hibernate still needs a JDBC driver underneath — Hibernate doesn't talk to MySQL directly, it generates SQL and hands it to this driver, exactly as mentioned in Day 7's architecture diagram.
- Version numbers matter — mismatched versions between Hibernate and the driver can cause errors. Use the versions above (or whatever the batch's standard setup uses) consistently across all students to avoid version-mismatch debugging during class.

**After adding this:** tell Maven to download everything — `Right-click project → Maven → Update Project` (Eclipse) or `mvn clean install` (command line). Confirm the JARs appear under "Maven Dependencies" before moving on — do not proceed until every student sees this.

---

## 4. File 2 — `hibernate.cfg.xml` (The Configuration File)

**Its job:** Tell Hibernate everything it needs to know to connect to the database and how to behave — this is the file the `Configuration` component (from Day 7's architecture diagram) reads.

**Location:** must be placed in `src/main/resources/hibernate.cfg.xml` — Hibernate looks for it here by default.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE hibernate-configuration PUBLIC
        "-//Hibernate/Hibernate Configuration DTD 3.0//EN"
        "http://www.hibernate.org/dtd/hibernate-configuration-3.0.dtd">

<hibernate-configuration>
    <session-factory>

        <!-- Database connection settings -->
        <property name="hibernate.connection.driver_class">com.mysql.cj.jdbc.Driver</property>
        <property name="hibernate.connection.url">jdbc:mysql://localhost:3306/studentdb</property>
        <property name="hibernate.connection.username">root</property>
        <property name="hibernate.connection.password">root123</property>

        <!-- Dialect: tells Hibernate which "flavor" of SQL to generate -->
        <property name="hibernate.dialect">org.hibernate.dialect.MySQLDialect</property>

        <!-- Show generated SQL in console (great for learning/debugging) -->
        <property name="hibernate.show_sql">true</property>
        <property name="hibernate.format_sql">true</property>

        <!-- Auto create/update table structure based on our entity classes -->
        <property name="hibernate.hbm2ddl.auto">update</property>

        <!-- Register our entity class -->
        <mapping class="com.apexswaram.hibernate.entity.Student"/>

    </session-factory>
</hibernate-configuration>
```

**Explain EVERY property — this file is 90% of "why doesn't Hibernate connect" issues, so go slow here:**

| Property | Meaning |
|---|---|
| `connection.driver_class` | The JDBC driver class name — same driver class used in Day 7's raw JDBC example, Hibernate just needs to be told which one to use. |
| `connection.url` | The database URL — `jdbc:mysql://<host>:<port>/<databaseName>`. Must match the database created in Section 1. |
| `connection.username` / `connection.password` | MySQL login credentials — same ones used to log into MySQL Workbench/command line. |
| `hibernate.dialect` | Tells Hibernate which SQL "dialect" to generate — MySQL, Oracle, and PostgreSQL all have slightly different SQL syntax; the dialect handles these differences so we don't have to. |
| `hibernate.show_sql` | When `true`, Hibernate prints every SQL statement it generates to the console — **extremely useful for today's class** so students can SEE Hibernate writing SQL for them, connecting directly back to Day 7's core promise ("Hibernate generates SQL for us"). |
| `hibernate.format_sql` | Just makes the printed SQL nicely indented/readable instead of one long line. |
| `hibernate.hbm2ddl.auto` | Controls whether Hibernate creates/updates the table automatically based on our entity class. `update` = create the table if it doesn't exist, and add new columns if the entity changes, but never delete existing data. (Other values: `create` = drops and recreates every time — data loss on every run, useful only for throwaway testing; `validate` = checks the entity matches an existing table but changes nothing; `none` = does nothing, table must already exist.) **Use `update` for this course** so students don't lose data between runs. |
| `<mapping class="...">` | Tells Hibernate "this Java class is an entity you should manage" — points to the `Student` class we build next. If we had multiple entities, we'd add one `<mapping>` line per class. |

**Common mistake to warn students about:** if `hibernate.cfg.xml` is placed in the wrong folder (not directly under `resources`), Hibernate won't find it and will throw a `SessionFactory` creation error — worth demonstrating this error once on purpose so students recognize it if it happens to them.

---

## 5. File 3 — `Student.java` (The Entity Class)

**Its job:** This is a plain Java class that represents ONE row of the `student` table — but with special annotations telling Hibernate exactly how to map it. This is the Java-object side of the ORM mapping from Day 7's table (`Class ↔ Table`, `Object ↔ Row`, `Field ↔ Column`).

```java
package com.apexswaram.hibernate.entity;

import jakarta.persistence.Entity;
import jakarta.persistence.Table;
import jakarta.persistence.Id;
import jakarta.persistence.GeneratedValue;
import jakarta.persistence.GenerationType;
import jakarta.persistence.Column;

@Entity
@Table(name = "student")
public class Student {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    @Column(name = "id")
    private int id;

    @Column(name = "name", nullable = false, length = 100)
    private String name;

    @Column(name = "username", nullable = false, unique = true, length = 50)
    private String username;

    @Column(name = "course")
    private String course;

    // Hibernate REQUIRES a no-argument constructor — explained below
    public Student() {
    }

    public Student(String name, String username, String course) {
        this.name = name;
        this.username = username;
        this.course = course;
    }

    // Getters and Setters — Hibernate uses these internally
    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getUsername() {
        return username;
    }

    public void setUsername(String username) {
        this.username = username;
    }

    public String getCourse() {
        return course;
    }

    public void setCourse(String course) {
        this.course = course;
    }

    @Override
    public String toString() {
        return "Student{id=" + id + ", name='" + name + "', username='" + username + "', course='" + course + "'}";
    }
}
```

**Explain EVERY annotation — go slowly, this is the heart of Hibernate:**

| Annotation | Meaning |
|---|---|
| `@Entity` | Marks this class as a Hibernate-managed entity — i.e., "this class maps to a database table." Without this, Hibernate ignores the class entirely. |
| `@Table(name = "student")` | Specifies which table this class maps to. If omitted, Hibernate uses the class name as the table name by default — we specify it explicitly here for clarity. |
| `@Id` | Marks this field as the **primary key** of the table — every entity MUST have exactly one `@Id` field. |
| `@GeneratedValue(strategy = GenerationType.IDENTITY)` | Tells Hibernate the primary key value should be auto-generated by the database itself (like MySQL's `AUTO_INCREMENT`) — we never manually set `id` when creating a new student; the database assigns it. |
| `@Column(name = "...", nullable = ..., unique = ..., length = ...)` | Maps a field to a specific column, and can enforce constraints: `nullable = false` (column can't be empty), `unique = true` (no duplicate values allowed — used here for `username`), `length` (max characters, maps to `VARCHAR(length)` in MySQL). If `@Column` is omitted entirely on a field, Hibernate still maps it — using the field name as the column name by default — but being explicit like this is better practice and avoids surprises. |

**Two rules students must memorize (explain WHY, don't just state them):**
1. **A no-argument constructor is mandatory.** Hibernate creates entity objects internally using reflection (behind the scenes, without calling our code directly) — it needs an empty constructor to do this, even though we also provide a convenience constructor with parameters for our own use.
2. **Getters and setters are required for every mapped field.** Hibernate uses these internally to read and write field values when saving/loading data — this is part of the JavaBean convention that Hibernate (and many Java frameworks) rely on.

**Connect back to Day 7:** this file alone represents the entire "Object Relational Mapping" idea from yesterday — `Student` class = `student` table, each field = a column, and every `Student` object we create in Java will become one row.

---

## 6. File 4 — `HibernateUtil.java` (The SessionFactory Utility Class)

**Its job:** Build the `SessionFactory` **exactly once** for the whole application and provide it to any class that needs it. Recall from Day 7: `SessionFactory` is heavyweight and expensive to create — creating a new one every time we need a `Session` would be extremely wasteful. This utility class solves that using a common design pattern.

```java
package com.apexswaram.hibernate.util;

import org.hibernate.SessionFactory;
import org.hibernate.cfg.Configuration;

public class HibernateUtil {

    private static final SessionFactory sessionFactory = buildSessionFactory();

    private static SessionFactory buildSessionFactory() {
        try {
            // Reads hibernate.cfg.xml automatically and builds the SessionFactory
            return new Configuration().configure().buildSessionFactory();
        } catch (Throwable ex) {
            System.err.println("SessionFactory creation failed: " + ex);
            throw new ExceptionInInitializerError(ex);
        }
    }

    public static SessionFactory getSessionFactory() {
        return sessionFactory;
    }
}
```

**Explain in detail:**
- `private static final SessionFactory sessionFactory = buildSessionFactory();` → This line runs **once**, when the class is first loaded by the JVM (`static` fields initialize once per application, not per object — a good moment to check if students remember `static` from core Java). This guarantees only ONE `SessionFactory` ever exists.
- `new Configuration().configure().buildSessionFactory();` → this is literally Day 7's architecture diagram written as code:
  - `new Configuration()` → creates the `Configuration` component
  - `.configure()` → tells it to read `hibernate.cfg.xml` (by default, looks in `src/main/resources`)
  - `.buildSessionFactory()` → uses everything read from the config to build and return the `SessionFactory`
- `getSessionFactory()` → a public method any other class in our project calls whenever it needs to start a `Session` — this is the ONLY entry point other classes should use; they should never build their own `SessionFactory`.
- The `try/catch` around `buildSessionFactory()` exists because if `hibernate.cfg.xml` has any mistake (wrong password, missing file, wrong dialect, etc.), this is exactly where the error will surface — printing it clearly helps students debug their own config file mistakes quickly.

**Why a separate utility class instead of writing this code directly in `main()`?** Any class anywhere in a larger project can call `HibernateUtil.getSessionFactory()` — this is the reusable, correct pattern used in real projects (and we'll reuse this exact class, unchanged, for the rest of the Hibernate module, Days 9–14).

---

## 7. File 5 — `StudentSaveDemo.java` (Putting It All Together)

**Its job:** Actually use everything above to save one `Student` object into the database. This is where we finally see Day 7's `Session` and `Transaction` components in action.

```java
package com.apexswaram.hibernate.main;

import com.apexswaram.hibernate.entity.Student;
import com.apexswaram.hibernate.util.HibernateUtil;
import org.hibernate.Session;
import org.hibernate.SessionFactory;
import org.hibernate.Transaction;

public class StudentSaveDemo {
    public static void main(String[] args) {

        // Step 1: Get the SessionFactory (built once, reused from HibernateUtil)
        SessionFactory factory = HibernateUtil.getSessionFactory();

        // Step 2: Open a Session (one unit of work)
        Session session = factory.openSession();

        // Step 3: Begin a Transaction
        Transaction transaction = session.beginTransaction();

        try {
            // Step 4: Create a plain Java object (no SQL written by us!)
            Student student = new Student("Ravi Kumar", "ravi123", "Java Full Stack");

            // Step 5: Save it — Hibernate generates and runs the INSERT SQL internally
            session.persist(student);

            // Step 6: Commit the transaction — actually writes the data to the database
            transaction.commit();

            System.out.println("Student saved successfully! Generated ID: " + student.getId());

        } catch (Exception e) {
            // If anything goes wrong, undo everything in this transaction
            transaction.rollback();
            e.printStackTrace();
        } finally {
            // Step 7: Always close the session when done
            session.close();
        }
    }
}
```

**Explain every step, connecting each one back to Day 7's architecture:**
1. `HibernateUtil.getSessionFactory()` → reuses the single `SessionFactory` built once (File 4) — we never create a new one here.
2. `factory.openSession()` → creates a `Session`, our "one unit of work" with the database, exactly as described in Day 7.
3. `session.beginTransaction()` → starts a `Transaction` — everything between this and `commit()`/`rollback()` either all succeeds or all fails together.
4. `new Student(...)` → notice this is a **completely plain Java object** — no SQL, no `ResultSet`, nothing database-specific. This is the entire point of ORM from Day 7.
5. `session.persist(student)` → tells Hibernate "save this object" — internally, Hibernate reads the `@Entity`/`@Column` annotations on `Student.java` and generates the correct `INSERT INTO student (...) VALUES (...)` SQL automatically. Because `hibernate.show_sql=true`, students will literally SEE this generated SQL printed in the console when we run this — point this out live, it's the most convincing proof of what Hibernate is doing for us.
6. `transaction.commit()` → actually sends the changes to the database permanently. **Important:** without calling `commit()`, nothing is actually saved — a very common beginner mistake to flag now.
7. `session.close()` in `finally` → always release the `Session`'s resources, whether the save succeeded or failed — using `finally` guarantees this runs either way.

**Run this now, live, in front of the class.** Then:
- Show the console output with the generated `INSERT` SQL (from `show_sql=true`).
- Open MySQL Workbench (or command line) and run `SELECT * FROM student;` to show the row is really there.
- Run the program a second time with a different name — show a second row appears with an auto-incremented `id`, proving `@GeneratedValue` works.

---

## 8. Common Errors & How to Recognize Them (Very Important for a Setup Day)

| Error Message (roughly) | Likely Cause |
|---|---|
| `Unable to create SessionFactory` / `ExceptionInInitializerError` | Something wrong in `hibernate.cfg.xml` — wrong password, wrong dialect, or the file isn't in `src/main/resources`. |
| `Communications link failure` | MySQL server isn't running, or wrong port/host in `connection.url`. |
| `Unknown database 'studentdb'` | Forgot to run `CREATE DATABASE studentdb;` from Section 1. |
| `Table 'studentdb.student' doesn't exist` | `hbm2ddl.auto` isn't set to `update`/`create`, or the entity class isn't registered in `<mapping class="...">`. |
| `No default constructor for entity` | Forgot the no-argument constructor in `Student.java` (Section 5, Rule 1). |

Deliberately trigger 1–2 of these on the shared teaching screen (e.g., temporarily stop MySQL, or comment out the no-arg constructor) so students recognize these errors instead of panicking when they hit them on their own machines.

---

## 9. In-Class Activity
Ask every student to individually:
1. Set up their own Maven project with `pom.xml` exactly as in Section 3.
2. Create `hibernate.cfg.xml` pointing to their own `studentdb`.
3. Create the `Student` entity class exactly as in Section 5.
4. Create `HibernateUtil.java` exactly as in Section 6.
5. Write their own `StudentSaveDemo.java` that saves **3 different students** (call `session.persist()` three times within the same transaction, before committing once).
6. Verify all 3 rows appear in MySQL Workbench.

## 10. Recap Questions (End of Class)
1. What is the job of `hibernate.cfg.xml`, and where must it be placed?
2. Why does `Student.java` need a no-argument constructor?
3. What does `hibernate.hbm2ddl.auto=update` actually do?
4. Why is `SessionFactory` built only once, while `Session` is created per operation?
5. What happens if we forget to call `transaction.commit()`?

## 11. Homework
- Re-run today's `StudentSaveDemo.java` after temporarily changing `hibernate.hbm2ddl.auto` to `create` — observe (carefully, on a throwaway/test database only) that existing data gets wiped. Change it back to `update` afterward. This is meant to make the difference between `update` and `create` unforgettable.
- Read ahead lightly on `session.get()` — Day 9 covers full CRUD (Create, Read, Update, Delete) using the exact same `Student` entity and `HibernateUtil` class built today, so today's setup work will be reused directly.

---
*Prepared for JFS Batch 2 — Day 8 of 15 (JSP & Hibernate Module)*
