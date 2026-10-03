# Day 10 — HQL & Criteria API

## A Note Before We Start
Day 9 gave us a one-line preview of HQL (`"FROM Student"`) just to read all rows. Today we go deep into **HQL** (Hibernate Query Language) for filtering, sorting, and aggregating data, and then look at the **Criteria API** — an alternative, fully Java (no query-string) way of building the same kinds of queries. Both approaches reuse `Student.java` and `HibernateUtil.java` from Day 8, completely unchanged.

## Objectives
By the end of this class, students should be able to:
- Write HQL queries with `WHERE`, `ORDER BY`, parameters, and aggregate functions
- Understand why HQL queries entity/field names, not table/column names
- Use named parameters safely (avoiding SQL-injection-style string concatenation)
- Build equivalent queries using the modern Criteria API
- Know when to reach for HQL vs Criteria API in real projects

## Quick Recap of Day 9
- CRUD summary: `persist()`, `get()`/`load()`, fetch-then-modify for update, `remove()`, `saveOrUpdate()`
- Automatic dirty checking — changes to an attached entity are saved on `commit()` without an explicit update call
- Ask 2 students to explain the difference between `get()` and `load()` before starting today.

---

## 1. Why HQL Instead of Plain SQL?

Quick reminder from Day 7/9: Hibernate maps `Student` (class) ↔ `student` (table). HQL lets us query using **class and field names** (`Student`, `name`, `course`) instead of **table and column names** (`student`, `name`, `course`) — this matters a lot once table/column names diverge from Java naming conventions (e.g., a column named `stu_name` mapped to a field called `name` via `@Column(name="stu_name")` — HQL would still use `name`, plain SQL would need `stu_name`).

**Biggest practical benefit:** HQL is **database-independent** — the same HQL query works whether the underlying database is MySQL, Oracle, or PostgreSQL, because Hibernate translates it into the correct dialect-specific SQL at runtime (same idea as the `hibernate.dialect` setting from Day 8).

---

## 2. HQL — Basic SELECT (Recap + Extend from Day 9)

```java
Session session = factory.openSession();
Query<Student> query = session.createQuery("FROM Student", Student.class);
List<Student> allStudents = query.list();
session.close();
```

**Explanation (recap from Day 9):** `FROM Student` queries the **entity name** `Student`, not the table name `student`. `createQuery(hql, ResultClass.class)` is the modern, type-safe way to run HQL — the second argument tells Hibernate what type to return, avoiding unchecked casts.

---

## 3. HQL — `WHERE` Clause with Named Parameters

**Full Example — `HqlWhereDemo.java`**

```java
package com.apexswaram.hibernate.main;

import com.apexswaram.hibernate.entity.Student;
import com.apexswaram.hibernate.util.HibernateUtil;
import org.hibernate.Session;
import org.hibernate.SessionFactory;
import org.hibernate.query.Query;
import java.util.List;

public class HqlWhereDemo {
    public static void main(String[] args) {
        SessionFactory factory = HibernateUtil.getSessionFactory();
        Session session = factory.openSession();

        String hql = "FROM Student WHERE course = :courseName";
        Query<Student> query = session.createQuery(hql, Student.class);
        query.setParameter("courseName", "Java Full Stack");

        List<Student> results = query.list();
        for (Student s : results) {
            System.out.println(s);
        }

        session.close();
    }
}
```

**Explanation — go slowly, this is the most important habit to build today:**
- `:courseName` is a **named parameter** — a placeholder in the HQL string.
- `query.setParameter("courseName", "Java Full Stack")` safely binds the actual value to that placeholder.
- **Critical point to stress:** NEVER build HQL by concatenating user input directly into the string, like `"FROM Student WHERE course = '" + userInput + "'"`. This reopens the exact SQL-injection risk Hibernate is supposed to protect us from. Always use named parameters (`:name`) or positional parameters (`?1`, `?2`) — never string concatenation. This is a direct callback to why `PreparedStatement` with `?` placeholders was used back in Day 7's raw JDBC example — the same safety principle applies here.

### 3.1 Multiple Conditions

```java
String hql = "FROM Student WHERE course = :courseName AND username LIKE :searchTerm";
Query<Student> query = session.createQuery(hql, Student.class);
query.setParameter("courseName", "Java Full Stack");
query.setParameter("searchTerm", "ra%");   // starts with "ra"

List<Student> results = query.list();
```

**Explanation:**
- Combine conditions with `AND`/`OR`, exactly like SQL.
- `LIKE` works the same as SQL — `%` is a wildcard. Here `"ra%"` matches any username starting with "ra" (e.g., "ravi123").

---

## 4. HQL — `ORDER BY`

```java
String hql = "FROM Student ORDER BY name ASC";
Query<Student> query = session.createQuery(hql, Student.class);
List<Student> results = query.list();
```

**Explanation:**
- Same syntax as SQL — `ASC` (default, can be omitted) or `DESC`.
- Can combine with `WHERE`: `"FROM Student WHERE course = :courseName ORDER BY name DESC"`.

---

## 5. HQL — Selecting Specific Fields (Projections)

So far we've fetched entire `Student` objects. Sometimes we only need one or two fields — HQL lets us select just those, which is more efficient (less data transferred).

```java
String hql = "SELECT s.name, s.course FROM Student s";
Query<Object[]> query = session.createQuery(hql, Object[].class);
List<Object[]> results = query.list();

for (Object[] row : results) {
    System.out.println("Name: " + row[0] + ", Course: " + row[1]);
}
```

**Explanation:**
- `s` here is an **alias** for `Student` — required once we start selecting individual fields, so Hibernate knows which entity `name`/`course` belong to.
- Since we're selecting 2 columns instead of a full entity, each result row comes back as an `Object[]` (an array of objects) rather than a `Student` — `row[0]` is `name`, `row[1]` is `course`, in the order we selected them.
- Mention this is a preview — a cleaner alternative (returning a proper small Java object instead of an `Object[]`) uses **constructor expressions**, which is a slightly more advanced HQL feature; keep today's focus on the `Object[]` version since it's simpler to grasp first.

---

## 6. HQL — Aggregate Functions

```java
String hql = "SELECT COUNT(s) FROM Student s WHERE s.course = :courseName";
Query<Long> query = session.createQuery(hql, Long.class);
query.setParameter("courseName", "Java Full Stack");

Long count = query.uniqueResult();
System.out.println("Total students in Java Full Stack: " + count);
```

**Explanation:**
- `COUNT()`, and similarly `SUM()`, `AVG()`, `MAX()`, `MIN()` all work in HQL exactly as in SQL.
- `query.uniqueResult()` is used (instead of `.list()`) when we expect exactly **one** row back — like a count or a single aggregate value. If the query unexpectedly returns more than one row, `uniqueResult()` throws an exception — a useful safety check.

---

## 7. HQL — UPDATE and DELETE (Bulk Operations)

So far, Day 9's update/delete worked by fetching ONE entity, modifying it, then committing (relying on automatic dirty checking). HQL also supports **bulk** update/delete — directly updating/deleting many rows in one query, without fetching them into Java objects first.

**Full Example — `HqlBulkUpdateDemo.java`**

```java
package com.apexswaram.hibernate.main;

import com.apexswaram.hibernate.util.HibernateUtil;
import org.hibernate.Session;
import org.hibernate.SessionFactory;
import org.hibernate.Transaction;
import org.hibernate.query.Query;

public class HqlBulkUpdateDemo {
    public static void main(String[] args) {
        SessionFactory factory = HibernateUtil.getSessionFactory();
        Session session = factory.openSession();
        Transaction transaction = session.beginTransaction();

        try {
            String hql = "UPDATE Student SET course = :newCourse WHERE course = :oldCourse";
            Query query = session.createQuery(hql);
            query.setParameter("newCourse", "Full Stack + AI/ML");
            query.setParameter("oldCourse", "Java Full Stack");

            int updatedCount = query.executeUpdate();

            transaction.commit();
            System.out.println(updatedCount + " student(s) updated.");

        } catch (Exception e) {
            transaction.rollback();
            e.printStackTrace();
        } finally {
            session.close();
        }
    }
}
```

**Explanation:**
- `query.executeUpdate()` runs the HQL directly as a bulk `UPDATE` statement against the database — it does NOT load entities into Java first, so it's much faster for updating many rows at once. It returns the number of rows affected.
- **Important caution to give students:** because bulk HQL updates/deletes bypass loading entities into the session, Hibernate's automatic dirty-checking and first-level cache (Day 13 topic) can become out of sync with what's actually in the database if you continue using the same session afterward for related work. For today, treat bulk HQL update/delete as a separate, standalone operation — don't mix it with fetch-then-modify style code in the same session without being aware of this.
- Bulk `DELETE` follows the identical pattern:
```java
String hql = "DELETE FROM Student WHERE course = :courseName";
Query query = session.createQuery(hql);
query.setParameter("courseName", "Data Analytics");
int deletedCount = query.executeUpdate();
```

---

## 8. The Criteria API — A Fully Java Alternative to HQL

**Concept:** Instead of writing HQL as a query *string*, the Criteria API lets us build queries using **pure Java method calls** — this means compile-time checking (typos become compiler errors instead of runtime surprises) and is useful for building queries dynamically (e.g., a search form with optional filters).

**Full Example — `CriteriaDemo.java`** (equivalent to Section 3's WHERE example)

```java
package com.apexswaram.hibernate.main;

import com.apexswaram.hibernate.entity.Student;
import com.apexswaram.hibernate.util.HibernateUtil;
import org.hibernate.Session;
import org.hibernate.SessionFactory;
import jakarta.persistence.criteria.CriteriaBuilder;
import jakarta.persistence.criteria.CriteriaQuery;
import jakarta.persistence.criteria.Root;
import java.util.List;

public class CriteriaDemo {
    public static void main(String[] args) {
        SessionFactory factory = HibernateUtil.getSessionFactory();
        Session session = factory.openSession();

        // Step 1: Get a CriteriaBuilder — the entry point for building criteria queries
        CriteriaBuilder cb = session.getCriteriaBuilder();

        // Step 2: Create a CriteriaQuery for the Student entity
        CriteriaQuery<Student> cq = cb.createQuery(Student.class);

        // Step 3: Define the "root" — represents the table/entity we're querying FROM
        Root<Student> root = cq.from(Student.class);

        // Step 4: Add a WHERE condition — equivalent to "WHERE course = 'Java Full Stack'"
        cq.select(root).where(cb.equal(root.get("course"), "Java Full Stack"));

        // Step 5: Execute
        List<Student> results = session.createQuery(cq).getResultList();

        for (Student s : results) {
            System.out.println(s);
        }

        session.close();
    }
}
```

**Explanation — map each step back to the HQL equivalent so students see they're doing the same thing two different ways:**
- `CriteriaBuilder cb` → the factory for building query conditions (`equal`, `like`, `and`, `or`, `greaterThan`, etc.) — think of it as the toolbox.
- `CriteriaQuery<Student> cq` → represents the overall query we're constructing, equivalent to writing `"... FROM Student ..."` in HQL.
- `Root<Student> root` → represents the `Student` entity in the query — equivalent to the alias `s` we used in Section 5's HQL projection example.
- `root.get("course")` → refers to the `course` field — note this is a `String` field name, so a typo here (`"corse"`) would only fail at runtime, not compile time; this is a limitation of the "basic" Criteria API style shown here (a more advanced "metamodel" approach avoids even this, but that's beyond today's scope).
- `cb.equal(root.get("course"), "Java Full Stack")` → builds the actual `WHERE course = 'Java Full Stack'` condition.
- `cq.select(root).where(...)` → chains the SELECT and WHERE together — equivalent to `"FROM Student WHERE course = :courseName"` in HQL.
- `session.createQuery(cq).getResultList()` → executes the built criteria query and returns the results, just like `.list()` did for HQL.

### 8.1 Criteria API — Multiple Conditions (AND)

```java
CriteriaBuilder cb = session.getCriteriaBuilder();
CriteriaQuery<Student> cq = cb.createQuery(Student.class);
Root<Student> root = cq.from(Student.class);

cq.select(root).where(
    cb.and(
        cb.equal(root.get("course"), "Java Full Stack"),
        cb.like(root.get("username"), "ra%")
    )
);

List<Student> results = session.createQuery(cq).getResultList();
```

**Explanation:**
- `cb.and(condition1, condition2)` combines conditions — equivalent to HQL's `AND` from Section 3.1.
- `cb.like(...)` works just like HQL's `LIKE`.

### 8.2 Criteria API — ORDER BY

```java
cq.select(root)
  .where(cb.equal(root.get("course"), "Java Full Stack"))
  .orderBy(cb.asc(root.get("name")));
```

**Explanation:** `cb.asc(...)`/`cb.desc(...)` are the Criteria equivalents of HQL's `ORDER BY ... ASC/DESC`.

---

## 9. HQL vs Criteria API — When to Use Which

| Aspect | HQL | Criteria API |
|---|---|---|
| Readability | Very readable, close to SQL | More verbose, but fully Java |
| Typo safety | Errors only caught at runtime | Some errors caught earlier, though field names are still strings in the basic form shown today |
| Best for | Fixed, known queries (most common case) | Dynamically building queries (e.g., a search form where filters are optional/conditional) |
| Learning priority for this course | **Primary tool — use this by default** | Good to know exists; use HQL unless a specific dynamic-query need arises |

**Practical guidance to give students:** in real projects (and in interviews), HQL is used far more often for everyday queries because it's simpler to read and write. The Criteria API shines specifically when a query's structure needs to change at runtime based on user input (e.g., "search students by name AND/OR course AND/OR only if a filter was provided") — building that with string concatenation in HQL gets messy fast, while Criteria API handles it cleanly with plain `if` statements adding `.where()` conditions conditionally.

---

## 10. In-Class Activity
Ask students to write BOTH an HQL version and a Criteria API version of the same query:
1. Find all students whose `course` is `"Java Full Stack"`, ordered by `name` ascending.
2. Count how many students are enrolled in each unique course (hint: `GROUP BY` in HQL — briefly introduce this as similar to SQL's `GROUP BY`, e.g. `"SELECT course, COUNT(s) FROM Student s GROUP BY course"`).
3. Using HQL bulk update, change the course of all students currently in `"Data Analytics"` to `"Data Analytics + AI"`.

## 11. Recap Questions (End of Class)
1. Why does HQL use `FROM Student` instead of `FROM student`?
2. Why should we always use named parameters (`:name`) instead of string concatenation in HQL?
3. What does `query.executeUpdate()` do differently compared to fetch-then-modify update from Day 9?
4. What are the four main building blocks of a Criteria API query (name the 4 objects we created in `CriteriaDemo.java`)?
5. When would you prefer the Criteria API over HQL?

## 12. Homework
- Rewrite one of Day 9's CRUD activity queries (the "read all students" step) using `ORDER BY name` in HQL.
- Read ahead lightly on entity relationships (`@OneToOne`, `@OneToMany`, `@ManyToOne`, `@ManyToMany`) — Day 12 covers these in full, and we'll query across related entities using HQL joins, building directly on today's HQL foundation.

---
*Prepared for JFS Batch 2 — Day 10 of 15 (JSP & Hibernate Module)*
