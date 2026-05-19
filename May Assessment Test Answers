# Answer Key – Paper 1

---

# Session A – Interview Questions Answers

## Java Answers

1. `==` compares memory/reference, `.equals()` compares content.

2. Method overloading means multiple methods with same name but different parameters.

3. Constructor initializes objects automatically during object creation, method performs operations.

4. `this` keyword refers to current object of the class.

5. Inheritance allows one class to acquire properties of another class using `extends`.

6. Array has fixed size, `ArrayList` is dynamic.

7. Encapsulation means binding data and methods together using private variables and public getter/setter methods.

8. Compile-time polymorphism → Method overloading.
   Runtime polymorphism → Method overriding.

9. `break` terminates loop, `continue` skips current iteration.

10. Abstract class can contain abstract and normal methods. Interface mainly contains abstract behavior contracts.

---

## SQL Answers

1.

* `DELETE` → Removes rows.
* `TRUNCATE` → Removes all rows quickly.
* `DROP` → Deletes entire table.

2.

* `PRIMARY KEY` uniquely identifies records.
* `FOREIGN KEY` creates relationship between tables.

3.

* `WHERE` filters rows before grouping.
* `HAVING` filters grouped data.

4. Joins combine rows from multiple tables. Types:

* INNER JOIN
* LEFT JOIN
* RIGHT JOIN
* FULL JOIN

5.

* `CHAR` fixed length.
* `VARCHAR` variable length.

6. Normalization removes redundancy and improves consistency.

7.

* DDL → CREATE, ALTER
* DML → INSERT, UPDATE
* DQL → SELECT
* TCL → COMMIT, ROLLBACK
* DCL → GRANT, REVOKE

8.

* `COUNT(*)` counts all rows.
* `COUNT(column)` ignores NULL values.

9. `GROUP BY` groups similar rows.

10.

* `UNION` removes duplicates.
* `UNION ALL` keeps duplicates.

---

# Session B – Answers

## Java Answers

### 1. Employee ID Validator

```java
public class EmployeeIDValidator {
    public static void main(String[] args) {

        String id = "456781";

        if(id.length() == 6 && id.charAt(0) != '0') {
            System.out.println("Valid Employee ID");
        } else {
            System.out.println("Invalid Employee ID");
        }
    }
}
```

---

### 2. Second Largest Number

```java
public class SecondLargest {
    public static void main(String[] args) {

        int arr[] = {12,45,7,89,23};

        int largest = arr[0];
        int second = arr[0];

        for(int i=0;i<arr.length;i++) {

            if(arr[i] > largest) {
                second = largest;
                largest = arr[i];
            }
            else if(arr[i] > second && arr[i] != largest) {
                second = arr[i];
            }
        }

        System.out.println("Second Largest = " + second);
    }
}
```

---

## SQL Answers

### 3. Employees in IT Department

```sql
SELECT emp_id, emp_name, salary
FROM employees
WHERE department = 'IT';
```

---

### 4. Salary Between 40000 and 60000

```sql
SELECT *
FROM staff
WHERE salary BETWEEN 40000 AND 60000;
```

---

# Session C – Answers

## Java Answers

### 1. Character Frequency

```java
public class CharacterFrequency {
    public static void main(String[] args) {

        String str = "corporate";

        for(int i=0;i<str.length();i++) {

            int count = 1;

            if(str.charAt(i) == ' ')
                continue;

            for(int j=i+1;j<str.length();j++) {

                if(str.charAt(i) == str.charAt(j)) {
                    count++;
                }
            }

            boolean alreadyPrinted = false;

            for(int k=0;k<i;k++) {
                if(str.charAt(i) == str.charAt(k)) {
                    alreadyPrinted = true;
                }
            }

            if(!alreadyPrinted) {
                System.out.println(str.charAt(i) + " -> " + count);
            }
        }
    }
}
```

---

### 2. Remove Duplicate Elements

```java
public class RemoveDuplicates {
    public static void main(String[] args) {

        int arr[] = {4,7,2,4,9,7,1,2};

        for(int i=0;i<arr.length;i++) {

            boolean duplicate = false;

            for(int j=0;j<i;j++) {
                if(arr[i] == arr[j]) {
                    duplicate = true;
                }
            }

            if(!duplicate) {
                System.out.print(arr[i] + " ");
            }
        }
    }
}
```

---

### 3. Banking Transaction Menu

```java
import java.util.Scanner;

public class BankingMenu {
    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int balance = 10000;

        System.out.println("1.Deposit");
        System.out.println("2.Withdraw");
        System.out.println("3.Check Balance");

        int choice = sc.nextInt();

        switch(choice) {

            case 1:
                System.out.println("Enter amount:");
                int deposit = sc.nextInt();
                balance += deposit;
                System.out.println("Balance = " + balance);
                break;

            case 2:
                System.out.println("Enter amount:");
                int withdraw = sc.nextInt();

                if(withdraw <= balance) {
                    balance -= withdraw;
                    System.out.println("Balance = " + balance);
                } else {
                    System.out.println("Insufficient Balance");
                }
                break;

            case 3:
                System.out.println("Balance = " + balance);
                break;

            default:
                System.out.println("Invalid Choice");
        }
    }
}
```

---

## SQL Answers

### 4. Department Wise Highest Salary

```sql
SELECT department, MAX(salary) AS highest_salary
FROM employee_salary
GROUP BY department;
```

---

### 5. Employee and Department Details using JOIN

```sql
SELECT e.emp_name,
       d.dept_name,
       e.salary
FROM employees_data e
INNER JOIN departments d
ON e.dept_id = d.dept_id;
```

---

### 6. Departments Having More Than One Employee

```sql
SELECT department, COUNT(*) AS total_employees
FROM company_employees
GROUP BY department
HAVING COUNT(*) > 1;
```

---

# Session D – Answers

## Java Answers

### 1. Longest Word in Sentence

```java
public class LongestWord {
    public static void main(String[] args) {

        String str = "Java developers solve real world problems";

        String words[] = str.split(" ");

        String longest = "";

        for(String word : words) {

            if(word.length() > longest.length()) {
                longest = word;
            }
        }

        System.out.println("Longest Word = " + longest);
    }
}
```

---

### 2. Electricity Bill Generator

```java
import java.util.Scanner;

public class ElectricityBill {
    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.println("Enter Customer Name:");
        String name = sc.nextLine();

        System.out.println("Enter Units:");
        int units = sc.nextInt();

        double bill;

        if(units <= 100) {
            bill = units * 2;
        }
        else if(units <= 200) {
            bill = units * 4;
        }
        else {
            bill = units * 6;
        }

        System.out.println("Customer Name : " + name);
        System.out.println("Units : " + units);
        System.out.println("Bill Amount : " + bill);
    }
}
```

---

## SQL Answers

### 3. Second Highest Salary

```sql
SELECT MAX(salary) AS second_highest_salary
FROM salary_details
WHERE salary < (
    SELECT MAX(salary)
    FROM salary_details
);
```

---

### 4. Customer Purchase Report

```sql
SELECT c.customer_name,
       SUM(o.amount) AS total_purchase
FROM customers c
JOIN orders o
ON c.customer_id = o.customer_id
GROUP BY c.customer_name
ORDER BY total_purchase DESC;
```

---

# Answer Key – Paper 2

---

# Session A – Interview Questions Answers

## Java Answers

1.

* Local Variable → inside method
* Instance Variable → inside class outside method
* Static Variable → shared among all objects

2. Constructor overloading means multiple constructors with different parameters.

3. `static` belongs to class, not object.

4.

* `String` immutable
* `StringBuffer` mutable and thread-safe
* `StringBuilder` mutable and faster

5. Exception handling manages runtime errors using `try`, `catch`, `finally`.

6.

* `for` loop when iterations known
* `while` loop when condition based

7. Objects are created using `new` keyword.

8. Java supports pass by value only.

9.

* Overloading → same method different parameters
* Overriding → subclass redefines parent method

10. Packages organize classes and avoid naming conflicts.

---

## SQL Answers

1.

* `PRIMARY KEY` cannot contain NULL.
* `UNIQUE` can contain NULL.

2. Examples:

* INT
* VARCHAR
* DATE
* FLOAT

3. `ORDER BY` sorts records.

4.

* INNER JOIN returns matching rows.
* LEFT JOIN returns all left table rows.

5. Aggregate functions:

* COUNT
* SUM
* AVG
* MAX
* MIN

6. Aliases provide temporary names.

7.

* `WHERE` filters rows.
* `ON` defines join condition.

8. `AUTO_INCREMENT` automatically generates values.

9.

* `COMMIT` saves transaction.
* `ROLLBACK` cancels transaction.

10. `DISTINCT` removes duplicate values.

---

# Session B – Answers

## Java Answers

### 1. Count Uppercase and Lowercase

```java
public class CountLetters {
    public static void main(String[] args) {

        String str = "JavaProgramming";

        int upper = 0;
        int lower = 0;

        for(int i=0;i<str.length();i++) {

            char ch = str.charAt(i);

            if(ch >= 'A' && ch <= 'Z') {
                upper++;
            }
            else if(ch >= 'a' && ch <= 'z') {
                lower++;
            }
        }

        System.out.println("Uppercase Letters = " + upper);
        System.out.println("Lowercase Letters = " + lower);
    }
}
```

---

### 2. Reverse Each Word

```java
public class ReverseWords {
    public static void main(String[] args) {

        String str = "Java is powerful";

        String words[] = str.split(" ");

        for(String word : words) {

            for(int i=word.length()-1;i>=0;i--) {
                System.out.print(word.charAt(i));
            }

            System.out.print(" ");
        }
    }
}
```

---

## SQL Answers

### 3. Products Greater Than 5000

```sql
SELECT *
FROM products
WHERE price > 5000;
```

---

### 4. Students Sorted by Marks

```sql
SELECT *
FROM students
ORDER BY marks DESC;
```

---

# Session C – Answers

## Java Answers

### 1. Missing Number in Array

```java
public class MissingNumber {
    public static void main(String[] args) {

        int arr[] = {1,2,3,4,5,6,7,9,10};

        int total = 55;
        int sum = 0;

        for(int i=0;i<arr.length;i++) {
            sum += arr[i];
        }

        System.out.println("Missing Number = " + (total - sum));
    }
}
```

---

### 2. String Rotation

```java
public class StringRotation {
    public static void main(String[] args) {

        String s1 = "ABCD";
        String s2 = "CDAB";

        String temp = s1 + s1;

        if(temp.contains(s2)) {
            System.out.println("Strings are rotations");
        }
        else {
            System.out.println("Not rotations");
        }
    }
}
```

---

### 3. Student Grade Management

```java
import java.util.Scanner;

public class StudentGrade {
    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int total = 0;

        for(int i=1;i<=5;i++) {

            System.out.println("Enter Marks:");
            total += sc.nextInt();
        }

        double avg = total / 5.0;

        System.out.println("Total = " + total);
        System.out.println("Average = " + avg);

        if(avg >= 90)
            System.out.println("Grade A");
        else if(avg >= 75)
            System.out.println("Grade B");
        else if(avg >= 60)
            System.out.println("Grade C");
        else
            System.out.println("Grade D");
    }
}
```

---

## SQL Answers

### 4. Total Salary Department Wise

```sql
SELECT department,
       SUM(salary) AS total_salary
FROM office_staff
GROUP BY department;
```

---

### 5. Employees Without Bonus

```sql
SELECT e.emp_name
FROM employees e
LEFT JOIN bonus b
ON e.emp_id = b.emp_id
WHERE b.bonus_amount IS NULL;
```

---

### 6. Average Salary Greater Than 50000

```sql
SELECT department,
       AVG(salary) AS average_salary
FROM salary_report
GROUP BY department
HAVING AVG(salary) > 50000;
```

---

# Session D – Answers

## Java Answers

### 1. Compress Consecutive Characters

```java
public class CompressString {
    public static void main(String[] args) {

        String str = "aaabbccccdde";

        int count = 1;

        for(int i=0;i<str.length();i++) {

            if(i < str.length()-1 &&
               str.charAt(i) == str.charAt(i+1)) {

                count++;
            }
            else {
                System.out.print(str.charAt(i));
                System.out.print(count);
                count = 1;
            }
        }
    }
}
```

---

### 2. Online Shopping Bill Generator

```java
import java.util.Scanner;

public class ShoppingBill {
    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.println("Enter Product Name:");
        String product = sc.nextLine();

        System.out.println("Enter Quantity:");
        int qty = sc.nextInt();

        System.out.println("Enter Price:");
        double price = sc.nextDouble();

        double subtotal = qty * price;

        double discount = 0;

        if(subtotal > 5000) {
            discount = subtotal * 0.10;
        }

        double afterDiscount = subtotal - discount;

        double gst = afterDiscount * 0.18;

        double finalBill = afterDiscount + gst;

        System.out.println("Subtotal = " + subtotal);
        System.out.println("Discount = " + discount);
        System.out.println("GST = " + gst);
        System.out.println("Final Bill = " + finalBill);
    }
}
```

---

## SQL Answers

### 3. Duplicate Employee Names

```sql
SELECT emp_name,
       COUNT(*) AS total_count
FROM employee_records
GROUP BY emp_name
HAVING COUNT(*) > 1;
```

---

### 4. Monthly Sales Analysis

```sql
SELECT sales_person,
       region,
       SUM(amount) AS total_sales
FROM sales
GROUP BY sales_person, region
HAVING SUM(amount) > 50000
ORDER BY total_sales DESC;
```
