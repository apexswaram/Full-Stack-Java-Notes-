# Day 9 — CRUD Operations with Hibernate (Save, Get, Update, Delete)

## A Note Before We Start
Today we reuse **two files from Day 8 completely unchanged**: `Student.java` (the entity) and `HibernateUtil.java` (the `SessionFactory` utility). This is intentional and worth pointing out to students — this is exactly why we built `HibernateUtil` as a separate reusable class instead of writing that setup code inline every time. Today we only write NEW main classes that use them to perform each CRUD operation, one at a time, each explained in full.

## Objectives
By the end of this class, students should be able to:
- Perform all 4 CRUD operations (Create, Read, Update, Delete) using Hibernate
- Understand the difference between `save()`, `persist()`, and `saveOrUpdate()`
- Understand the difference between `get()` and `load()`
- Correctly manage transactions for every operation
- Explain what happens internally (which SQL Hibernate generates) for each operation

## Quick Recap of Day 8
- 5 files: `pom.xml`, `hibernate.cfg.xml`, `Student.java` (entity), `HibernateUtil.java`, main class
- `SessionFactory` = built once. `Session` = one unit of work. `Transaction` = wraps operations so they succeed/fail together.
- We successfully saved a `Student` row using `session.persist()` + `transaction.commit()`.
- Ask 2 students to recall the 5 files and what each does, before moving on.

---

## 1. Files We're Reusing As-Is From Day 8

**`Student.java`** (entity) — unchanged, same annotations (`@Entity`, `@Table`, `@Id`, `@GeneratedValue`, `@Column`) as Day 8 Section 5.

**`HibernateUtil.java`** (SessionFactory utility) — unchanged, same singleton pattern as Day 8 Section 6.

If any student doesn't have these working from Day 8, pause and get them working FIRST — today's entire class depends on both of these already running correctly.

---

## 2. The Standard Pattern for Every Hibernate Operation

Before diving into each operation, show students that **every single CRUD operation follows the exact same 5-step skeleton** — once they see this pattern, all of today's code becomes predictable instead of new syntax to memorize each time:

```java
SessionFactory factory = HibernateUtil.getSessionFactory();  // Step 1: get factory
Session session = factory.openSession();                     // Step 2: open session
Transaction transaction = session.beginTransaction();         // Step 3: begin transaction
try {
    // Step 4: DO THE ACTUAL OPERATION HERE (save/get/update/delete)
    transaction.commit();
} catch (Exception e) {
    transaction.rollback();
    e.printStackTrace();
} finally {
    session.close();                                          // Step 5: always close
}
```

Point this out explicitly: **only Step 4 changes** across all the examples below. Everything else is copy-paste identical to what we wrote in Day 8's `StudentSaveDemo.java`.

---

## 3. CREATE — `persist()` vs `save()`

We already did this on Day 8 using `session.persist()`. Today, formalize the theory with a comparison, since both methods exist in Hibernate and students will see both in real projects/tutorials.

| Aspect | `session.save()` | `session.persist()` |
|---|---|---|
| Return value | Returns the generated ID (`Serializable`) | Returns `void` |
| When SQL runs | May execute `INSERT` immediately | Executes according to transaction/flush timing (more predictable) |
| JPA standard | Not part of JPA (Hibernate-specific) | Part of the JPA specification — the modern, recommended choice |
| Recommended for new code | Older/legacy code | **Yes — use this by default** |

**Full Example — `StudentCreateDemo.java`**

```java
package com.apexswaram.hibernate.main;

import com.apexswaram.hibernate.entity.Student;
import com.apexswaram.hibernate.util.HibernateUtil;
import org.hibernate.Session;
import org.hibernate.SessionFactory;
import org.hibernate.Transaction;

public class StudentCreateDemo {
    public static void main(String[] args) {
        SessionFactory factory = HibernateUtil.getSessionFactory();
        Session session = factory.openSession();
        Transaction transaction = session.beginTransaction();

        try {
            Student s1 = new Student("Priya Sharma", "priya456", "Python Full Stack");
            Student s2 = new Student("Anil Reddy", "anil789", "Data Analytics");

            session.persist(s1);
            session.persist(s2);

            transaction.commit();
            System.out.println("Saved Priya with ID: " + s1.getId());
            System.out.println("Saved Anil with ID: " + s2.getId());

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
- Both `s1` and `s2` are saved within the **same transaction** — if the second `persist()` somehow failed, `transaction.rollback()` would undo the first one too, keeping data consistent (this is the whole point of wrapping operations in a transaction, as introduced Day 7).
- We use `persist()` here (not `save()`) — reinforce this is the modern default choice per the table above.

---

## 4. READ — `get()` vs `load()`

**Concept:** To fetch a single row by its primary key, Hibernate gives us two methods that look similar but behave very differently — this is a classic interview question, so spend real time on the difference.

| Aspect | `session.get()` | `session.load()` |
|---|---|---|
| When data is fetched | Immediately (hits the database right away) | Lazily (returns a "proxy" object, only hits DB when a field is accessed) |
| If record doesn't exist | Returns `null` | Throws `ObjectNotFoundException` when the proxy is accessed |
| Use case | When you're not sure the record exists, or need the data right away | When you're confident the record exists and just need a reference (e.g., to set up a relationship) |

**Full Example — `StudentReadDemo.java`**

```java
package com.apexswaram.hibernate.main;

import com.apexswaram.hibernate.entity.Student;
import com.apexswaram.hibernate.util.HibernateUtil;
import org.hibernate.Session;
import org.hibernate.SessionFactory;

public class StudentReadDemo {
    public static void main(String[] args) {
        SessionFactory factory = HibernateUtil.getSessionFactory();
        Session session = factory.openSession();

        // --- Using get() ---
        Student studentUsingGet = session.get(Student.class, 1);
        if (studentUsingGet != null) {
            System.out.println("Found using get(): " + studentUsingGet);
        } else {
            System.out.println("No student with ID 1 found (get() returned null).");
        }

        // --- Using load() ---
        try {
            Student studentUsingLoad = session.load(Student.class, 2);
            System.out.println("Found using load(): " + studentUsingLoad.getName());
        } catch (Exception e) {
            System.out.println("load() threw an exception because the record wasn't accessible: " + e.getMessage());
        }

        session.close();
    }
}
```

**Explanation:**
- `session.get(Student.class, 1)` → immediately runs `SELECT * FROM student WHERE id=1` and returns a fully-populated `Student` object, or `null` if not found. Notice: **no transaction needed for a simple read** — transactions matter for operations that change data (create/update/delete); reads can technically work without one, though wrapping reads in a transaction is still common practice in larger applications.
- `session.load(Student.class, 2)` → does NOT hit the database immediately. It returns a **proxy** (a placeholder object). Only when we call `.getName()` does Hibernate actually run the `SELECT` — this is called **lazy loading**. If ID 2 doesn't exist, the exception happens at `.getName()`, not at the `load()` call itself — an important and often-confusing detail to demonstrate live.
- **Practical rule of thumb to give students:** default to `get()` unless you have a specific reason to use `load()` — `get()`'s behavior is more predictable for beginners and most everyday use cases.

### 4.1 Reading ALL Records (Preview of HQL, Full Detail on Day 11)

```java
import org.hibernate.query.Query;
import java.util.List;

Session session = factory.openSession();
Query<Student> query = session.createQuery("FROM Student", Student.class);
List<Student> allStudents = query.list();

for (Student s : allStudents) {
    System.out.println(s);
}
session.close();
```

**Explanation:**
- `"FROM Student"` is **HQL (Hibernate Query Language)** — notice it queries the **entity class name** (`Student`), NOT the table name (`student`) — a common early mistake. Full HQL syntax and more complex queries are covered in depth on **Day 11** — today we just need this one line to demonstrate reading multiple rows.

---

## 5. UPDATE — Modifying an Existing Record

**Concept:** To update a row, we first **fetch** the existing entity (so Hibernate knows which row it maps to), **change its fields** using normal Java setters, then **commit** — Hibernate automatically detects the changed fields and generates the correct `UPDATE` SQL. We never write `UPDATE` SQL ourselves.

**Full Example — `StudentUpdateDemo.java`**

```java
package com.apexswaram.hibernate.main;

import com.apexswaram.hibernate.entity.Student;
import com.apexswaram.hibernate.util.HibernateUtil;
import org.hibernate.Session;
import org.hibernate.SessionFactory;
import org.hibernate.Transaction;

public class StudentUpdateDemo {
    public static void main(String[] args) {
        SessionFactory factory = HibernateUtil.getSessionFactory();
        Session session = factory.openSession();
        Transaction transaction = session.beginTransaction();

        try {
            // Step 1: Fetch the existing record
            Student student = session.get(Student.class, 1);

            if (student != null) {
                // Step 2: Modify fields using normal setters
                student.setCourse("Full Stack + AI/ML");

                // Step 3: No explicit "update" call needed here —
                // Hibernate tracks changes automatically (see explanation below)

                transaction.commit();
                System.out.println("Student updated: " + student);
            } else {
                System.out.println("No student with ID 1 to update.");
                transaction.rollback();
            }

        } catch (Exception e) {
            transaction.rollback();
            e.printStackTrace();
        } finally {
            session.close();
        }
    }
}
```

**Explanation — this confuses students the most, so go slowly:**
- Notice we never called anything like `session.update(student)` in this example — we only called `student.setCourse(...)`. Why does this still update the database?
- This is called **automatic dirty checking**. While a `Session` is open, any entity fetched through it (like `student` here) is "attached"/"managed" by that session. Hibernate keeps track of the original field values internally, and when `transaction.commit()` runs, it compares the current object state to what it originally loaded — if anything changed, it generates the `UPDATE` SQL automatically, only for the fields that actually changed.
- **This only works while the session is still open** — if we had called `session.close()` before modifying `student.setCourse(...)`, the change would NOT be saved, because the object would be "detached" and no longer tracked. This is a very common bug for beginners — demonstrate this live by closing the session early and showing the update silently fails to persist.

### 5.1 Explicit `update()` — For Detached Objects

Sometimes we have an object that was loaded in one session (or built manually, e.g. from form data) and we want to update it in a **different**, new session. In that case, we need to explicitly tell Hibernate:

```java
Session session2 = factory.openSession();
Transaction tx2 = session2.beginTransaction();

Student detachedStudent = new Student();
detachedStudent.setId(1);              // must set the ID so Hibernate knows which row
detachedStudent.setName("Ravi Kumar");
detachedStudent.setUsername("ravi123");
detachedStudent.setCourse("Java Full Stack Advanced");

session2.update(detachedStudent);      // explicitly reattach and mark for update
tx2.commit();
session2.close();
```

**Explanation:**
- `session.update()` is needed here because `detachedStudent` was never fetched through `session2` — it's a "detached" object Hibernate doesn't already know about. `update()` tells Hibernate "treat this object as an existing row that needs updating" (based on its `id`).
- **Caution to mention:** every field on a detached object passed to `update()` will overwrite the database row, including fields we didn't intend to change, if they weren't set correctly. This is one reason the "fetch-then-modify" approach (Section 5's main example) is generally preferred over building a detached object by hand.

---

## 6. DELETE — Removing a Record

**Full Example — `StudentDeleteDemo.java`**

```java
package com.apexswaram.hibernate.main;

import com.apexswaram.hibernate.entity.Student;
import com.apexswaram.hibernate.util.HibernateUtil;
import org.hibernate.Session;
import org.hibernate.SessionFactory;
import org.hibernate.Transaction;

public class StudentDeleteDemo {
    public static void main(String[] args) {
        SessionFactory factory = HibernateUtil.getSessionFactory();
        Session session = factory.openSession();
        Transaction transaction = session.beginTransaction();

        try {
            Student student = session.get(Student.class, 3);

            if (student != null) {
                session.remove(student);
                transaction.commit();
                System.out.println("Student with ID 3 deleted.");
            } else {
                System.out.println("No student with ID 3 to delete.");
                transaction.rollback();
            }

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
- Just like update, delete requires **fetching the record first** (`session.get()`), then calling `session.remove(student)` — Hibernate uses the object's `@Id` value to generate `DELETE FROM student WHERE id=?`.
- Note: `session.remove()` is the modern JPA-standard method name. Older Hibernate tutorials/code may show `session.delete()` — mention both names exist so students aren't confused if they see `delete()` in older reference material, but use `remove()` going forward.
- Same rule as update: the record must be fetched through the **currently open session** for automatic tracking to know what to delete — always fetch first, never try to delete a raw `new Student()` with just an ID set unless you're intentionally working with a detached reference (same caveat as Section 5.1).

---

## 7. `saveOrUpdate()` — The "Smart" Method

**Concept:** A convenience method that decides FOR us whether to `INSERT` or `UPDATE`, based on whether the object already has an `id` set.

```java
Session session = factory.openSession();
Transaction transaction = session.beginTransaction();

Student student = new Student("Kavya Reddy", "kavya321", "Java Full Stack");
// student.getId() is currently 0/unset → saveOrUpdate() will INSERT

session.saveOrUpdate(student);
transaction.commit();
session.close();
```

**Explanation:**
- If the entity's identifier is unset (or matches Hibernate's definition of "new"), `saveOrUpdate()` behaves like `save()` (INSERT). If the identifier IS set and Hibernate believes the row already exists, it behaves like `update()`.
- **Modern equivalent:** JPA's `session.merge()` serves a very similar purpose and is the more modern, standard-aligned choice — mention this exists, but `saveOrUpdate()` remains extremely common in real (especially older) Hibernate codebases, so students should recognize it.
- **When is this actually useful?** A great real example: a "save profile" form that's used for BOTH creating a new student and editing an existing one — instead of writing two separate methods, `saveOrUpdate()` lets one method handle both cases based on whether an ID was submitted.

---

## 8. Full CRUD Summary Table

| Operation | Method | Requires Fetch First? | Notes |
|---|---|---|---|
| Create | `session.persist(obj)` | No | Preferred over `save()` for new code |
| Read (single) | `session.get(Class, id)` | N/A | Returns `null` if not found; hits DB immediately |
| Read (single, lazy) | `session.load(Class, id)` | N/A | Returns proxy; throws exception on access if missing |
| Read (all/HQL) | `session.createQuery("FROM Entity")` | N/A | Full HQL syntax covered Day 11 |
| Update (attached) | Fetch + modify fields + commit | Yes | Automatic dirty checking — no explicit call needed |
| Update (detached) | `session.update(obj)` | No (but `id` must be set) | Overwrites all fields — use carefully |
| Delete | `session.remove(obj)` | Yes | Must fetch first (or supply a valid detached reference) |
| Smart Create/Update | `session.saveOrUpdate(obj)` | No | Decides based on whether `id` is set |

---

## 9. In-Class Activity
Ask students to build ONE combined class, `StudentCrudActivity.java`, that in order:
1. Creates 2 new students using `persist()`.
2. Reads and prints ALL students using the HQL query from Section 4.1.
3. Updates one student's course (fetch-then-modify pattern from Section 5).
4. Deletes one student by ID (Section 6).
5. Reads and prints ALL students again — confirm the update and delete are both reflected.

Each step should be its own session + transaction (following the 5-step skeleton from Section 2), not all crammed into one shared session — this reinforces "one unit of work per operation" from Day 7's architecture.

## 10. Recap Questions (End of Class)
1. What's the key difference between `save()` and `persist()`? Which should we prefer in new code?
2. Why does `get()` sometimes hit the database immediately while `load()` doesn't?
3. Why did our update example work without calling `session.update()` explicitly — what is this behavior called?
4. When would you need to call `session.update()` explicitly instead of relying on that automatic behavior?
5. What does `saveOrUpdate()` decide between, and what does it base that decision on?

## 11. Homework
- Modify `StudentDeleteDemo.java` to first check with `get()` whether the student exists, print their name before deleting them, and print a friendly "not found" message otherwise (already shown in the example — have students explain each line back in their own words in a short comment above it, as review).
- Read ahead lightly on HQL syntax (`WHERE`, `ORDER BY`) and the Criteria API — covered in full on Day 11. Today's `"FROM Student"` query was just a preview.

---
*Prepared for JFS Batch 2 — Day 9 of 15 (JSP & Hibernate Module)*
