
# 1. Project Structures

## 1. One-to-One Project

Project Name: Hibernate-OneToOne-Demo

```
Hibernate-OneToOne-Demo
|
|-- pom.xml
|
|-- src
    |-- main
        |-- java
        |   |-- com/apexswaram/onetoone
        |       |-- entity
        |       |   |-- Student.java
        |       |   |-- StudentProfile.java
        |       |
        |       |-- util
        |       |   |-- HibernateUtil.java
        |       |
        |       |-- main
        |           |-- OneToOneDemo.java
        |
        |-- resources
            |-- hibernate.cfg.xml
```

---

## 2. One-to-Many Project

Project Name: Hibernate-OneToMany-Demo

```
Hibernate-OneToMany-Demo
|
|-- pom.xml
|
|-- src
    |-- main
        |-- java
        |   |-- com/apexswaram/onetomany
        |       |-- entity
        |       |   |-- Student.java
        |       |   |-- Course.java
        |       |
        |       |-- util
        |       |   |-- HibernateUtil.java
        |       |
        |       |-- main
        |           |-- OneToManyDemo.java
        |
        |-- resources
            |-- hibernate.cfg.xml
```

---

## 3. Many-to-One Project (Separate for Teaching)

Project Name: Hibernate-ManyToOne-Demo

```
Hibernate-ManyToOne-Demo
|
|-- pom.xml
|
|-- src
    |-- main
        |-- java
        |   |-- com/apexswaram/manytoone
        |       |-- entity
        |       |   |-- Student.java
        |       |   |-- Course.java
        |       |
        |       |-- util
        |       |   |-- HibernateUtil.java
        |       |
        |       |-- main
        |           |-- ManyToOneDemo.java
        |
        |-- resources
            |-- hibernate.cfg.xml
```

---

## 4. Many-to-Many Project

Project Name: Hibernate-ManyToMany-Demo

```
Hibernate-ManyToMany-Demo
|
|-- pom.xml
|
|-- src
    |-- main
        |-- java
        |   |-- com/apexswaram/manytomany
        |       |-- entity
        |       |   |-- Student.java
        |       |   |-- Course.java
        |       |
        |       |-- util
        |       |   |-- HibernateUtil.java
        |       |
        |       |-- main
        |           |-- ManyToManyDemo.java
        |
        |-- resources
            |-- hibernate.cfg.xml
```

---
# Day 11 — Hibernate Relationships (One-to-One, One-to-Many, Many-to-One, Many-to-Many)

## A Note Before We Start
Every relationship type today needs **at least 2 entity classes** working together, plus updated `hibernate.cfg.xml` mappings, plus a main class to test it — more files than any single day so far. Go through each relationship type completely (both entity classes, the mapping annotations, the config update, AND a working demo) before moving to the next type. Don't rush — relationships are the single most confusing Hibernate topic for most students, so full worked examples matter more today than any other day.

## Objectives
By the end of this class, students should be able to:
- Explain the 4 relationship types and identify which one fits a given real-world scenario
- Correctly annotate both sides of each relationship
- Understand owning side vs inverse side, and what `mappedBy` does
- Understand `FetchType.LAZY` vs `FetchType.EAGER`
- Save and query related entities together

## Quick Recap of Day 10
- HQL: `WHERE` with named parameters, `ORDER BY`, aggregates, bulk `executeUpdate()`
- Criteria API: `CriteriaBuilder` → `CriteriaQuery` → `Root` → `.where()`
- Ask 2 students to write one HQL query with a `WHERE` clause on the board before starting today.

---

## 1. Why Relationships Matter (The Real-World Problem)

So far, `Student` has been one flat table with no connections to anything else. Real applications almost always have **related data** — e.g., a student enrolls in multiple courses, or a student has one profile/address, or courses have many students and students take many courses. Hibernate lets us model these connections **as Java object references** (one object holding another, or a `List` of others) instead of manually writing JOIN queries and stitching results together ourselves — this is ORM's relationship-mapping power, building on everything from Days 7–10.

### 1.1 The 4 Relationship Types — Quick Overview (Write on Board First)

| Relationship | Real Example | Java Representation |
|---|---|---|
| One-to-One | A Student has exactly one StudentProfile (address, phone) | `Student` holds one `StudentProfile` field |
| One-to-Many / Many-to-One | A Course has many Students; each Student belongs to one Course | `Course` holds a `List<Student>`; `Student` holds one `Course` |
| Many-to-Many | A Student can enroll in many Courses; a Course can have many Students | Both `Student` and `Course` hold a `List` of each other |

We'll build all three patterns today, each with full working code.

---

## 2. One-to-One — `Student` and `StudentProfile`

**Scenario:** Each student has exactly one profile record (address, phone number) — kept in a separate table for organization, but tied 1:1 to a student.

### 2.1 `StudentProfile.java` (New Entity)

```java
package com.apexswaram.hibernate.entity;

import jakarta.persistence.*;

@Entity
@Table(name = "student_profile")
public class StudentProfile {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private int id;

    @Column(name = "address")
    private String address;

    @Column(name = "phone")
    private String phone;

    // Owning side of the relationship — this table will hold the foreign key
    @OneToOne
    @JoinColumn(name = "student_id")   // creates a "student_id" foreign key column in student_profile table
    private Student student;

    public StudentProfile() {
    }

    public StudentProfile(String address, String phone, Student student) {
        this.address = address;
        this.phone = phone;
        this.student = student;
    }

    // Getters and setters
    public int getId() { return id; }
    public void setId(int id) { this.id = id; }
    public String getAddress() { return address; }
    public void setAddress(String address) { this.address = address; }
    public String getPhone() { return phone; }
    public void setPhone(String phone) { this.phone = phone; }
    public Student getStudent() { return student; }
    public void setStudent(Student student) { this.student = student; }
}
```

**Explanation:**
- `@OneToOne` marks this field as a one-to-one relationship.
- `@JoinColumn(name = "student_id")` → this is the **owning side** — it tells Hibernate to add a `student_id` column in the `student_profile` table, which stores the ID of the related `Student` row. Whichever side has `@JoinColumn` is the "owning side" — it controls the foreign key.

### 2.2 Update `Student.java` (Add the Inverse Side)

Add this field to the existing `Student.java` from Day 8 (don't recreate the whole file — just add this field, its getter/setter, and the import):

```java
import jakarta.persistence.OneToOne;
import jakarta.persistence.CascadeType;

// ... inside the Student class, alongside existing fields:

@OneToOne(mappedBy = "student", cascade = CascadeType.ALL)
private StudentProfile profile;

// Getter and setter:
public StudentProfile getProfile() { return profile; }
public void setProfile(StudentProfile profile) { this.profile = profile; }
```

**Explanation — this is the most important concept in this whole section, go slowly:**
- `mappedBy = "student"` → tells Hibernate "don't create another foreign key column here — this side is just the **inverse/mirror view** of the relationship already defined by the `student` field over in `StudentProfile.java`." The value `"student"` must exactly match the field name in `StudentProfile.java` that holds `@JoinColumn`.
- **Owning side vs inverse side, explained simply:** think of it like a real-world friendship — only ONE side needs to "own" the paperwork (the foreign key column). `StudentProfile` owns it (has `@JoinColumn`); `Student` just has a convenient Java reference back (`mappedBy`) without any extra database column. If we forgot `mappedBy` and put `@JoinColumn` on BOTH sides, Hibernate would try to create two separate foreign key columns in two separate tables — wrong and confusing. Only one side ever gets `@JoinColumn`.
- `cascade = CascadeType.ALL` → when we save/update/delete a `Student`, automatically apply the same operation to its related `StudentProfile` too. Without this, we'd have to manually save the `StudentProfile` separately every time — explained more in Section 6.

### 2.3 Register the New Entity in `hibernate.cfg.xml`

Add this line inside `<session-factory>`, alongside the existing `Student` mapping from Day 8:

```xml
<mapping class="com.apexswaram.hibernate.entity.StudentProfile"/>
```

### 2.4 Full Working Demo — `OneToOneDemo.java`

```java
package com.apexswaram.hibernate.main;

import com.apexswaram.hibernate.entity.Student;
import com.apexswaram.hibernate.entity.StudentProfile;
import com.apexswaram.hibernate.util.HibernateUtil;
import org.hibernate.Session;
import org.hibernate.SessionFactory;
import org.hibernate.Transaction;

public class OneToOneDemo {
    public static void main(String[] args) {
        SessionFactory factory = HibernateUtil.getSessionFactory();
        Session session = factory.openSession();
        Transaction transaction = session.beginTransaction();

        try {
            Student student = new Student("Kavya Reddy", "kavya321", "Java Full Stack");
            StudentProfile profile = new StudentProfile("Vijayawada, AP", "9876543210", student);

            student.setProfile(profile);   // link both sides in Java, for consistency

            session.persist(student);      // because of CascadeType.ALL, this ALSO saves the profile

            transaction.commit();
            System.out.println("Student and profile saved together!");

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
- We set the relationship from BOTH sides in Java (`profile`'s constructor takes `student`, AND we call `student.setProfile(profile)`) — this is good practice, even though only ONE side (`StudentProfile`'s `@JoinColumn`) actually determines what's saved to the database. Keeping both sides in sync in Java avoids confusing bugs later if other code reads `student.getProfile()`.
- `session.persist(student)` — we only save the `Student`! Because of `cascade = CascadeType.ALL` on the `Student` side, Hibernate automatically also saves the linked `StudentProfile` — this is exactly the convenience `cascade` provides, and worth demonstrating by checking both tables in MySQL Workbench afterward and seeing both rows appear from ONE `persist()` call.

---

## 3. One-to-Many / Many-to-One — `Course` and `Student`

**Scenario:** A `Course` has many `Student`s; each `Student` belongs to exactly one `Course`. Note: this REPLACES the simple `String course` field students have been using since Day 8 — today we upgrade it into a real relationship. Mention this explicitly so students understand why `Student.java` is changing.

### 3.1 `Course.java` (New Entity)

```java
package com.apexswaram.hibernate.entity;

import jakarta.persistence.*;
import java.util.List;
import java.util.ArrayList;

@Entity
@Table(name = "course")
public class Course {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private int id;

    @Column(name = "course_name")
    private String courseName;

    // Inverse side — Course does NOT hold the foreign key; Student does (see below)
    @OneToMany(mappedBy = "course", cascade = CascadeType.ALL)
    private List<Student> students = new ArrayList<>();

    public Course() {
    }

    public Course(String courseName) {
        this.courseName = courseName;
    }

    // Getters and setters
    public int getId() { return id; }
    public void setId(int id) { this.id = id; }
    public String getCourseName() { return courseName; }
    public void setCourseName(String courseName) { this.courseName = courseName; }
    public List<Student> getStudents() { return students; }
    public void setStudents(List<Student> students) { this.students = students; }
}
```

**Explanation:**
- `@OneToMany(mappedBy = "course", ...)` → `Course` is the **inverse side** here — it holds a `List<Student>` for convenient reading in Java, but the actual foreign key column lives in the `student` table (added in the next step), not here. `mappedBy = "course"` points to the field name in `Student.java` that owns the relationship.
- Always initialize the `List` (`= new ArrayList<>()`) instead of leaving it `null` — prevents `NullPointerException` when we try to add students to a brand-new `Course` before it's ever been saved/loaded.

### 3.2 Update `Student.java` — Replace `course` String Field

**Remove** the old `private String course;` field, its getter, and setter from `Student.java` (from Day 8). **Add** this instead:

```java
import jakarta.persistence.ManyToOne;
import jakarta.persistence.JoinColumn;

// ... inside the Student class:

@ManyToOne
@JoinColumn(name = "course_id")   // this creates the foreign key column in the student table
private Course course;

// Getter and setter:
public Course getCourse() { return course; }
public void setCourse(Course course) { this.course = course; }
```

**Explanation:**
- `@ManyToOne` → many `Student`s relate to one `Course`. This is the **owning side** (it has `@JoinColumn`) — Hibernate adds a `course_id` column to the `student` table, storing which course each student belongs to.
- **Important teaching point:** `@ManyToOne` is ALWAYS the owning side in a one-to-many/many-to-one pair, because it makes logical sense for the "many" side to hold a single foreign key pointing to the "one" side — trying to do it the other way around (storing a list of foreign keys in one column) isn't how relational databases work. This pairing (`@OneToMany(mappedBy=...)` on one side, `@ManyToOne @JoinColumn` on the other) is the standard, memorize this pattern.

### 3.3 Register `Course` in `hibernate.cfg.xml`

```xml
<mapping class="com.apexswaram.hibernate.entity.Course"/>
```

### 3.4 Full Working Demo — `OneToManyDemo.java`

```java
package com.apexswaram.hibernate.main;

import com.apexswaram.hibernate.entity.Course;
import com.apexswaram.hibernate.entity.Student;
import com.apexswaram.hibernate.util.HibernateUtil;
import org.hibernate.Session;
import org.hibernate.SessionFactory;
import org.hibernate.Transaction;

public class OneToManyDemo {
    public static void main(String[] args) {
        SessionFactory factory = HibernateUtil.getSessionFactory();
        Session session = factory.openSession();
        Transaction transaction = session.beginTransaction();

        try {
            Course course = new Course("Java Full Stack");

            Student s1 = new Student();
            s1.setName("Ravi Kumar");
            s1.setUsername("ravi123");
            s1.setCourse(course);

            Student s2 = new Student();
            s2.setName("Priya Sharma");
            s2.setUsername("priya456");
            s2.setCourse(course);

            course.getStudents().add(s1);
            course.getStudents().add(s2);

            session.persist(course);   // cascade saves both students too

            transaction.commit();
            System.out.println("Course and students saved together!");

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
- We link BOTH sides again (each `Student.setCourse(course)`, AND `course.getStudents().add(...)`) — same "keep both sides in sync in Java" principle as Section 2.4.
- `session.persist(course)` alone saves everything — `cascade = CascadeType.ALL` on `Course`'s `students` field means saving the course automatically saves its student list too.

### 3.5 Reading the Relationship Back — HQL Join (Preview, Builds on Day 10)

```java
Session session = factory.openSession();
String hql = "FROM Course c JOIN FETCH c.students WHERE c.courseName = :name";
Query<Course> query = session.createQuery(hql, Course.class);
query.setParameter("name", "Java Full Stack");

Course course = query.uniqueResult();
System.out.println("Course: " + course.getCourseName());
for (Student s : course.getStudents()) {
    System.out.println(" - " + s.getName());
}
session.close();
```

**Explanation:**
- `JOIN FETCH` tells Hibernate to load the `Course` AND its related `students` in a single SQL query (a real SQL `JOIN` underneath) — without `JOIN FETCH`, accessing `course.getStudents()` later could trigger a SEPARATE query at that point (related to lazy loading, covered next) or fail if the session is already closed.

---

## 4. Many-to-Many — `Student` and `Course` (Alternative Modeling, Brief)

**Note for context:** Sections 2–3 modeled `Student`↔`Course` as one-to-many (each student belongs to exactly one course) — this fits our batch structure. But in some systems, a student can enroll in MULTIPLE courses simultaneously, and a course can have many students — that's many-to-many. We cover the pattern briefly here for completeness and interview purposes, without rewiring today's main `Student`/`Course` demo.

**Full Example — conceptual `Student`/`Course` many-to-many (separate from today's main exercise)**

```java
// Inside a Student entity (hypothetical many-to-many version):
@ManyToMany
@JoinTable(
    name = "student_course",                              // the join/link table Hibernate creates
    joinColumns = @JoinColumn(name = "student_id"),        // FK pointing to student
    inverseJoinColumns = @JoinColumn(name = "course_id")   // FK pointing to course
)
private List<Course> courses = new ArrayList<>();
```

```java
// Inside the corresponding Course entity:
@ManyToMany(mappedBy = "courses")
private List<Student> students = new ArrayList<>();
```

**Explanation:**
- Many-to-many relationships need a **third "join table"** (`student_course` here) in the database, holding just two foreign key columns — one row per student-course pairing. Hibernate creates and manages this join table automatically via `@JoinTable`.
- `@JoinTable` goes on the **owning side** (here, `Student`) — specifying the join table's name and its two foreign key columns.
- The other side (`Course`) just uses `mappedBy`, exactly the same inverse-side pattern from Sections 2 and 3.
- **When to use this instead of one-to-many:** if your batch's business rule changes to "a student can be enrolled in multiple courses at once," this many-to-many pattern would replace today's one-to-many `Student`↔`Course` setup.

---

## 5. `FetchType.LAZY` vs `FetchType.EAGER`

**Concept:** Controls WHEN Hibernate loads related data — immediately alongside the main entity, or only when actually accessed.

```java
@OneToMany(mappedBy = "course", fetch = FetchType.LAZY)   // default for @OneToMany/@ManyToMany
private List<Student> students;

@ManyToOne(fetch = FetchType.EAGER)   // default for @ManyToOne/@OneToOne
@JoinColumn(name = "course_id")
private Course course;
```

| Fetch Type | Behavior | Default For |
|---|---|---|
| `LAZY` | Related data is loaded only when you actually call the getter (e.g., `course.getStudents()`) | `@OneToMany`, `@ManyToMany` |
| `EAGER` | Related data is loaded immediately, in the same query as the main entity | `@ManyToOne`, `@OneToOne` |

**Explanation:**
- These are the DEFAULTS if you don't specify `fetch` explicitly — worth memorizing, since it explains some default Hibernate behavior students will observe without having written `fetch=...` anywhere.
- **Common real bug to warn about:** if you fetch a `Course` with `LAZY` students, then `session.close()`, and only AFTERWARD try to call `course.getStudents()` — this throws a `LazyInitializationException`, because the session (needed to fetch the extra data on demand) is already closed. This is one of the most common real-world Hibernate errors — the fix is either to access lazy data BEFORE closing the session, or use `JOIN FETCH` (Section 3.5) to load everything needed upfront in one go.
- **Practical guidance:** default fetch types are usually fine to start with; reach for `JOIN FETCH` in your HQL query when you know you'll need the related data, rather than changing the entity's fetch type globally.

---

## 6. Cascade Types — Brief Reference

We used `cascade = CascadeType.ALL` in Sections 2 and 3. Full list, for reference:

| Cascade Type | Effect |
|---|---|
| `PERSIST` | Saving the parent also saves new related children |
| `MERGE` | Updating the parent also updates related children |
| `REMOVE` | Deleting the parent also deletes related children |
| `ALL` | All of the above, combined — what we used today |

**Explanation:** `CascadeType.ALL` is convenient for tightly-coupled relationships like `Student`↔`StudentProfile` (a profile makes no sense without its student) — but should be used carefully for relationships like `Course`↔`Student`, since deleting a `Course` with `CascadeType.ALL` would also delete every enrolled `Student`, which is probably NOT the intended real-world behavior. Flag this as a design decision students must think through per relationship, not something to apply everywhere by default.

---

---

# Project: Hibernate-ManyToMany-Demo

```
Hibernate-ManyToMany-Demo
|
|-- pom.xml
|
|-- src
    |-- main
        |-- java
        |   |-- com/apexswaram/manytomany
        |       |-- entity
        |       |   |-- Student.java
        |       |   |-- Course.java
        |       |
        |       |-- util
        |       |   |-- HibernateUtil.java
        |       |
        |       |-- main
        |           |-- ManyToManyDemo.java
        |
        |-- resources
            |-- hibernate.cfg.xml
```

---

# Student.java

```java
package com.apexswaram.manytomany.entity;

import jakarta.persistence.*;
import java.util.ArrayList;
import java.util.List;

@Entity
@Table(name = "student")
public class Student {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private int id;

    private String name;
    private String username;

    @ManyToMany
    @JoinTable(
        name = "student_course",
        joinColumns = @JoinColumn(name = "student_id"),
        inverseJoinColumns = @JoinColumn(name = "course_id")
    )
    private List<Course> courses = new ArrayList<>();

    public Student() {}

    public Student(String name, String username) {
        this.name = name;
        this.username = username;
    }

    public int getId() { return id; }

    public String getName() { return name; }
    public void setName(String name) { this.name = name; }

    public String getUsername() { return username; }
    public void setUsername(String username) { this.username = username; }

    public List<Course> getCourses() { return courses; }
    public void setCourses(List<Course> courses) { this.courses = courses; }
}
```

---

# Course.java

```java
package com.apexswaram.manytomany.entity;

import jakarta.persistence.*;
import java.util.ArrayList;
import java.util.List;

@Entity
@Table(name = "course")
public class Course {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private int id;

    private String courseName;

    @ManyToMany(mappedBy = "courses")
    private List<Student> students = new ArrayList<>();

    public Course() {}

    public Course(String courseName) {
        this.courseName = courseName;
    }

    public int getId() { return id; }

    public String getCourseName() { return courseName; }
    public void setCourseName(String courseName) { this.courseName = courseName; }

    public List<Student> getStudents() { return students; }
    public void setStudents(List<Student> students) { this.students = students; }
}
```

---

# HibernateUtil.java

```java
package com.apexswaram.manytomany.util;

import org.hibernate.SessionFactory;
import org.hibernate.cfg.Configuration;

public class HibernateUtil {

    private static SessionFactory sessionFactory;

    static {
        try {
            sessionFactory = new Configuration().configure().buildSessionFactory();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }

    public static SessionFactory getSessionFactory() {
        return sessionFactory;
    }
}
```

---

# hibernate.cfg.xml

```xml
<hibernate-configuration>
    <session-factory>

        <property name="hibernate.connection.driver_class">com.mysql.cj.jdbc.Driver</property>
        <property name="hibernate.connection.url">jdbc:mysql://localhost:3306/test</property>
        <property name="hibernate.connection.username">root</property>
        <property name="hibernate.connection.password">root</property>

        <property name="hibernate.dialect">org.hibernate.dialect.MySQLDialect</property>

        <property name="hibernate.hbm2ddl.auto">update</property>
        <property name="hibernate.show_sql">true</property>
        <property name="hibernate.format_sql">true</property>

        <mapping class="com.apexswaram.manytomany.entity.Student"/>
        <mapping class="com.apexswaram.manytomany.entity.Course"/>

    </session-factory>
</hibernate-configuration>
```

---

# ManyToManyDemo.java

```java
package com.apexswaram.manytomany.main;

import com.apexswaram.manytomany.entity.Student;
import com.apexswaram.manytomany.entity.Course;
import com.apexswaram.manytomany.util.HibernateUtil;
import org.hibernate.Session;
import org.hibernate.SessionFactory;
import org.hibernate.Transaction;

public class ManyToManyDemo {

    public static void main(String[] args) {

        SessionFactory factory = HibernateUtil.getSessionFactory();
        Session session = factory.openSession();
        Transaction tx = session.beginTransaction();

        try {
            Student s1 = new Student("Ravi", "ravi123");
            Student s2 = new Student("Priya", "priya456");

            Course c1 = new Course("Java");
            Course c2 = new Course("Python");

            s1.getCourses().add(c1);
            s1.getCourses().add(c2);

            s2.getCourses().add(c1);

            c1.getStudents().add(s1);
            c1.getStudents().add(s2);

            c2.getStudents().add(s1);

            session.persist(s1);
            session.persist(s2);

            tx.commit();

            System.out.println("Many-to-Many data saved!");

        } catch (Exception e) {
            tx.rollback();
            e.printStackTrace();
        } finally {
            session.close();
        }
    }
}
```

---

