# JDBC executeUpdate() Notes

## What is executeUpdate()?

**executeUpdate()** is used to execute SQL queries that modify the database.

### Used For:

* INSERT
* UPDATE
* DELETE
* ALTER
* DROP
* TRUNCATE

### Syntax

```java
int rows = st.executeUpdate(sql);
```

### Return Type

```java
int
```

Returns the number of affected rows.

---

# 1. UPDATE

### Definition

Used to modify existing records in a table.

### SQL Syntax

```sql
UPDATE student
SET city='Hyderabad'
WHERE id=101;
```

### JDBC Code

```java
String sql =
"UPDATE student SET city='Hyderabad' WHERE id=101";

int rows = st.executeUpdate(sql);

System.out.println(rows + " Record Updated");
```

### Output

```text
1 Record Updated
```

---

# 2. DELETE

### Definition

Used to remove records from a table.

### SQL Syntax

```sql
DELETE FROM student
WHERE id=101;
```

### JDBC Code

```java
String sql =
"DELETE FROM student WHERE id=101";

int rows = st.executeUpdate(sql);

System.out.println(rows + " Record Deleted");
```

### Output

```text
1 Record Deleted
```

---

# 3. ALTER

### Definition

Used to change the structure of a table.

### Example

Add a new column.

### SQL Syntax

```sql
ALTER TABLE student
ADD email VARCHAR(50);
```

### JDBC Code

```java
String sql =
"ALTER TABLE student ADD email VARCHAR(50)";

st.executeUpdate(sql);

System.out.println("Table Altered Successfully");
```

### Output

```text
Table Altered Successfully
```

---

# 4. DROP

### Definition

Used to permanently delete an entire table.

### SQL Syntax

```sql
DROP TABLE student;
```

### JDBC Code

```java
String sql =
"DROP TABLE student";

st.executeUpdate(sql);

System.out.println("Table Dropped Successfully");
```

### Output

```text
Table Dropped Successfully
```

### Note

⚠️ Table structure and all records will be deleted permanently.

---

# 5. TRUNCATE

### Definition

Used to remove all records from a table while keeping the table structure.

### SQL Syntax

```sql
TRUNCATE TABLE student;
```

### JDBC Code

```java
String sql =
"TRUNCATE TABLE student";

st.executeUpdate(sql);

System.out.println("Table Truncated Successfully");
```

### Output

```text
Table Truncated Successfully
```

### Note

* Records removed
* Structure remains

---

# 6. COMMIT

### Definition

Used to permanently save changes made to the database.

### SQL Syntax

```sql
COMMIT;
```

### JDBC Code

```java
con.setAutoCommit(false);

String sql =
"INSERT INTO student VALUES(101,'Mahesh','Vijayawada')";

st.executeUpdate(sql);

con.commit();

System.out.println("Transaction Committed");
```

### Output

```text
Transaction Committed
```

---

# Real World Example of COMMIT

### Without Commit

```text
ATM Withdrawal
      ↓
Money deducted
      ↓
System crash
      ↓
Transaction not saved
```

### With Commit

```text
ATM Withdrawal
      ↓
Money deducted
      ↓
COMMIT
      ↓
Changes permanently saved
```

---

# Quick Revision Table

| Command  | Purpose                            |
| -------- | ---------------------------------- |
| INSERT   | Add new records                    |
| UPDATE   | Modify existing records            |
| DELETE   | Remove specific records            |
| ALTER    | Change table structure             |
| DROP     | Delete table permanently           |
| TRUNCATE | Remove all records, keep structure |
| COMMIT   | Save changes permanently           |

---

# Interview Questions

### Which method is used for INSERT, UPDATE, DELETE?

```java
executeUpdate()
```

### Can executeUpdate() execute ALTER?

```text
Yes
```

### Can executeUpdate() execute DROP?

```text
Yes
```

### Can executeUpdate() execute TRUNCATE?

```text
Yes
```

### What is the return type of executeUpdate()?

```java
int
```

### Difference Between DELETE and TRUNCATE?

| DELETE                           | TRUNCATE                             |
| -------------------------------- | ------------------------------------ |
| Removes selected rows            | Removes all rows                     |
| WHERE allowed                    | WHERE not allowed                    |
| Slower                           | Faster                               |
| Can rollback (transactional DBs) | Usually cannot rollback after commit |

---

### One-Line Definitions

**UPDATE:** Used to modify existing records in a table.

**DELETE:** Used to remove records from a table.

**ALTER:** Used to change the structure of a table.

**DROP:** Used to permanently delete a table.

**TRUNCATE:** Used to remove all records while keeping the table structure.

**COMMIT:** Used to permanently save changes made to the database.

### Easy Memory Trick

**I U D A D T C**

```text
INSERT
UPDATE
DELETE
ALTER
DROP
TRUNCATE
COMMIT
```

All these operations are commonly executed using **executeUpdate()** in JDBC.
