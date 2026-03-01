# Full-Stack-Java-Notes

# Core Java 

##  By Maheswaram | ApexSwaram


---

# TABLE OF CONTENTS

1. [Java History](#1-java-history)
2. [Features of Java](#2-features-of-java)
3. [Difference Between JDK, JRE, and JVM](#3-difference-between-jdk-jre-and-jvm)
4. [Data Types in Java](#4-data-types-in-java)
5. [Operators in Java](#5-operators-in-java)
6. [Variables in Java](#6-variables-in-java)
7. [Decision Making Statements](#7-decision-making-statements)
8. [Loop Statements](#8-loop-statements)
9. [Jump Statements](#9-jump-statements)
10. [Strings and String Methods](#10-strings-and-string-methods)
11. [Methods in Java](#11-methods-in-java)
12. [Arrays in Java](#12-arrays-in-java)
13. [Oop's in Java] (#Oops-in-java)
14. [What is the Java Collection Framework?](#1-what-is-the-java-collection-framework)
15. [JCF Hierarchy Overview](#2-jcf-hierarchy-overview)
16. [List Interface](#3-list-interface)
   - [What is a List?](#what-is-a-list)
   - [Types of List](#types-of-list)
   - [Creating a List](#creating-a-list)
   - [List Methods](#list-methods)
16. [Set Interface](#4-set-interface)
   - [What is a Set?](#what-is-a-set)
   - [Types of Set](#types-of-set)
   - [Creating a Set](#creating-a-set)
   - [Set Methods](#set-methods)

---

# 1. Java History

## What is Java?

Java is a **high-level, class-based, object-oriented programming language** that is designed to have as few implementation dependencies as possible. It was originally developed so that application developers could write once and run anywhere (WORA).

---

## Timeline of Java History

| Year | Event |
|------|-------|
| **1991** | James Gosling and his team at **Sun Microsystems** started developing a language called **"Oak"** inside the **Green Project**. The goal was to create a language for embedded systems (like digital cable TV boxes). |
| **1992** | The Green Project was completed. Oak was renamed because "Oak" was already a registered trademark. It was then renamed to **"Java"** (named after the Indonesian island of Java, which is famous for coffee). |
| **1995** | Java was officially released to the public by Sun Microsystems. It gained popularity because of the World Wide Web (internet). |
| **1997** | Sun Microsystems attempted to turn Java into a proprietary standard. The **Java Community Process (JCP)** was formed. |
| **2006** | Sun Microsystems released Java as **open source** under the **GNU General Public License (GPL)**. |
| **2010** | **Oracle Corporation** acquired Sun Microsystems and took ownership of Java. |
| **2017** | Oracle changed the Java licensing model. Java 9+ moved to a **new release cycle** (every 6 months). |
| **Present** | Java is one of the **most popular and widely used programming languages** in the world. |

---

## Key People

- **James Gosling** — Known as the "Father of Java." He led the development of Java at Sun Microsystems.
- **Sun Microsystems** — The company that originally created and maintained Java.
- **Oracle Corporation** — The current owner of Java (after acquiring Sun Microsystems in 2010).

---

## Why Was Java Created?

1. To create a **platform-independent** language (works on any OS without recompilation).
2. To build applications for **embedded systems** (like set-top boxes, smart devices).
3. To provide a language that is **simple, secure, and object-oriented**.

---
---

# 2. Features of Java

Java has many features that make it popular. The important ones are:

---

## 2.1 Simple

- Java is very **easy to learn** compared to C and C++.
- It does **not use pointers**, which makes it simpler.
- It has a simple and clean **syntax**.

## 2.2 Object-Oriented

- Everything in Java is based on **objects and classes**.
- Supports concepts like **Inheritance, Polymorphism, Encapsulation, and Abstraction**.

## 2.3 Platform Independent (Write Once, Run Anywhere — WORA)

- Java code is compiled into **bytecode** (not machine code directly).
- Bytecode can run on **any platform** that has a JVM installed.
- This is Java's most important feature.

```
Java Code  →  [Compiler]  →  Bytecode (.class file)  →  [JVM]  →  Runs on Any OS
```

## 2.4 Portable

- Because of platform independence, Java programs can be **moved from one computer to another** without any changes.

## 2.5 Robust

- Java has **strong type checking** at compile time.
- It handles errors using **Exception Handling**.
- It uses **Garbage Collection** to manage memory automatically.

## 2.6 Secure

- Java does **not allow direct access to memory** (no pointers).
- It has a **Security Manager** that controls access to resources.
- It uses **class loaders** and **bytecode verification** for security.

## 2.7 Multi-Threaded

- Java supports **multi-threading**, which means multiple tasks can run at the same time.
- This makes Java applications **faster and more efficient**.

## 2.8 High Performance

- Java uses **Just-In-Time (JIT) Compilation** to convert bytecode to machine code at runtime, which improves performance.

## 2.9 Dynamic

- Java supports **dynamic loading of classes** at runtime.
- New classes can be added without stopping the application.

## 2.10 Distributed

- Java supports **distributed computing**, meaning programs can run across multiple computers connected via a network.

---
---

# 3. Difference Between JDK, JRE, and JVM

These are three very important terms in Java. Understanding them is essential.

---

## 3.1 JVM — Java Virtual Machine

### Definition:
> JVM is a **virtual machine** that runs Java bytecode. It is the **runtime engine** that executes Java programs. JVM is **platform-specific** — there is a different JVM for Windows, Linux, Mac, etc.

### Responsibilities of JVM:
1. **Loads** the .class file (bytecode).
2. **Verifies** the bytecode (checks for errors and security).
3. **Executes** the bytecode.
4. **Manages memory** (Garbage Collection).

### How JVM Works:

```
.class file (Bytecode)
        ↓
  ┌─────────────┐
  │    JVM      │
  │  ┌───────┐  │
  │  │ Class │  │  ← Loads and verifies bytecode
  │  │ Loader│  │
  │  └───┬───┘  │
  │      ↓      │
  │  ┌───────┐  │
  │  │ Byte  │  │  ← Checks bytecode is valid
  │  │ Code  │  │
  │  │Verifier│ │
  │  └───┬───┘  │
  │      ↓      │
  │  ┌───────┐  │
  │  │ JIT   │  │  ← Converts bytecode to machine code
  │  │Compiler│ │
  │  └───┬───┘  │
  │      ↓      │
  │  ┌───────┐  │
  │  │Execute│  │  ← Runs the program
  │  └───────┘  │
  └─────────────┘
```

---

## 3.2 JRE — Java Runtime Environment

### Definition:
> JRE is the **environment** needed to **run** a Java program. It contains the **JVM** and the **Java Standard Libraries (APIs)**.

### What is inside JRE?
- **JVM** (to execute bytecode)
- **Java Standard Libraries** (like java.lang, java.util, java.io, etc.)

### Important:
> With JRE, you can only **RUN** Java programs. You **CANNOT compile** Java programs with JRE alone.

---

## 3.3 JDK — Java Development Kit

### Definition:
> JDK is the **complete package** needed to **develop and run** Java programs. It contains the **JRE** and the **Java Compiler (javac)** and other development tools.

### What is inside JDK?
- **JRE** (which includes JVM + Standard Libraries)
- **Java Compiler (javac)** — to compile .java files into .class files
- **Debugger (jdb)**
- **Other tools** like javadoc, jar, etc.

---

## Comparison Table

| Feature | JVM | JRE | JDK |
|--------|-----|-----|-----|
| **Full Name** | Java Virtual Machine | Java Runtime Environment | Java Development Kit |
| **Purpose** | Executes bytecode | Runs Java programs | Develops and runs Java programs |
| **Contains** | Execution engine | JVM + Libraries | JRE + Compiler + Tools |
| **Can Run Programs?** | Yes | Yes | Yes |
| **Can Compile Programs?** | No | No | Yes |
| **Who Needs It?** | (Part of JRE) | End Users | Developers |

---

## Visual Diagram

```
┌──────────────────────────────────────────┐
│                  JDK                      │
│  ┌────────────────────────────────────┐  │
│  │              JRE                   │  │
│  │  ┌───────────────────────────────┐ │  │
│  │  │          JVM                  │ │  │
│  │  │  (Executes Bytecode)          │ │  │
│  │  └───────────────────────────────┘ │  │
│  │  + Java Standard Libraries         │  │
│  └────────────────────────────────────┘  │
│  + Java Compiler (javac)                  │
│  + Debugger (jdb)                         │
│  + Other Tools (javadoc, jar, etc.)       │
└──────────────────────────────────────────┘
```

---
---

# 4. Data Types in Java

A **data type** defines the type of data that a variable can store — like integers, decimal numbers, characters, or boolean values.

Java has **two** categories of data types:

```
Data Types
├── Primitive Data Types (8 types)
│   ├── Numeric
│   │   ├── Integer Types: byte, short, int, long
│   │   └── Floating Point Types: float, double
│   ├── Character Type: char
│   └── Boolean Type: boolean
└── Non-Primitive Data Types (Reference Types)
    ├── String
    ├── Array
    ├── Class
    └── Interface
```

---

## 4.1 Primitive Data Types

Primitive data types are the **basic building blocks**. They store **simple values** directly in memory.

Java has **8 primitive data types**:

| Data Type | Size | Range | Default Value | Example |
|-----------|------|-------|---------------|---------|
| **byte** | 1 byte (8 bits) | -128 to 127 | 0 | `byte b = 100;` |
| **short** | 2 bytes (16 bits) | -32,768 to 32,767 | 0 | `short s = 30000;` |
| **int** | 4 bytes (32 bits) | -2,147,483,648 to 2,147,483,647 | 0 | `int i = 100000;` |
| **long** | 8 bytes (64 bits) | -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 | 0L | `long l = 100000L;` |
| **float** | 4 bytes (32 bits) | 3.4e-38 to 3.4e+38 | 0.0f | `float f = 3.14f;` |
| **double** | 8 bytes (64 bits) | 1.7e-308 to 1.7e+308 | 0.0 | `double d = 3.14;` |
| **char** | 2 bytes (16 bits) | 0 to 65,535 (Unicode) | '\u0000' | `char c = 'A';` |
| **boolean** | 1 bit (but usually 1 byte in memory) | true or false | false | `boolean b = true;` |

---

### Important Notes on Primitive Types:

- **int** is the **default** integer type in Java. If you write `100`, Java treats it as `int`.
- **double** is the **default** floating-point type. If you write `3.14`, Java treats it as `double`.
- For **long**, you must add `L` or `l` at the end: `long l = 100000L;`
- For **float**, you must add `f` or `F` at the end: `float f = 3.14f;`
- **char** stores a single character. It uses **Unicode** (2 bytes), so it can store any character from any language.

---

### Example Program: Primitive Data Types

```java
public class PrimitiveDataTypes {
    public static void main(String[] args) {
        
        // Integer Types
        byte myByte = 127;
        short myShort = 32000;
        int myInt = 100000;
        long myLong = 9999999999L;
        
        // Floating Point Types
        float myFloat = 3.14f;
        double myDouble = 9.99999999;
        
        // Character Type
        char myChar = 'A';
        
        // Boolean Type
        boolean myBoolean = true;
        
        // Printing all values
        System.out.println("byte value: " + myByte);
        System.out.println("short value: " + myShort);
        System.out.println("int value: " + myInt);
        System.out.println("long value: " + myLong);
        System.out.println("float value: " + myFloat);
        System.out.println("double value: " + myDouble);
        System.out.println("char value: " + myChar);
        System.out.println("boolean value: " + myBoolean);
    }
}
```

**Output:**
```
byte value: 127
short value: 32000
int value: 100000
long value: 9999999999
float value: 3.14
double value: 9.99999999
char value: A
boolean value: true
```

---

## 4.2 Non-Primitive Data Types (Reference Types)

Non-primitive data types are **not predefined** by Java (except String). They are **created by the programmer** or come from Java libraries. They store a **reference (address)** to the actual data in memory, not the data itself.

### Types of Non-Primitive Data Types:

| Type | Description | Example |
|------|-------------|---------|
| **String** | A sequence of characters. It is a **class** in Java. | `String name = "Java";` |
| **Array** | A collection of elements of the **same data type**. | `int[] arr = {1, 2, 3};` |
| **Class** | A user-defined data type (blueprint for objects). | `Student s = new Student();` |
| **Interface** | A type that defines a contract (set of methods). | `Runnable r = ...;` |

### Key Differences: Primitive vs Non-Primitive

| Feature | Primitive | Non-Primitive |
|---------|-----------|---------------|
| **Predefined?** | Yes (8 types) | No (user-defined or from libraries) |
| **What they store** | Actual value | Reference (memory address) |
| **Default value** | 0, 0.0, false, '\u0000' | null |
| **Size** | Fixed size | Variable size |
| **Examples** | int, double, char, boolean | String, Array, Class |
| **Start with** | Lowercase | Uppercase (e.g., String, Integer) |

---
---

# 5. Operators in Java

An **operator** is a symbol that is used to perform operations on one or more operands (values or variables).

Java has **8 types** of operators:

---

## 5.1 Unary Operators

Unary operators work on **only one operand**.

| Operator | Name | Description | Example |
|----------|------|-------------|---------|
| `+` | Unary Plus | Makes a value positive (usually not needed) | `+a` |
| `-` | Unary Minus | Makes a value negative | `-a` |
| `++` | Increment | Increases value by 1 | `a++` or `++a` |
| `--` | Decrement | Decreases value by 1 | `a--` or `--a` |
| `!` | Logical NOT | Reverses boolean value | `!true` → `false` |
| `~` | Bitwise NOT | Flips all bits | `~a` |

### Pre and Post Increment/Decrement:

- **Post-increment (`a++`)**: The **current value is used first**, then incremented.
- **Pre-increment (`++a`)**: The value is **incremented first**, then used.
- Same logic applies for decrement (`a--` and `--a`).

```java
public class UnaryOperatorDemo {
    public static void main(String[] args) {
        int a = 10;
        
        System.out.println("a = " + a);           // Output: a = 10
        System.out.println("a++ = " + a++);       // Output: a++ = 10  (prints 10, then a becomes 11)
        System.out.println("a = " + a);           // Output: a = 11
        System.out.println("++a = " + (++a));     // Output: ++a = 12  (a becomes 12, then prints 12)
        System.out.println("a-- = " + a--);       // Output: a-- = 12  (prints 12, then a becomes 11)
        System.out.println("--a = " + (--a));     // Output: --a = 10  (a becomes 10, then prints 10)
        
        boolean flag = true;
        System.out.println("!flag = " + !flag);   // Output: !flag = false
    }
}
```

**Output:**
```
a = 10
a++ = 10
a = 11
++a = 12
a-- = 12
--a = 10
!flag = false
```

---

## 5.2 Arithmetic Operators

Arithmetic operators are used to perform **mathematical operations**.

| Operator | Name | Description | Example |
|----------|------|-------------|---------|
| `+` | Addition | Adds two values | `10 + 5 = 15` |
| `-` | Subtraction | Subtracts second from first | `10 - 5 = 5` |
| `*` | Multiplication | Multiplies two values | `10 * 5 = 50` |
| `/` | Division | Divides first by second | `10 / 5 = 2` |
| `%` | Modulus (Remainder) | Returns the remainder after division | `10 % 3 = 1` |

### Important Notes:
- **Integer Division**: `10 / 3 = 3` (not 3.33). Java truncates the decimal part when both operands are integers.
- **To get decimal result**, at least one operand must be `float` or `double`: `10.0 / 3 = 3.3333`
- **Modulus** works with negative numbers too: `-10 % 3 = -1`

```java
public class ArithmeticOperatorDemo {
    public static void main(String[] args) {
        int a = 10;
        int b = 3;
        
        System.out.println("a + b = " + (a + b));   // 13
        System.out.println("a - b = " + (a - b));   // 7
        System.out.println("a * b = " + (a * b));   // 30
        System.out.println("a / b = " + (a / b));   // 3 (integer division)
        System.out.println("a % b = " + (a % b));   // 1
        
        // Floating point division
        double c = 10.0;
        System.out.println("c / b = " + (c / b));   // 3.3333333333333335
    }
}
```

**Output:**
```
a + b = 13
a - b = 7
a * b = 30
a / b = 3
a % b = 1
c / b = 3.3333333333333335
```

---

## 5.3 Shift Operators

Shift operators are used to shift the **binary representation** of an integer to the left or right.

| Operator | Name | Description | Example |
|----------|------|-------------|---------|
| `<<` | Left Shift | Shifts bits to the left. Equivalent to multiplying by 2. | `a << 2` |
| `>>` | Right Shift (Signed) | Shifts bits to the right. Equivalent to dividing by 2. Preserves the sign bit. | `a >> 2` |
| `>>>` | Right Shift (Unsigned) | Shifts bits to the right. Fills leftmost bits with 0 (ignores sign). | `a >>> 2` |

```java
public class ShiftOperatorDemo {
    public static void main(String[] args) {
        int a = 8;   // Binary: 1000
        
        System.out.println("a << 2 = " + (a << 2));   // 8 * 4 = 32  (Binary: 100000)
        System.out.println("a >> 1 = " + (a >> 1));   // 8 / 2 = 4   (Binary: 100)
        
        int negative = -8;
        System.out.println("-8 >> 1 = " + (negative >> 1));    // -4 (sign preserved)
        System.out.println("-8 >>> 1 = " + (negative >>> 1));  // 2147483644 (sign NOT preserved)
    }
}
```

**Output:**
```
a << 2 = 32
a >> 1 = 4
-8 >> 1 = -4
-8 >>> 1 = 2147483644
```

---

## 5.4 Relational Operators

Relational operators are used to **compare** two values. They always return a **boolean** value (`true` or `false`).

| Operator | Name | Description | Example |
|----------|------|-------------|---------|
| `==` | Equal to | Returns true if both values are equal | `10 == 10` → `true` |
| `!=` | Not equal to | Returns true if values are not equal | `10 != 5` → `true` |
| `>` | Greater than | Returns true if first is greater | `10 > 5` → `true` |
| `<` | Less than | Returns true if first is smaller | `5 < 10` → `true` |
| `>=` | Greater than or equal | Returns true if first is greater or equal | `10 >= 10` → `true` |
| `<=` | Less than or equal | Returns true if first is less or equal | `5 <= 10` → `true` |

```java
public class RelationalOperatorDemo {
    public static void main(String[] args) {
        int a = 10;
        int b = 20;
        
        System.out.println("a == b: " + (a == b));   // false
        System.out.println("a != b: " + (a != b));   // true
        System.out.println("a > b: " + (a > b));     // false
        System.out.println("a < b: " + (a < b));     // true
        System.out.println("a >= b: " + (a >= b));   // false
        System.out.println("a <= b: " + (a <= b));   // true
    }
}
```

**Output:**
```
a == b: false
a != b: true
a > b: false
a < b: true
a >= b: false
a <= b: true
```

---

## 5.5 Bitwise Operators

Bitwise operators work on the **binary (bit) level** of integer values.

| Operator | Name | Description |
|----------|------|-------------|
| `&` | Bitwise AND | Returns 1 if **both** bits are 1 |
| `\|` | Bitwise OR | Returns 1 if **at least one** bit is 1 |
| `^` | Bitwise XOR | Returns 1 if bits are **different** |
| `~` | Bitwise NOT | Flips all bits (0→1, 1→0) |

### Truth Table:

| A | B | A & B | A \| B | A ^ B |
|---|---|-------|--------|-------|
| 0 | 0 | 0 | 0 | 0 |
| 0 | 1 | 0 | 1 | 1 |
| 1 | 0 | 0 | 1 | 1 |
| 1 | 1 | 1 | 1 | 0 |

```java
public class BitwiseOperatorDemo {
    public static void main(String[] args) {
        int a = 5;   // Binary: 0101
        int b = 3;   // Binary: 0011
        
        System.out.println("a & b = " + (a & b));   // 0001 = 1
        System.out.println("a | b = " + (a | b));   // 0111 = 7
        System.out.println("a ^ b = " + (a ^ b));   // 0110 = 6
        System.out.println("~a = " + (~a));          // -6
    }
}
```

**Output:**
```
a & b = 1
a | b = 7
a ^ b = 6
~a = -6
```

---

## 5.6 Logical Operators

Logical operators are used to perform **logical operations** on boolean values. They return `true` or `false`.

| Operator | Name | Description | Example |
|----------|------|-------------|---------|
| `&&` | Logical AND | Returns `true` if **both** conditions are true | `true && false` → `false` |
| `\|\|` | Logical OR | Returns `true` if **at least one** condition is true | `true \|\| false` → `true` |
| `!` | Logical NOT | Reverses the boolean value | `!true` → `false` |

### Short-Circuit Evaluation:
- **`&&` (Short-Circuit AND)**: If the **first condition is false**, the second condition is **NOT evaluated**.
- **`||` (Short-Circuit OR)**: If the **first condition is true**, the second condition is **NOT evaluated**.

```java
public class LogicalOperatorDemo {
    public static void main(String[] args) {
        boolean a = true;
        boolean b = false;
        
        System.out.println("a && b = " + (a && b));   // false
        System.out.println("a || b = " + (a || b));   // true
        System.out.println("!a = " + (!a));            // false
        System.out.println("!b = " + (!b));            // true
        
        // Short-circuit example
        int x = 0;
        // Second condition is NOT checked because first is false
        if (false && (++x > 0)) {
            System.out.println("This will not print");
        }
        System.out.println("x = " + x);  // x = 0 (x was NOT incremented)
    }
}
```

**Output:**
```
a && b = false
a || b = true
!a = false
!b = true
x = 0
```

---

## 5.7 Ternary Operator

The ternary operator is a **shortcut for if-else**. It is the only operator in Java that takes **three operands**.

### Syntax:
```
variable = (condition) ? valueIfTrue : valueIfFalse;
```

### How it works:
1. The **condition** is evaluated.
2. If the condition is `true`, `valueIfTrue` is returned.
3. If the condition is `false`, `valueIfFalse` is returned.

```java
public class TernaryOperatorDemo {
    public static void main(String[] args) {
        int a = 10;
        int b = 20;
        
        // Find the maximum of two numbers
        int max = (a > b) ? a : b;
        System.out.println("Maximum: " + max);   // 20
        
        // Check if a number is even or odd
        int num = 15;
        String result = (num % 2 == 0) ? "Even" : "Odd";
        System.out.println(num + " is " + result);  // 15 is Odd
        
        // Nested Ternary (find max of three numbers)
        int x = 5, y = 10, z = 3;
        int maximum = (x > y) ? ((x > z) ? x : z) : ((y > z) ? y : z);
        System.out.println("Max of 5, 10, 3 = " + maximum);  // 10
    }
}
```

**Output:**
```
Maximum: 20
15 is Odd
Max of 5, 10, 3 = 10
```

---

## 5.8 Assignment Operators

Assignment operators are used to **assign values** to variables.

| Operator | Name | Description | Example | Equivalent |
|----------|------|-------------|---------|------------|
| `=` | Simple Assignment | Assigns right value to left variable | `a = 10` | — |
| `+=` | Addition Assignment | Adds and assigns | `a += 5` | `a = a + 5` |
| `-=` | Subtraction Assignment | Subtracts and assigns | `a -= 5` | `a = a - 5` |
| `*=` | Multiplication Assignment | Multiplies and assigns | `a *= 5` | `a = a * 5` |
| `/=` | Division Assignment | Divides and assigns | `a /= 5` | `a = a / 5` |
| `%=` | Modulus Assignment | Modulus and assigns | `a %= 3` | `a = a % 3` |
| `&=` | Bitwise AND Assignment | Bitwise AND and assigns | `a &= 3` | `a = a & 3` |
| `\|=` | Bitwise OR Assignment | Bitwise OR and assigns | `a \|= 3` | `a = a \| 3` |
| `^=` | Bitwise XOR Assignment | Bitwise XOR and assigns | `a ^= 3` | `a = a ^ 3` |
| `<<=` | Left Shift Assignment | Left shift and assigns | `a <<= 2` | `a = a << 2` |
| `>>=` | Right Shift Assignment | Right shift and assigns | `a >>= 2` | `a = a >> 2` |

```java
public class AssignmentOperatorDemo {
    public static void main(String[] args) {
        int a = 10;
        System.out.println("a = " + a);        // 10
        
        a += 5;
        System.out.println("a += 5: " + a);    // 15
        
        a -= 3;
        System.out.println("a -= 3: " + a);    // 12
        
        a *= 2;
        System.out.println("a *= 2: " + a);    // 24
        
        a /= 4;
        System.out.println("a /= 4: " + a);    // 6
        
        a %= 4;
        System.out.println("a %= 4: " + a);    // 2
    }
}
```

**Output:**
```
a = 10
a += 5: 15
a -= 3: 12
a *= 2: 24
a /= 4: 6
a %= 4: 2
```

---

## Operator Precedence (Order of Evaluation)

When multiple operators are used in one expression, Java follows this order (highest to lowest):

| Priority | Operators |
|----------|-----------|
| 1 (Highest) | `++`, `--` (Postfix) |
| 2 | `+`, `-`, `~`, `!` (Unary) |
| 3 | `*`, `/`, `%` |
| 4 | `+`, `-` (Addition/Subtraction) |
| 5 | `<<`, `>>`, `>>>` |
| 6 | `<`, `<=`, `>`, `>=` |
| 7 | `==`, `!=` |
| 8 | `&` |
| 9 | `^` |
| 10 | `\|` |
| 11 | `&&` |
| 12 | `\|\|` |
| 13 | `? :` (Ternary) |
| 14 (Lowest) | `=`, `+=`, `-=`, etc. |

---
---

# 6. Variables in Java

## Definition:
> A **variable** is a **named storage location** in memory that holds a value. The value can be changed during the program execution.

---

## Syntax for Declaring a Variable:
```
dataType variableName;                    // Declaration
dataType variableName = value;            // Declaration + Initialization
```

---

## Types of Variables:

### 6.1 Based on Location / Scope:

| Type | Where Declared | Scope | Example |
|------|----------------|-------|---------|
| **Local Variable** | Inside a method or block `{ }` | Only accessible within that method/block | `int x = 10;` inside a method |
| **Instance Variable** | Inside a class but outside any method | Accessible by all methods of the class (using object) | `int age;` inside a class |
| **Static Variable** | Inside a class with `static` keyword | Shared across all objects of the class | `static int count;` |

### 6.2 Based on Data Type:
- **Primitive Variables**: Store primitive values (`int`, `double`, `char`, `boolean`, etc.)
- **Reference Variables**: Store references to objects (`String`, `Array`, `Class`, etc.)

---

## Rules for Naming Variables:

1. Variable names can contain **letters, digits, underscores (_), and dollar signs ($)**.
2. Variable names **cannot start with a digit**.
3. Variable names **cannot be a reserved keyword** (like `int`, `class`, `public`, etc.).
4. Variable names are **case-sensitive** (`age` and `Age` are different).
5. Variable names should be **meaningful** (use camelCase convention).

### Valid Names:
```
myVariable, age, student_name, $salary, _count, firstName
```

### Invalid Names:
```
2name       → Starts with a digit
my-name     → Contains a hyphen
class       → Reserved keyword
my name     → Contains a space
```

---

## Variable Example Program:

```java
public class VariableDemo {
    // Instance Variable (declared inside class, outside method)
    int instanceVar = 50;
    
    // Static Variable (shared by all objects)
    static int staticVar = 100;
    
    public static void main(String[] args) {
        // Local Variable (declared inside method)
        int localVar = 10;
        String name = "Java";
        double pi = 3.14159;
        boolean isJavaFun = true;
        
        System.out.println("Local Variable: " + localVar);
        System.out.println("Name: " + name);
        System.out.println("Pi: " + pi);
        System.out.println("Is Java Fun? " + isJavaFun);
        System.out.println("Static Variable: " + staticVar);
        
        // Accessing instance variable using object
        VariableDemo obj = new VariableDemo();
        System.out.println("Instance Variable: " + obj.instanceVar);
    }
}
```

**Output:**
```
Local Variable: 10
Name: Java
Pi: 3.14159
Is Java Fun? true
Static Variable: 100
Instance Variable: 50
```

---

## Type Casting (Converting one type to another)

### Widening (Implicit) — Small to Large (Automatic):
```
byte → short → int → long → float → double
```

### Narrowing (Explicit) — Large to Small (Manual — needs casting):
```
double → float → long → int → short → byte
```

```java
public class TypeCastingDemo {
    public static void main(String[] args) {
        // Widening (Automatic)
        int i = 100;
        double d = i;   // int → double (automatic)
        System.out.println("Widening: " + d);   // 100.0
        
        // Narrowing (Manual - needs cast)
        double pi = 3.99;
        int truncated = (int) pi;   // double → int (manual)
        System.out.println("Narrowing: " + truncated);  // 3 (decimal part removed)
    }
}
```

**Output:**
```
Widening: 100.0
Narrowing: 3
```

---
---

# 7. Decision Making Statements

Decision making statements are used to execute a **specific block of code** based on a **condition**. If the condition is `true`, one block runs; if `false`, another block runs (or nothing runs).

---

## 7.1 If Statement

### a) Simple If Statement

**Definition:** Executes a block of code only if the condition is `true`.

**Syntax:**
```java
if (condition) {
    // This code runs only if condition is true
}
```

**Example:**
```java
public class SimpleIfDemo {
    public static void main(String[] args) {
        int age = 20;
        
        if (age >= 18) {
            System.out.println("You are an adult.");
        }
        
        System.out.println("Program ends.");
    }
}
```

**Output:**
```
You are an adult.
Program ends.
```

> **Explanation:** `age` is 20. The condition `age >= 18` is `true` (20 >= 18), so the message "You are an adult." is printed. Then the program continues to print "Program ends."

---

### b) If-Else Statement

**Definition:** If the condition is `true`, the `if` block runs. If the condition is `false`, the `else` block runs.

**Syntax:**
```java
if (condition) {
    // Runs if condition is true
} else {
    // Runs if condition is false
}
```

**Example:**
```java
public class IfElseDemo {
    public static void main(String[] args) {
        int number = -5;
        
        if (number > 0) {
            System.out.println("Number is Positive");
        } else {
            System.out.println("Number is NOT Positive");
        }
    }
}
```

**Output:**
```
Number is NOT Positive
```

> **Explanation:** `number` is -5. The condition `number > 0` is `false` (-5 is not greater than 0), so the `else` block runs and prints "Number is NOT Positive."

---

### c) Else-If (Else If) Statement

**Definition:** Used when there are **multiple conditions** to check. It checks conditions one by one from top to bottom, and executes the first block whose condition is `true`.

**Syntax:**
```java
if (condition1) {
    // Runs if condition1 is true
} else if (condition2) {
    // Runs if condition1 is false AND condition2 is true
} else if (condition3) {
    // Runs if condition1 and condition2 are false AND condition3 is true
} else {
    // Runs if ALL conditions are false
}
```

**Example:**
```java
public class ElseIfDemo {
    public static void main(String[] args) {
        int marks = 75;
        
        if (marks >= 90) {
            System.out.println("Grade: A");
        } else if (marks >= 80) {
            System.out.println("Grade: B");
        } else if (marks >= 70) {
            System.out.println("Grade: C");
        } else if (marks >= 60) {
            System.out.println("Grade: D");
        } else {
            System.out.println("Grade: F (Fail)");
        }
    }
}
```

**Output:**
```
Grade: C
```

> **Explanation:** `marks` is 75. Java checks each condition from top to bottom:
> - `marks >= 90` → 75 >= 90 → `false` → Skip
> - `marks >= 80` → 75 >= 80 → `false` → Skip
> - `marks >= 70` → 75 >= 70 → `true` → **Execute this block** → Prints "Grade: C"
> - Remaining conditions are not checked.

---

### d) Nested If Statement

**Definition:** An `if` statement placed **inside** another `if` statement. The inner `if` is checked only when the outer `if` condition is `true`.

**Syntax:**
```java
if (condition1) {
    // Outer if block
    if (condition2) {
        // Inner if block — runs only if BOTH condition1 AND condition2 are true
    }
}
```

**Example:**
```java
public class NestedIfDemo {
    public static void main(String[] args) {
        int age = 25;
        boolean hasLicense = true;
        
        if (age >= 18) {
            System.out.println("Age is 18 or above.");
            
            if (hasLicense) {
                System.out.println("You can drive a car.");
            } else {
                System.out.println("Please get a license first.");
            }
        } else {
            System.out.println("You are too young.");
        }
    }
}
```

**Output:**
```
Age is 18 or above.
You can drive a car.
```

> **Explanation:** First, `age >= 18` is checked → 25 >= 18 → `true`. So we enter the outer if block. Then `hasLicense` is checked → `true`. So "You can drive a car." is printed.

---

## 7.2 Switch Statement

**Definition:** The switch statement is used when you have **multiple choices** based on the value of a single variable. It is an alternative to a long if-else-if chain.

**Syntax:**
```java
switch (expression) {
    case value1:
        // Code for value1
        break;
    case value2:
        // Code for value2
        break;
    case value3:
        // Code for value3
        break;
    default:
        // Code if no case matches
        break;
}
```

### Important Notes:
- The `expression` can be of type `int`, `char`, `String`, or `enum`.
- **`break`** is used to stop execution after a case is matched. Without `break`, execution **falls through** to the next case.
- **`default`** is optional. It runs when no other case matches. It can be placed anywhere (not necessarily at the end).

**Example:**
```java
public class SwitchDemo {
    public static void main(String[] args) {
        int day = 3;
        
        switch (day) {
            case 1:
                System.out.println("Monday");
                break;
            case 2:
                System.out.println("Tuesday");
                break;
            case 3:
                System.out.println("Wednesday");
                break;
            case 4:
                System.out.println("Thursday");
                break;
            case 5:
                System.out.println("Friday");
                break;
            case 6:
                System.out.println("Saturday");
                break;
            case 7:
                System.out.println("Sunday");
                break;
            default:
                System.out.println("Invalid day number!");
                break;
        }
    }
}
```

**Output:**
```
Wednesday
```

### Fall-Through Example (What happens without break):
```java
public class SwitchFallThroughDemo {
    public static void main(String[] args) {
        int num = 2;
        
        switch (num) {
            case 1:
                System.out.println("One");
            case 2:
                System.out.println("Two");       // Matches here
            case 3:
                System.out.println("Three");     // Falls through (no break)
            case 4:
                System.out.println("Four");      // Falls through (no break)
            default:
                System.out.println("Default");   // Falls through (no break)
        }
    }
}
```

**Output:**
```
Two
Three
Four
Default
```

> **Explanation:** When `num = 2`, case 2 matches. But since there is no `break` after any case, execution **falls through** all subsequent cases until the end of the switch block.

---
---

# 8. Loop Statements

Loop statements are used to **repeat a block of code** multiple times until a condition becomes `false`.

---

## 8.1 While Loop

**Definition:** The while loop repeats a block of code **as long as the condition is true**. The condition is checked **before** each iteration.

**Syntax:**
```java
while (condition) {
    // Code to repeat
    // Update statement (to avoid infinite loop)
}
```

**When to use:** When you **don't know** how many times the loop should run in advance.

**Example:**
```java
public class WhileLoopDemo {
    public static void main(String[] args) {
        int i = 1;
        
        while (i <= 5) {
            System.out.println("Iteration: " + i);
            i++;   // Increment i by 1
        }
        
        System.out.println("Loop finished!");
    }
}
```

**Output:**
```
Iteration: 1
Iteration: 2
Iteration: 3
Iteration: 4
Iteration: 5
Loop finished!
```

> **Explanation:** `i` starts at 1. Each time, the condition `i <= 5` is checked. If true, the body prints the iteration number and increments `i`. When `i` becomes 6, `i <= 5` is `false`, and the loop stops.

---

## 8.2 Do-While Loop

**Definition:** The do-while loop executes the block of code **at least once**, and then repeats as long as the condition is true. The condition is checked **after** each iteration.

**Syntax:**
```java
do {
    // Code to repeat (runs at least once)
    // Update statement
} while (condition);
```

**Key Difference from While Loop:** The do-while loop runs the body **first**, then checks the condition. So even if the condition is `false` from the beginning, the body executes **once**.

**Example:**
```java
public class DoWhileLoopDemo {
    public static void main(String[] args) {
        int i = 1;
        
        do {
            System.out.println("Iteration: " + i);
            i++;
        } while (i <= 5);
        
        System.out.println("Loop finished!");
        
        // Example: condition is false from the start
        System.out.println("--- Do-While with false condition ---");
        int x = 10;
        do {
            System.out.println("x = " + x);  // This still prints ONCE
            x++;
        } while (x < 5);   // 10 < 5 is false, but body already ran once
    }
}
```

**Output:**
```
Iteration: 1
Iteration: 2
Iteration: 3
Iteration: 4
Iteration: 5
Loop finished!
--- Do-While with false condition ---
x = 10
```

---

## 8.3 For Loop

**Definition:** The for loop is used when you **know in advance** how many times the loop should run. It is the most commonly used loop in Java.

**Syntax:**
```java
for (initialization; condition; update) {
    // Code to repeat
}
```

### Parts of the For Loop:
1. **Initialization**: Declares and initializes the loop variable (runs **once** at the start).
2. **Condition**: Checked **before each iteration**. If `true`, the loop body runs. If `false`, the loop stops.
3. **Update**: Updates the loop variable **after each iteration** (usually increment or decrement).

**Example:**
```java
public class ForLoopDemo {
    public static void main(String[] args) {
        // Print numbers 1 to 5
        for (int i = 1; i <= 5; i++) {
            System.out.println("Number: " + i);
        }
        
        // Print numbers in reverse (5 to 1)
        System.out.println("--- Reverse ---");
        for (int i = 5; i >= 1; i--) {
            System.out.println("Number: " + i);
        }
        
        // Multiplication table of 3
        System.out.println("--- Multiplication Table of 3 ---");
        for (int i = 1; i <= 5; i++) {
            System.out.println("3 x " + i + " = " + (3 * i));
        }
    }
}
```

**Output:**
```
Number: 1
Number: 2
Number: 3
Number: 4
Number: 5
--- Reverse ---
Number: 5
Number: 4
Number: 3
Number: 2
Number: 1
--- Multiplication Table of 3 ---
3 x 1 = 3
3 x 2 = 6
3 x 3 = 9
3 x 4 = 12
3 x 5 = 15
```

---

## 8.4 For-Each Loop (Enhanced For Loop)

**Definition:** The for-each loop is used to **iterate over elements** in an array or collection (like ArrayList). It is simpler than the regular for loop when you just need to access each element.

**Syntax:**
```java
for (dataType variable : arrayOrCollection) {
    // Use 'variable' — it holds each element one by one
}
```

**Example:**
```java
public class ForEachLoopDemo {
    public static void main(String[] args) {
        // Array of fruits
        String[] fruits = {"Apple", "Banana", "Cherry", "Mango", "Grape"};
        
        System.out.println("All Fruits:");
        for (String fruit : fruits) {
            System.out.println("  - " + fruit);
        }
        
        // Array of numbers — calculate sum
        int[] numbers = {10, 20, 30, 40, 50};
        int sum = 0;
        
        for (int num : numbers) {
            sum += num;
        }
        System.out.println("Sum of numbers: " + sum);
    }
}
```

**Output:**
```
All Fruits:
  - Apple
  - Banana
  - Cherry
  - Mango
  - Grape
Sum of numbers: 150
```

---

## 8.5 Nested Loops

**Definition:** A loop placed **inside** another loop. The **inner loop** completes all its iterations for **each iteration** of the outer loop.

**Example: Print a multiplication table (1 to 5):**
```java
public class NestedLoopDemo {
    public static void main(String[] args) {
        // Multiplication table
        for (int i = 1; i <= 5; i++) {           // Outer loop (rows)
            for (int j = 1; j <= 5; j++) {       // Inner loop (columns)
                System.out.print(i * j + "\t");  // \t = tab for alignment
            }
            System.out.println();                // New line after each row
        }
    }
}
```

**Output:**
```
1	2	3	4	5	
2	4	6	8	10	
3	6	9	12	15	
4	8	12	16	20	
5	10	15	20	25	
```

**Pattern Example (Star Triangle):**
```java
public class StarPattern {
    public static void main(String[] args) {
        int rows = 5;
        
        for (int i = 1; i <= rows; i++) {
            for (int j = 1; j <= i; j++) {
                System.out.print("* ");
            }
            System.out.println();
        }
    }
}
```

**Output:**
```
* 
* * 
* * * 
* * * * 
* * * * * 
```

---

## Comparison of Loops

| Feature | While Loop | Do-While Loop | For Loop | For-Each Loop |
|---------|-----------|---------------|----------|---------------|
| **Condition checked** | Before loop | After loop | Before loop | Automatically |
| **Minimum iterations** | 0 | 1 | 0 | Depends on array size |
| **Best when** | Iterations unknown | At least one run guaranteed | Iterations known | Iterating arrays/collections |
| **Loop variable** | Declared outside | Declared outside | Declared inside | Declared in loop |

---
---

# 9. Jump Statements

Jump statements are used to **change the flow** of a loop (skip iterations or exit the loop early).

---

## 9.1 Break Statement

**Definition:** The `break` statement **exits** the loop immediately. No more iterations are executed after `break`.

**Syntax:**
```java
break;
```

**Example:**
```java
public class BreakDemo {
    public static void main(String[] args) {
        // Break in a for loop
        System.out.println("--- Break in For Loop ---");
        for (int i = 1; i <= 10; i++) {
            if (i == 5) {
                break;   // Exit the loop when i is 5
            }
            System.out.println("i = " + i);
        }
        System.out.println("Loop ended!");
        
        // Break in a while loop
        System.out.println("--- Break in While Loop ---");
        int num = 0;
        while (true) {   // Infinite loop
            num++;
            if (num > 3) {
                break;   // Exit when num exceeds 3
            }
            System.out.println("num = " + num);
        }
        System.out.println("While loop ended!");
    }
}
```

**Output:**
```
--- Break in For Loop ---
i = 1
i = 2
i = 3
i = 4
Loop ended!
--- Break in While Loop ---
num = 1
num = 2
num = 3
While loop ended!
```

> **Explanation:** In the for loop, when `i` becomes 5, the `break` statement is executed, which **immediately exits** the loop. So only 1, 2, 3, 4 are printed. In the while loop, `break` stops the infinite loop when `num` exceeds 3.

---

### Labeled Break:

When you have **nested loops**, `break` only exits the **innermost loop**. To exit an outer loop, you use a **label**.

```java
public class LabeledBreakDemo {
    public static void main(String[] args) {
        outer:   // Label for the outer loop
        for (int i = 1; i <= 3; i++) {
            for (int j = 1; j <= 3; j++) {
                if (i == 2 && j == 2) {
                    break outer;   // Exits the OUTER loop
                }
                System.out.println("i=" + i + ", j=" + j);
            }
        }
        System.out.println("Done!");
    }
}
```

**Output:**
```
i=1, j=1
i=1, j=2
i=1, j=3
i=2, j=1
Done!
```

---

## 9.2 Continue Statement

**Definition:** The `continue` statement **skips the current iteration** and moves to the **next iteration** of the loop. The loop does not end — it just skips one iteration.

**Syntax:**
```java
continue;
```

**Example:**
```java
public class ContinueDemo {
    public static void main(String[] args) {
        // Skip even numbers, print only odd numbers
        System.out.println("--- Odd Numbers from 1 to 10 ---");
        for (int i = 1; i <= 10; i++) {
            if (i % 2 == 0) {
                continue;   // Skip even numbers
            }
            System.out.println(i);
        }
        
        // Skip number 5
        System.out.println("--- Numbers 1 to 7, skipping 5 ---");
        int i = 0;
        while (i < 7) {
            i++;
            if (i == 5) {
                continue;   // Skip 5
            }
            System.out.println(i);
        }
    }
}
```

**Output:**
```
--- Odd Numbers from 1 to 10 ---
1
3
5
7
9
--- Numbers 1 to 7, skipping 5 ---
1
2
3
4
6
7
```

---

### Labeled Continue:

Like labeled break, you can use a label with `continue` to skip to the next iteration of an **outer loop**.

```java
public class LabeledContinueDemo {
    public static void main(String[] args) {
        outer:
        for (int i = 1; i <= 3; i++) {
            for (int j = 1; j <= 3; j++) {
                if (j == 2) {
                    continue outer;   // Skip to next iteration of OUTER loop
                }
                System.out.println("i=" + i + ", j=" + j);
            }
        }
    }
}
```

**Output:**
```
i=1, j=1
i=2, j=1
i=3, j=1
```

> **Explanation:** Whenever `j` becomes 2, the `continue outer` skips the rest of the inner loop and moves to the next value of `i`. So only `j=1` is printed for each `i`.

---

## Difference: Break vs Continue

| Feature | Break | Continue |
|---------|-------|----------|
| **What it does** | **Exits** the loop completely | **Skips** the current iteration |
| **Remaining iterations** | None — loop ends | Remaining iterations still run |
| **Usage** | When you want to **stop** the loop | When you want to **skip** certain iterations |

---
---

# 10. Strings and String Methods

## Definition:
> A **String** in Java is a **sequence of characters**. It is an **object** of the `String` class (located in `java.lang` package).

---

## How to Create a String:

### Method 1: String Literal (Using double quotes)
```java
String str1 = "Hello World";
```

### Method 2: Using `new` keyword
```java
String str2 = new String("Hello World");
```

---

## Strings are IMMUTABLE

> **Immutable** means that once a String is created, its value **cannot be changed**. If you try to change it, Java creates a **new String object** instead of modifying the existing one.

```java
public class ImmutableStringDemo {
    public static void main(String[] args) {
        String str = "Hello";
        str = str + " World";   // A NEW string "Hello World" is created
        // The original "Hello" still exists in memory but str now points to "Hello World"
        System.out.println(str);   // Hello World
    }
}
```

> **Why Immutable?** Strings are immutable in Java for **security, thread-safety, and performance** reasons. Since String objects cannot be changed, they can be safely shared between multiple threads.

---

## String Methods — Complete Reference:

---

### 1. `length()`
**Definition:** Returns the **number of characters** in the string.

**Syntax:** `string.length()`

```java
String str = "Hello";
System.out.println(str.length());   // Output: 5
```

---

### 2. `charAt(int index)`
**Definition:** Returns the character at the specified **index**. Index starts at **0**.

**Syntax:** `string.charAt(index)`

```java
String str = "Hello";
System.out.println(str.charAt(0));   // Output: H
System.out.println(str.charAt(4));   // Output: o
```

> **Note:** If index is out of range (negative or >= length), it throws `StringIndexOutOfBoundsException`.

---

### 3. `substring(int beginIndex)` and `substring(int beginIndex, int endIndex)`
**Definition:** Returns a **part (substring)** of the string.
- `substring(beginIndex)` — returns from `beginIndex` to the **end**.
- `substring(beginIndex, endIndex)` — returns from `beginIndex` to `endIndex - 1` (endIndex is **exclusive**).

```java
String str = "Hello World";
System.out.println(str.substring(6));      // Output: World
System.out.println(str.substring(0, 5));   // Output: Hello
```

---

### 4. `indexOf(String str)` and `indexOf(String str, int fromIndex)`
**Definition:** Returns the **index of the first occurrence** of the specified string. Returns **-1** if not found.

```java
String str = "Hello World Hello";
System.out.println(str.indexOf("Hello"));       // Output: 0
System.out.println(str.indexOf("World"));       // Output: 6
System.out.println(str.indexOf("Hello", 1));    // Output: 12 (starts searching from index 1)
System.out.println(str.indexOf("Java"));        // Output: -1 (not found)
```

---

### 5. `lastIndexOf(String str)`
**Definition:** Returns the **index of the last occurrence** of the specified string. Returns **-1** if not found.

```java
String str = "Hello World Hello";
System.out.println(str.lastIndexOf("Hello"));   // Output: 12
System.out.println(str.lastIndexOf("World"));   // Output: 6
```

---

### 6. `contains(CharSequence s)`
**Definition:** Returns `true` if the string **contains** the specified sequence of characters.

```java
String str = "Hello World";
System.out.println(str.contains("World"));   // Output: true
System.out.println(str.contains("Java"));    // Output: false
```

---

### 7. `startsWith(String prefix)`
**Definition:** Returns `true` if the string **starts with** the specified prefix.

```java
String str = "Hello World";
System.out.println(str.startsWith("Hello"));   // Output: true
System.out.println(str.startsWith("World"));   // Output: false
```

---

### 8. `endsWith(String suffix)`
**Definition:** Returns `true` if the string **ends with** the specified suffix.

```java
String str = "Hello World";
System.out.println(str.endsWith("World"));   // Output: true
System.out.println(str.endsWith("Hello"));   // Output: false
```

---

### 9. `equals(Object obj)`
**Definition:** Returns `true` if the string is **exactly equal** to the given object (case-sensitive).

> **Important:** Always use `.equals()` to compare strings, **never use `==`**. The `==` operator compares **references (memory addresses)**, not the actual content.

```java
String str1 = "Hello";
String str2 = "Hello";
String str3 = "hello";

System.out.println(str1.equals(str2));   // Output: true
System.out.println(str1.equals(str3));   // Output: false (different case)
```

---

### 10. `equalsIgnoreCase(String str)`
**Definition:** Returns `true` if the string is equal to the given string, **ignoring case** (upper or lower).

```java
String str1 = "Hello";
String str2 = "hello";
String str3 = "HELLO";

System.out.println(str1.equalsIgnoreCase(str2));   // Output: true
System.out.println(str1.equalsIgnoreCase(str3));   // Output: true
```

---

### 11. `compareTo(String str)`
**Definition:** Compares two strings **lexicographically** (alphabetically based on Unicode values).
- Returns **0** if strings are equal.
- Returns a **negative value** if this string comes **before** the argument.
- Returns a **positive value** if this string comes **after** the argument.

```java
String str1 = "Apple";
String str2 = "Banana";
String str3 = "Apple";

System.out.println(str1.compareTo(str2));   // Output: -1 (Apple comes before Banana)
System.out.println(str2.compareTo(str1));   // Output: 1  (Banana comes after Apple)
System.out.println(str1.compareTo(str3));   // Output: 0  (Equal)
```

---

### 12. `replace(char oldChar, char newChar)`
**Definition:** Replaces **all occurrences** of `oldChar` with `newChar`.

```java
String str = "Hello World";
System.out.println(str.replace('o', '0'));   // Output: Hell0 W0rld
System.out.println(str.replace('l', 'L'));   // Output: HeLLo WorLd
```

---

### 13. `replaceAll(String regex, String replacement)`
**Definition:** Replaces **all occurrences** that match the given **regular expression** with the replacement string.

```java
String str = "Hello 123 World 456";
System.out.println(str.replaceAll("[0-9]+", "NUM"));   // Output: Hello NUM World NUM
System.out.println(str.replaceAll("\\s+", "_"));       // Output: Hello_123_World_456
```

---

### 14. `toUpperCase()`
**Definition:** Returns the string converted to **uppercase** letters.

```java
String str = "Hello World";
System.out.println(str.toUpperCase());   // Output: HELLO WORLD
```

---

### 15. `toLowerCase()`
**Definition:** Returns the string converted to **lowercase** letters.

```java
String str = "Hello World";
System.out.println(str.toLowerCase());   // Output: hello world
```

---

### 16. `trim()`
**Definition:** Removes **leading (front) and trailing (end) whitespace** from the string. Does NOT remove spaces in the middle.

```java
String str = "   Hello World   ";
System.out.println("'" + str.trim() + "'");   // Output: 'Hello World'
```

---

### 17. `isEmpty()`
**Definition:** Returns `true` if the string has **zero length** (is empty: `""`).

```java
String str1 = "";
String str2 = "Hello";
String str3 = "   ";

System.out.println(str1.isEmpty());   // Output: true
System.out.println(str2.isEmpty());   // Output: false
System.out.println(str3.isEmpty());   // Output: false (spaces are characters)
```

---

### 18. `isBlank()`
**Definition:** Returns `true` if the string is **empty or contains only whitespace** characters. (Available since Java 11)

```java
String str1 = "";
String str2 = "   ";
String str3 = "Hello";

System.out.println(str1.isBlank());   // Output: true
System.out.println(str2.isBlank());   // Output: true  (only whitespace)
System.out.println(str3.isBlank());   // Output: false
```

> **Difference: isEmpty() vs isBlank():**
> - `isEmpty()` → true only for `""`
> - `isBlank()` → true for `""` AND `"   "` (whitespace only)

---

### 19. `concat(String str)`
**Definition:** Joins (concatenates) the given string to the **end** of this string and returns a new string.

```java
String str1 = "Hello";
String str2 = " World";
System.out.println(str1.concat(str2));   // Output: Hello World
```

> **Note:** You can also use the `+` operator to concatenate: `str1 + str2`

---

### 20. `join(CharSequence delimiter, CharSequence... elements)`
**Definition:** Joins multiple strings together with a **delimiter** (separator) between them. It is a **static method**.

```java
String result = String.join(", ", "Apple", "Banana", "Cherry");
System.out.println(result);   // Output: Apple, Banana, Cherry

String result2 = String.join("-", "2024", "01", "15");
System.out.println(result2);  // Output: 2024-01-15
```

---

## Complete String Methods Example Program:

```java
public class StringMethodsDemo {
    public static void main(String[] args) {
        String str = "Hello World";
        
        System.out.println("Original String: " + str);
        System.out.println("Length: " + str.length());
        System.out.println("charAt(0): " + str.charAt(0));
        System.out.println("substring(6): " + str.substring(6));
        System.out.println("substring(0,5): " + str.substring(0, 5));
        System.out.println("indexOf('World'): " + str.indexOf("World"));
        System.out.println("lastIndexOf('l'): " + str.lastIndexOf("l"));
        System.out.println("contains('World'): " + str.contains("World"));
        System.out.println("startsWith('Hello'): " + str.startsWith("Hello"));
        System.out.println("endsWith('World'): " + str.endsWith("World"));
        System.out.println("toUpperCase: " + str.toUpperCase());
        System.out.println("toLowerCase: " + str.toLowerCase());
        System.out.println("replace('o','0'): " + str.replace('o', '0'));
        System.out.println("trim: '" + "  Hi  ".trim() + "'");
        System.out.println("isEmpty: " + str.isEmpty());
        System.out.println("isBlank: " + "   ".isBlank());
        System.out.println("concat: " + "Hello".concat(" Java"));
        System.out.println("join: " + String.join(", ", "A", "B", "C"));
        System.out.println("equals: " + str.equals("Hello World"));
        System.out.println("equalsIgnoreCase: " + str.equalsIgnoreCase("hello world"));
        System.out.println("compareTo: " + "Apple".compareTo("Banana"));
    }
}
```

**Output:**
```
Original String: Hello World
Length: 11
charAt(0): H
substring(6): World
substring(0,5): Hello
indexOf('World'): 6
lastIndexOf('l'): 9
contains('World'): true
startsWith('Hello'): true
endsWith('World'): true
toUpperCase: HELLO WORLD
toLowerCase: hello world
replace('o','0'): Hell0 W0rld
trim: 'Hi'
isEmpty: false
isBlank: true
concat: Hello Java
join: A, B, C
equals: true
equalsIgnoreCase: true
compareTo: -1
```

---
---

# 11. Methods in Java

## Definition:
> A **method** is a **block of code** that performs a specific task. Methods can be called (invoked) multiple times, which makes code **reusable** and **organized**.

---

## Structure of a Method:

```java
returnType methodName(parameterType parameterName, ...) {
    // Method body — the code that runs
    return value;   // Only if returnType is NOT void
}
```

### Parts Explained:
| Part | Description | Example |
|------|-------------|---------|
| **Return Type** | The data type of the value the method returns. Use `void` if it returns nothing. | `int`, `String`, `void` |
| **Method Name** | The name of the method (follows camelCase). | `add`, `printMessage` |
| **Parameters** | Input values passed to the method (optional). | `int a, int b` |
| **Method Body** | The code inside `{ }` that performs the task. | Calculations, print statements, etc. |
| **Return Statement** | Returns a value from the method (not needed for `void` methods). | `return sum;` |

---

## 11.1 Parametric vs Non-Parametric Methods

### Non-Parametric Method (No Parameters):
A method that takes **no input** (no parameters).

```java
public class NonParametricDemo {
    // Non-parametric method — no parameters
    public static void greet() {
        System.out.println("Hello! Welcome to Java.");
    }
    
    public static void main(String[] args) {
        greet();   // Calling the method
    }
}
```

**Output:**
```
Hello! Welcome to Java.
```

---

### Parametric Method (With Parameters):
A method that takes **one or more inputs** (parameters).

```java
public class ParametricDemo {
    // Parametric method — takes two int parameters
    public static int add(int a, int b) {
        int sum = a + b;
        return sum;   // Returns the result
    }
    
    public static void main(String[] args) {
        int result = add(10, 20);   // Passing arguments
        System.out.println("Sum: " + result);
    }
}
```

**Output:**
```
Sum: 30
```

> **Important Terminology:**
> - **Parameters** = variables declared in the method definition: `int a, int b`
> - **Arguments** = actual values passed when calling the method: `10, 20`

---

## 11.2 Static vs Non-Static Methods

### Static Method:
- Declared with the `static` keyword.
- Can be called **without creating an object**.
- Called using: `ClassName.methodName()` or directly if in the same class.
- Does **not** have access to instance variables (non-static variables).

### Non-Static Method:
- Declared **without** the `static` keyword.
- **Must create an object** to call it.
- Called using: `objectName.methodName()`
- Has access to **instance variables** of the object.

```java
public class StaticVsNonStaticDemo {
    int instanceVariable = 100;   // Instance (non-static) variable
    
    // Static Method
    public static void staticMethod() {
        System.out.println("This is a STATIC method.");
        System.out.println("I can be called without an object.");
    }
    
    // Non-Static Method
    public void nonStaticMethod() {
        System.out.println("This is a NON-STATIC method.");
        System.out.println("Instance variable value: " + instanceVariable);
    }
    
    public static void main(String[] args) {
        // Calling static method — no object needed
        staticMethod();
        
        // Calling non-static method — need an object
        StaticVsNonStaticDemo obj = new StaticVsNonStaticDemo();
        obj.nonStaticMethod();
    }
}
```

**Output:**
```
This is a STATIC method.
I can be called without an object.
This is a NON-STATIC method.
Instance variable value: 100
```

---

## 11.3 Void Method vs Non-Void Method

### Void Method:
- Return type is `void`.
- Does **NOT return any value**.
- Used to perform an action (like printing).

### Non-Void Method:
- Has a return type other than `void` (like `int`, `String`, `double`, etc.).
- **Must return a value** using the `return` keyword.

```java
public class VoidVsNonVoidDemo {
    // Void method — returns nothing
    public static void printGreeting(String name) {
        System.out.println("Hello, " + name + "!");
        // No return statement needed
    }
    
    // Non-void method — returns an int
    public static int multiply(int a, int b) {
        return a * b;   // Must return a value
    }
    
    // Non-void method — returns a String
    public static String getGreeting(String name) {
        return "Hello, " + name + "!";
    }
    
    public static void main(String[] args) {
        // Calling void method
        printGreeting("Java");
        
        // Calling non-void methods
        int product = multiply(5, 6);
        System.out.println("5 x 6 = " + product);
        
        String greeting = getGreeting("World");
        System.out.println(greeting);
    }
}
```

**Output:**
```
Hello, Java!
5 x 6 = 30
Hello, World!
```

---

## 11.4 Method Overloading

**Definition:** Method overloading is when you have **two or more methods** with the **same name** but **different parameters** (different number of parameters, or different types).

> Java decides which method to call based on the **arguments** passed at the time of calling.

### Rules for Overloading:
1. Method names must be the **same**.
2. Parameters must be **different** (number, type, or order).
3. Return type can be same or different — it does **NOT** matter for overloading.

```java
public class MethodOverloadingDemo {
    // Method 1: Two int parameters
    public static int add(int a, int b) {
        System.out.println("add(int, int) called");
        return a + b;
    }
    
    // Method 2: Three int parameters (overloaded)
    public static int add(int a, int b, int c) {
        System.out.println("add(int, int, int) called");
        return a + b + c;
    }
    
    // Method 3: Two double parameters (overloaded)
    public static double add(double a, double b) {
        System.out.println("add(double, double) called");
        return a + b;
    }
    
    // Method 4: One String parameter (overloaded — different type)
    public static void add(String message) {
        System.out.println("add(String) called");
        System.out.println("Message: " + message);
    }
    
    public static void main(String[] args) {
        System.out.println("Result: " + add(10, 20));
        System.out.println("Result: " + add(10, 20, 30));
        System.out.println("Result: " + add(3.5, 2.5));
        add("Hello Overloading!");
    }
}
```

**Output:**
```
add(int, int) called
Result: 30
add(int, int, int) called
Result: 60
add(double, double) called
Result: 6.0
add(String) called
Message: Hello Overloading!
```

---

## 11.5 Calling Methods

### Ways to Call a Method:

1. **Direct call** (for static methods in the same class):
   ```java
   greet();
   ```

2. **Using class name** (for static methods in other classes):
   ```java
   MathUtils.add(10, 20);
   ```

3. **Using an object** (for non-static methods):
   ```java
   MyClass obj = new MyClass();
   obj.myMethod();
   ```

4. **Storing return value**:
   ```java
   int result = add(5, 10);
   ```

5. **Directly in expressions**:
   ```java
   System.out.println("Sum = " + add(5, 10));
   ```

---

## Complete Methods Example:

```java
public class MethodsCompleteDemo {
    // 1. Non-parametric void method
    public static void sayHello() {
        System.out.println("Hello from sayHello()!");
    }
    
    // 2. Parametric void method
    public static void printName(String name) {
        System.out.println("Name: " + name);
    }
    
    // 3. Parametric non-void method (returns int)
    public static int square(int number) {
        return number * number;
    }
    
    // 4. Method that returns boolean
    public static boolean isEven(int number) {
        return number % 2 == 0;
    }
    
    // 5. Overloaded methods
    public static double calculate(double a, double b) {
        return a + b;
    }
    
    public static double calculate(double a, double b, double c) {
        return a + b + c;
    }
    
    public static void main(String[] args) {
        sayHello();
        printName("Alice");
        
        int sq = square(7);
        System.out.println("Square of 7: " + sq);
        
        System.out.println("Is 10 even? " + isEven(10));
        System.out.println("Is 7 even? " + isEven(7));
        
        System.out.println("calculate(1.5, 2.5) = " + calculate(1.5, 2.5));
        System.out.println("calculate(1.5, 2.5, 3.0) = " + calculate(1.5, 2.5, 3.0));
    }
}
```

**Output:**
```
Hello from sayHello()!
Name: Alice
Square of 7: 49
Is 10 even? true
Is 7 even? false
calculate(1.5, 2.5) = 4.0
calculate(1.5, 2.5, 3.0) = 7.0
```

---
---

# 12. Arrays in Java

## Definition:
> An **array** is a collection of **fixed-size elements** of the **same data type**, stored in **contiguous (adjacent) memory locations**. Arrays are used to store multiple values in a single variable.

---

## Why Use Arrays?
- Instead of creating multiple variables (`int a1, a2, a3, ... a100`), you can use a **single array**: `int[] arr = new int[100];`
- Arrays make it easy to **store, access, and manipulate** a group of related values.

---

## Key Concepts:
- **Index**: Each element in an array has an index starting from **0**.
- **Size**: The number of elements in the array (fixed once created).
- **Element**: Each individual value stored in the array.

```
Index:    0     1     2     3     4
        ┌─────┬─────┬─────┬─────┬─────┐
Array:  │ 10  │ 20  │ 30  │ 40  │ 50  │
        └─────┴─────┴─────┴─────┴─────┘
```

---

## 12.1 One-Dimensional (1D) Array

### Ways to Declare and Initialize a 1D Array:

#### Method 1: Declaration + Size (Default Values)
```java
int[] arr = new int[5];   // Creates array of size 5 with default values (0)
```

#### Method 2: Declaration + Initialization (Direct Values)
```java
int[] arr = {10, 20, 30, 40, 50};
```

#### Method 3: Using `new` with values
```java
int[] arr = new int[]{10, 20, 30, 40, 50};
```

#### Method 4: Declaration first, then initialization
```java
int[] arr;
arr = new int[]{10, 20, 30, 40, 50};
```

---

### Accessing Array Elements:
```java
arr[0]   // First element
arr[1]   // Second element
arr[arr.length - 1]   // Last element
```

### Array Length:
```java
arr.length   // Returns the number of elements in the array
```

> **Note:** `length` is a **property** (not a method) in arrays, so there are **no parentheses**: `arr.length` (correct), NOT `arr.length()` (wrong).

---

### 1D Array Example Program:

```java
public class OneDimensionalArrayDemo {
    public static void main(String[] args) {
        // Method 1: Array with default values
        int[] arr1 = new int[5];
        System.out.println("--- Array with default values ---");
        for (int i = 0; i < arr1.length; i++) {
            System.out.println("arr1[" + i + "] = " + arr1[i]);   // All 0
        }
        
        // Method 2: Array with initial values
        int[] arr2 = {10, 20, 30, 40, 50};
        System.out.println("\n--- Array with initial values ---");
        for (int i = 0; i < arr2.length; i++) {
            System.out.println("arr2[" + i + "] = " + arr2[i]);
        }
        
        // Using for-each loop
        System.out.println("\n--- Using for-each loop ---");
        String[] fruits = {"Apple", "Banana", "Cherry", "Mango"};
        for (String fruit : fruits) {
            System.out.println("Fruit: " + fruit);
        }
        
        // Array length
        System.out.println("\nLength of fruits array: " + fruits.length);
        
        // Modifying array elements
        arr2[2] = 99;
        System.out.println("\nAfter arr2[2] = 99:");
        System.out.println("arr2[2] = " + arr2[2]);
        
        // Sum of array elements
        int sum = 0;
        for (int num : arr2) {
            sum += num;
        }
        System.out.println("\nSum of arr2: " + sum);
    }
}
```

**Output:**
```
--- Array with default values ---
arr1[0] = 0
arr1[1] = 0
arr1[2] = 0
arr1[3] = 0
arr1[4] = 0

--- Array with initial values ---
arr2[0] = 10
arr2[1] = 20
arr2[2] = 30
arr2[3] = 40
arr2[4] = 50

--- Using for-each loop ---
Fruit: Apple
Fruit: Banana
Fruit: Cherry
Fruit: Mango

Length of fruits array: 4

After arr2[2] = 99:
arr2[2] = 99

Sum of arr2: 199
```

---

### Default Values in Arrays:

| Data Type | Default Value |
|-----------|---------------|
| int, short, byte, long | 0 |
| float, double | 0.0 |
| boolean | false |
| char | '\u0000' (null character) |
| String / Object | null |

---

### Common 1D Array Operations:

#### 1. Finding the Maximum Element:
```java
public class FindMax {
    public static void main(String[] args) {
        int[] arr = {34, 78, 12, 56, 90, 23, 45};
        
        int max = arr[0];   // Assume first element is max
        for (int i = 1; i < arr.length; i++) {
            if (arr[i] > max) {
                max = arr[i];
            }
        }
        System.out.println("Maximum element: " + max);   // 90
    }
}
```

#### 2. Finding the Minimum Element:
```java
public class FindMin {
    public static void main(String[] args) {
        int[] arr = {34, 78, 12, 56, 90, 23, 45};
        
        int min = arr[0];
        for (int i = 1; i < arr.length; i++) {
            if (arr[i] < min) {
                min = arr[i];
            }
        }
        System.out.println("Minimum element: " + min);   // 12
    }
}
```

#### 3. Calculating the Average:
```java
public class FindAverage {
    public static void main(String[] args) {
        int[] arr = {10, 20, 30, 40, 50};
        
        int sum = 0;
        for (int num : arr) {
            sum += num;
        }
        double average = (double) sum / arr.length;
        System.out.println("Average: " + average);   // 30.0
    }
}
```

#### 4. Reversing an Array:
```java
public class ReverseArray {
    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5};
        
        System.out.print("Original: ");
        for (int num : arr) System.out.print(num + " ");
        
        // Reverse using two pointers
        int left = 0;
        int right = arr.length - 1;
        while (left < right) {
            int temp = arr[left];
            arr[left] = arr[right];
            arr[right] = temp;
            left++;
            right--;
        }
        
        System.out.print("\nReversed: ");
        for (int num : arr) System.out.print(num + " ");
        System.out.println();
    }
}
```

**Output:**
```
Original: 1 2 3 4 5 
Reversed: 5 4 3 2 1 
```

#### 5. Searching an Element (Linear Search):
```java
public class LinearSearch {
    public static void main(String[] args) {
        int[] arr = {10, 25, 33, 47, 55, 68, 72};
        int target = 47;
        
        boolean found = false;
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == target) {
                System.out.println("Element " + target + " found at index " + i);
                found = true;
                break;
            }
        }
        
        if (!found) {
            System.out.println("Element not found!");
        }
    }
}
```

**Output:**
```
Element 47 found at index 3
```

#### 6. Sorting an Array (Bubble Sort):
```java
public class BubbleSort {
    public static void main(String[] args) {
        int[] arr = {64, 34, 25, 12, 22, 11, 90};
        
        // Bubble Sort Algorithm
        for (int i = 0; i < arr.length - 1; i++) {
            for (int j = 0; j < arr.length - i - 1; j++) {
                if (arr[j] > arr[j + 1]) {
                    // Swap
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                }
            }
        }
        
        System.out.print("Sorted Array: ");
        for (int num : arr) {
            System.out.print(num + " ");
        }
        System.out.println();
    }
}
```

**Output:**
```
Sorted Array: 11 12 22 25 34 64 90 
```

---

### Using java.util.Arrays Class (Built-in Array Methods):

The `java.util.Arrays` class provides **utility methods** for working with arrays.

```java
import java.util.Arrays;

public class ArraysClassDemo {
    public static void main(String[] args) {
        int[] arr = {5, 2, 8, 1, 9, 3};
        
        // 1. Print array
        System.out.println("Original: " + Arrays.toString(arr));
        
        // 2. Sort array
        Arrays.sort(arr);
        System.out.println("Sorted: " + Arrays.toString(arr));
        
        // 3. Binary Search (array must be sorted first)
        int index = Arrays.binarySearch(arr, 8);
        System.out.println("Index of 8: " + index);
        
        // 4. Fill array with a value
        int[] filled = new int[5];
        Arrays.fill(filled, 7);
        System.out.println("Filled: " + Arrays.toString(filled));
        
        // 5. Copy of array
        int[] copy = Arrays.copyOf(arr, arr.length);
        System.out.println("Copy: " + Arrays.toString(copy));
        
        // 6. Copy of range
        int[] rangeCopy = Arrays.copyOfRange(arr, 1, 4);
        System.out.println("Range Copy (1 to 4): " + Arrays.toString(rangeCopy));
        
        // 7. Compare two arrays
        int[] arr2 = {1, 2, 3, 5, 8, 9};
        System.out.println("Arrays equal? " + Arrays.equals(arr, arr2));
    }
}
```

**Output:**
```
Original: [5, 2, 8, 1, 9, 3]
Sorted: [1, 2, 3, 5, 8, 9]
Index of 8: 4
Filled: [7, 7, 7, 7, 7]
Copy: [1, 2, 3, 5, 8, 9]
Range Copy (1 to 4): [2, 3, 5]
Arrays equal? true
```

### Summary of java.util.Arrays Methods:

| Method | Description |
|--------|-------------|
| `Arrays.toString(arr)` | Returns a string representation of the array |
| `Arrays.sort(arr)` | Sorts the array in ascending order |
| `Arrays.binarySearch(arr, key)` | Searches for key in a sorted array, returns index |
| `Arrays.fill(arr, value)` | Fills all elements with the given value |
| `Arrays.copyOf(arr, length)` | Creates a copy of the array with specified length |
| `Arrays.copyOfRange(arr, from, to)` | Copies a range of elements from the array |
| `Arrays.equals(arr1, arr2)` | Returns true if two arrays have the same elements |
| `Arrays.deepToString(arr2d)` | Returns string representation of a 2D array |
| `Arrays.deepEquals(arr1, arr2)` | Compares two 2D arrays |

---

## 12.2 Two-Dimensional (2D) Array

### Definition:
> A **2D array** is an **array of arrays**. It is like a **table or matrix** with **rows and columns**.

### Visualization:
```
         Column 0   Column 1   Column 2
Row 0   [   1    ,    2    ,    3    ]
Row 1   [   4    ,    5    ,    6    ]
Row 2   [   7    ,    8    ,    9    ]
```

### Syntax to Declare and Initialize:

#### Method 1: Using size
```java
int[][] matrix = new int[3][3];   // 3 rows and 3 columns
```

#### Method 2: Direct initialization
```java
int[][] matrix = {
    {1, 2, 3},    // Row 0
    {4, 5, 6},    // Row 1
    {7, 8, 9}     // Row 2
};
```

#### Method 3: Jagged Array (rows with different lengths)
```java
int[][] jagged = new int[3][];
jagged[0] = new int[]{1, 2};          // Row 0 has 2 elements
jagged[1] = new int[]{3, 4, 5};       // Row 1 has 3 elements
jagged[2] = new int[]{6, 7, 8, 9};    // Row 2 has 4 elements
```

---

### Accessing 2D Array Elements:
```java
matrix[row][column]
matrix[0][0]   // First row, first column → 1
matrix[1][2]   // Second row, third column → 6
matrix[2][1]   // Third row, second column → 8
```

### 2D Array Size:
```java
matrix.length        // Number of rows
matrix[0].length     // Number of columns in row 0
```

---

### 2D Array Example Program:

```java
public class TwoDimensionalArrayDemo {
    public static void main(String[] args) {
        // Initialize a 2D array
        int[][] matrix = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };
        
        // Print using nested loops
        System.out.println("--- Matrix (2D Array) ---");
        for (int i = 0; i < matrix.length; i++) {           // Rows
            for (int j = 0; j < matrix[i].length; j++) {    // Columns
                System.out.print(matrix[i][j] + "\t");       // \t for tab alignment
            }
            System.out.println();   // New line after each row
        }
        
        // Access specific elements
        System.out.println("\nmatrix[0][0] = " + matrix[0][0]);   // 1
        System.out.println("matrix[1][2] = " + matrix[1][2]);     // 6
        System.out.println("matrix[2][1] = " + matrix[2][1]);     // 8
        
        // Number of rows and columns
        System.out.println("\nRows: " + matrix.length);           // 3
        System.out.println("Columns: " + matrix[0].length);       // 3
        
        // Sum of all elements
        int sum = 0;
        for (int i = 0; i < matrix.length; i++) {
            for (int j = 0; j < matrix[i].length; j++) {
                sum += matrix[i][j];
            }
        }
        System.out.println("Sum of all elements: " + sum);   // 45
    }
}
```

**Output:**
```
--- Matrix (2D Array) ---
1	2	3	
4	5	6	
7	8	9	

matrix[0][0] = 1
matrix[1][2] = 6
matrix[2][1] = 8

Rows: 3
Columns: 3
Sum of all elements: 45
```

---

### Common 2D Array Operations:

#### 1. Matrix Addition:
```java
public class MatrixAddition {
    public static void main(String[] args) {
        int[][] a = {{1, 2}, {3, 4}};
        int[][] b = {{5, 6}, {7, 8}};
        int[][] result = new int[2][2];
        
        // Add corresponding elements
        for (int i = 0; i < 2; i++) {
            for (int j = 0; j < 2; j++) {
                result[i][j] = a[i][j] + b[i][j];
            }
        }
        
        // Print result
        System.out.println("Matrix A + Matrix B:");
        for (int i = 0; i < 2; i++) {
            for (int j = 0; j < 2; j++) {
                System.out.print(result[i][j] + "\t");
            }
            System.out.println();
        }
    }
}
```

**Output:**
```
Matrix A + Matrix B:
6	8	
10	12	
```

#### 2. Transpose of a Matrix:
```java
public class MatrixTranspose {
    public static void main(String[] args) {
        int[][] matrix = {
            {1, 2, 3},
            {4, 5, 6}
        };   // 2 rows, 3 columns
        
        int rows = matrix.length;          // 2
        int cols = matrix[0].length;       // 3
        
        // Transpose: rows become columns, columns become rows
        int[][] transpose = new int[cols][rows];   // 3 rows, 2 columns
        
        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < cols; j++) {
                transpose[j][i] = matrix[i][j];
            }
        }
        
        System.out.println("Original Matrix (2x3):");
        for (int[] row : matrix) {
            for (int val : row) System.out.print(val + "\t");
            System.out.println();
        }
        
        System.out.println("\nTranspose Matrix (3x2):");
        for (int[] row : transpose) {
            for (int val : row) System.out.print(val + "\t");
            System.out.println();
        }
    }
}
```

**Output:**
```
Original Matrix (2x3):
1	2	3	
4	5	6	

Transpose Matrix (3x2):
1	4	
2	5	
3	6	
```

#### 3. Jagged Array Example:
```java
public class JaggedArrayDemo {
    public static void main(String[] args) {
        // Jagged array — rows have different lengths
        int[][] jagged = new int[3][];
        jagged[0] = new int[]{1, 2};
        jagged[1] = new int[]{3, 4, 5};
        jagged[2] = new int[]{6, 7, 8, 9};
        
        System.out.println("Jagged Array:");
        for (int i = 0; i < jagged.length; i++) {
            System.out.print("Row " + i + " (length=" + jagged[i].length + "): ");
            for (int j = 0; j < jagged[i].length; j++) {
                System.out.print(jagged[i][j] + " ");
            }
            System.out.println();
        }
    }
}
```

**Output:**
```
Jagged Array:
Row 0 (length=2): 1 2 
Row 1 (length=3): 3 4 5 
Row 2 (length=4): 6 7 8 9 
```

---

### Difference: 1D Array vs 2D Array

| Feature | 1D Array | 2D Array |
|---------|----------|----------|
| **Structure** | Single row of elements | Table (rows and columns) |
| **Declaration** | `int[] arr` | `int[][] arr` |
| **Access** | `arr[index]` | `arr[row][column]` |
| **Size** | `arr.length` | Rows: `arr.length`, Cols: `arr[0].length` |
| **Iteration** | Single loop | Nested loops (two loops) |
| **Use Case** | Simple list of values | Matrix, grid, table data |
| **Example** | `{1, 2, 3, 4, 5}` | `{{1,2}, {3,4}, {5,6}}` |

---

Understood.
Below is the **same content**, **cleaned**, **NO icons**, **pure notes**, **Markdown only**.

---

# Oops in java

# Class & Object (Java)

---

## Concept

A class is a blueprint or template that defines variables (data) and methods (behavior).
An object is a real instance of a class created at runtime using the `new` keyword.

A class represents the structure.
An object represents the actual working entity.

---

## Why Class & Object

* To represent real-world entities in code
* To group related data and behavior
* To enable code reuse
* To execute logic at runtime

---

## Syntax

```java
class ClassName {
    variables;
    methods;
}

ClassName objectName = new ClassName();
```

---

## Code (From Your Project)

### Address Class

```java
public class Address {
    String city = "Guntur";
    String State = "Andra Pradesh";
    String contry = "INDIA";

    void DisplayAddess() {
        System.out.println("City :" + city);
        System.out.println("State :" + State);
        System.out.println("Country :" + contry);
    }
}
```

---

### Student Class

```java
public class Student {

    String name = "NavyaSri";
    int RollNo = 101;

    Address address1 = new Address();

    void DisplayInfo() {
        System.out.println("Name : " + name);
        System.out.println("Roll No : " + RollNo);
        address1.DisplayAddess();
    }
}
```

---

### Main Class

```java
public class Main {
    public static void main(String[] args) {

        Student st1 = new Student();
        st1.DisplayInfo();

    }
}
```

---

## Line-by-Line Explanation

### Address Class

* `public class Address` defines a class named Address
* `city`, `State`, `contry` are instance variables
* `DisplayAddess()` is a method
* Method prints address details stored inside the object

---

### Student Class

* `Student` is a class
* `name` and `RollNo` are instance variables
* `Address address1 = new Address();` creates an Address object
* `DisplayInfo()` prints student details and calls Address method

---

### Main Class

* Program execution starts from `main()`
* `new Student()` creates an object in heap memory
* `st1.DisplayInfo()` calls method using object reference

---

## Object Creation Flow

1. JVM loads the Main class
2. main() method starts execution
3. Student object is created
4. Address object is created inside Student
5. Methods execute using object references

---

## Key Points

* Class does not consume memory
* Object consumes memory
* Instance variables belong to objects
* Methods are accessed using object reference

---

## OOP Concepts Used

* Class
* Object
* Method invocation

---

Next topic to request:

```
HAS-A Relationship (Association)
```


---

# Association (HAS-A Relationship) in Java

---

## Concept

Association represents a relationship between two separate classes where one class uses
another class as a dependency.  
When one class **has an object of another class**, it is called a **HAS-A relationship**.

In association:
- Both classes can exist independently
- Relationship is created through object reference

Example:
Student has an Address

---

## Why Association (HAS-A)

- To reuse functionality of another class
- To represent real-world relationships
- To achieve loose coupling
- To improve code modularity and readability

---

## Syntax

```java
class A {
    B obj = new B();
}
````

or using constructor injection:

```java
class A {
    B obj;
    A(B obj) {
        this.obj = obj;
    }
}
```

---

## Code (From Your Project)

### Student Class

```java
package basics;

public class Student {

    void StudentInfo() {
        System.out.println("This is Student Class StudentInfo() method ");
    }
}
```

---

### Address Class (HAS-A Relationship)

```java
package basics;

public class Address {

    private Student name;

    Address(Student name) {
        this.name = name;
    }

    void display() {
        name.StudentInfo();
        System.out.println("display method called in Address Class");
    }
}
```

---

### Main Class

```java
package basics;

public class Main {

    public static void main(String[] args) {

        Student name = new Student();
        Address addr = new Address(name);

        addr.display();
    }
}
```

---

## Explanation

* `Student` is an independent class
* `Address` has a reference of `Student`
* The `Student` object is passed to `Address` using constructor
* This is called **Constructor Injection**
* `Address` uses `Student` without extending it

---

## Relationship Type

* Student and Address are separate entities
* Address depends on Student
* No inheritance is used
* This confirms HAS-A (Association), not IS-A

---

## Object Creation Flow

1. JVM loads Main class
2. Student object is created
3. Address object is created with Student dependency
4. Address method accesses Student method

---

## Key Points

* Association uses object reference
* Classes remain loosely coupled
* One class can use multiple other classes
* Preferred over inheritance when relationship is "uses-a"

---

## OOP Concepts Used

* Association
* HAS-A relationship
* Constructor Injection
* Dependency handling

```
```
---
# Inheritance (Single Inheritance) in Java

---

## Concept

Inheritance is an OOP mechanism where one class acquires the properties and methods of another class.  
In **single inheritance**, a child class inherits from **only one parent class**.

This creates an **IS-A relationship**.

Example:  
Child IS-A Father

---

## Why Single Inheritance

- To reuse existing code
- To avoid code duplication
- To create logical parent–child relationships
- To allow method overriding

---

## Syntax

```java
class Parent {
    // variables and methods
}

class Child extends Parent {
    // additional variables and methods
}
````

---

## Code (From Your Project)

### Parent Class (Father)

```java
package basics;

public class Father {
    String FatherName = "Pullayya";
    int age = 55;

    void fatherMethod() {
        System.out.println("i'am " + FatherName + " age " + age);
        System.out.println("i love Family ");
    }

    void hobbies() {
        System.out.println("Reading Paper");
        System.out.println("Cycling ");
        System.out.println("exercise ");
        System.out.println("Farming ");
    }
}
```

---

### Child Class (Children)

```java
package basics;

public class Children extends Father {

    String name = "Raju";
    int age = 20;

    void childMethod() {
        System.out.println("i'am " + name + " age " + age);
        System.out.println("I love C7");
    }
}
```

---

### Main Class

```java
package basics;

public class Main {
    public static void main(String[] args) {

        Children c1 = new Children();

        c1.fatherMethod();
        c1.childMethod();
        c1.hobbies();
    }
}
```

---

## Explanation

* `Father` is the parent class
* `Children` is the child class
* `extends` keyword establishes inheritance
* Child class gets access to public and protected members of parent
* Child object can call both parent and child methods

---

## IS-A Relationship

* Children IS-A Father
* This relationship allows reuse of parent functionality

---

## Method Access Flow

* `c1.fatherMethod()` → method inherited from Father
* `c1.hobbies()` → method inherited from Father
* `c1.childMethod()` → method of Children class

---

## Key Rules of Single Inheritance

* One child class can extend only one parent class
* Java does not support multiple inheritance using classes
* Constructors are not inherited
* Private members are not directly accessible

---

## Memory Behavior

* One object of Children is created
* Parent class variables exist inside child object
* Methods are resolved using inheritance hierarchy

---

## OOP Concepts Used

* Inheritance
* Single Inheritance
* IS-A relationship
* Code Reusability

```
```
---
# Inheritance (Multilevel Inheritance) in Java

---

## Concept

Multilevel inheritance occurs when a class is derived from another derived class.  
This forms a **chain of inheritance** where each class inherits from its immediate parent.

Structure:
GrandFather → Father → Children

Each lower-level class automatically gets access to all higher-level class members
(except private members).

---

## Why Multilevel Inheritance

- To represent real-world hierarchical relationships
- To reuse code across multiple levels
- To extend functionality step by step
- To organize complex systems logically

---

## Syntax

```java
class A {
}

class B extends A {
}

class C extends B {
}
````

---

## Code (From Your Project)

### GrandFather Class

```java
package basics;

public class GrandFather {
    String GrandFatherName = "rammaya";
    int age = 75;

    void GrandfatherMethod() {
        System.out.println("i'am " + GrandFatherName + " age " + age);
        System.out.println("i love Family ");
    }

    void Grandfatherhobbies() {
        System.out.println("Chilling with friends");
        System.out.println("Farming ");
        System.out.println("camp fire ");
        System.out.println("... ");
    }
}
```

---

### Father Class

```java
package basics;

public class Father extends GrandFather {
    String FatherName = "Pullayya";
    int age = 55;

    void fatherMethod() {
        System.out.println("i'am " + FatherName + " age " + age);
        System.out.println("i love Family ");
    }

    void fatherhobbies() {
        System.out.println("Reading Paper");
        System.out.println("Cycling ");
        System.out.println("exercise ");
        System.out.println("Farming ");
    }
}
```

---

### Children Class

```java
package basics;

public class Children extends Father {

    String name = "Raju";
    int age = 20;

    void childMethod() {
        System.out.println("i'am " + name + " age " + age);
        System.out.println("I love C7");
    }

    void childrenhobbies() {
        System.out.println("Movies");
        System.out.println("Cars");
        System.out.println("Food");
        System.out.println("JFS");
    }
}
```

---

### Main Class

```java
package basics;

public class Main {
    public static void main(String[] args) {

        Children c1 = new Children();

        System.out.println("GarndFather Method called with child object");
        System.out.println("-------------------------------------------");
        c1.GrandfatherMethod();
        c1.Grandfatherhobbies();

        System.out.println("-------------------------------------------");
        System.out.println("Father Method called with child object");
        System.out.println("-------------------------------------------");
        c1.fatherMethod();
        c1.fatherhobbies();

        System.out.println("-------------------------------------------");
        System.out.println("Child Method called with child object");
        System.out.println("-------------------------------------------");
        c1.childMethod();
        c1.childrenhobbies();
    }
}
```

---

## Explanation

* `GrandFather` is the root parent class
* `Father` inherits from `GrandFather`
* `Children` inherits from `Father`
* `Children` object can access methods from all three classes
* Inheritance flows upward in the hierarchy

---

## Method Resolution Flow

* JVM searches method in Children class first
* If not found, it moves to Father class
* If still not found, it moves to GrandFather class

---

## IS-A Relationship Chain

* Children IS-A Father
* Father IS-A GrandFather
* Therefore, Children IS-A GrandFather

---

## Key Rules of Multilevel Inheritance

* Java supports multilevel inheritance
* Private members are not inherited
* Constructors execute from parent to child
* Method overriding works across levels

---

## Memory Behavior

* Only one object is created (Children)
* Parent class data exists inside child object
* Separate memory is not created for parent objects

---

## OOP Concepts Used

* Inheritance
* Multilevel Inheritance
* IS-A relationship
* Code Reusability

```
```
---
# Inheritance (Hierarchical Inheritance) in Java

---

## Concept

Hierarchical inheritance occurs when **multiple child classes inherit from the same parent class**.

One parent → many children

Each child class gets access to the parent class members, but **child classes do not share
their own members with each other**.

---

## Why Hierarchical Inheritance

- To reuse common behavior in multiple classes
- To represent real-world structures with one base entity
- To avoid duplication of common logic
- To maintain clear class separation

---

## Structure

```

```
    Parent
    |
```

---

|              |
Child1         Child2

````

---

## Syntax

```java
class Parent {
}

class Child1 extends Parent {
}

class Child2 extends Parent {
}
````

---

## Code (From Your Project)

### Parent Class (C)

```java
package inheritance;

public class C extends B {
    void displayC() {
        System.out.println("-------------------------------------------");
        System.out.println("this is display method C");
        System.out.println("Class C inherits from B");
    }
}
```

---

### Child Class 1 (D)

```java
package inheritance;

public class D extends C {
    void displayD() {
        System.out.println("-------------------------------------------");
        System.out.println("this is display method D");
        System.out.println("Class D inherits from C (child 1)");
    }
}
```

---

### Child Class 2 (E)

```java
package inheritance;

public class E extends C {
    void displayE() {
        System.out.println("-------------------------------------------");
        System.out.println("this is display method E");
        System.out.println("Class E inherits from C (child 2)");
    }
}
```

---

### Supporting Parent Classes

```java
package inheritance;

public class A {
    void DisplayForA() {
        System.out.println("-------------------------------------------");
        System.out.println("this is display method A");
        System.out.println("class A Root parent class");
    }
}
```

```java
package inheritance;

public class B extends A {
    void displayB() {
        System.out.println("-------------------------------------------");
        System.out.println("this is display method B");
        System.out.println("Class B inherits from A");
    }
}
```

---

### Main Class

```java
package inheritance;

public class Main {
    public static void main(String[] args) {

        D objD = new D();
        objD.displayD();
        objD.displayC();
        objD.displayB();
        objD.DisplayForA();

        System.out.println("--------------------");

        E objE = new E();
        objE.displayE();
        objE.displayC();
        objE.displayB();
        objE.DisplayForA();
    }
}
```

---

## Explanation

* `C` acts as the **common parent** for `D` and `E`
* `D` and `E` both inherit from `C`
* Both child classes reuse methods from:

  * `C`
  * `B`
  * `A`
* `D` and `E` do not inherit from each other

---

## IS-A Relationship

* D IS-A C
* E IS-A C
* D IS-A B and A (through C)
* E IS-A B and A (through C)

---

## Method Resolution Flow

For object of class `D`:

1. JVM checks `D`
2. Then `C`
3. Then `B`
4. Then `A`

Same flow applies to `E`.

---

## Key Rules of Hierarchical Inheritance

* One parent can have multiple child classes
* Java supports hierarchical inheritance
* Private members are not inherited
* Each child class remains independent

---

## Memory Behavior

* Separate objects are created for `D` and `E`
* Parent class members exist inside each child object
* No shared object memory between sibling classes

---

## OOP Concepts Used

* Inheritance
* Hierarchical Inheritance
* IS-A relationship
* Code Reusability

```
```
---
# Polymorphism in Java (Runtime Polymorphism)

---

## Concept

Polymorphism means **many forms**.  
In Java, polymorphism allows the **same method name** to behave differently based on the
**object type at runtime**.

Runtime polymorphism is achieved using:
- Method overriding
- Parent class reference pointing to child class object

---

## Why Polymorphism

- To achieve flexibility in code
- To support dynamic behavior
- To follow the Open–Closed Principle
- To reduce dependency on specific implementations

---

## Types of Polymorphism in Java

1. Compile-time Polymorphism (Method Overloading)
2. Runtime Polymorphism (Method Overriding)

This example demonstrates **Runtime Polymorphism**.

---

## Syntax (Runtime Polymorphism)

```java
class Parent {
    void method() { }
}

class Child extends Parent {
    @Override
    void method() { }
}

Parent obj = new Child();
obj.method();
````

---

## Code (From Your Project)

### Parent Class (Bank)

```java
package polymarphism;

public class Bank {
    double RateOfIntrent() {
        return 1.0;
    }
}
```

---

### Child Class 1 (SBI)

```java
package polymarphism;

public class SBI extends Bank {
    @Override
    double RateOfIntrent() {
        return 2.0;
    }
}
```

---

### Child Class 2 (Andrabank)

```java
package polymarphism;

public class Andrabank extends Bank {
    @Override
    double RateOfIntrent() {
        return 3.0;
    }
}
```

---

### Main Class

```java
package polymarphism;

public class Main {
    public static void main(String args[]) {

        Bank obj = new Bank();
        System.out.println("Bank Interest : " + obj.RateOfIntrent());

        Bank obj1 = new SBI();
        System.out.println("SBI Bank Interest : " + obj1.RateOfIntrent());

        Bank obj2 = new Andrabank();
        System.out.println("AndraBank Interest : " + obj2.RateOfIntrent());
    }
}
```

---

## Explanation

* `Bank` defines a method `RateOfIntrent()`
* `SBI` and `Andrabank` override the same method
* Parent reference (`Bank`) holds child objects
* Method call is resolved at **runtime**, not compile time

---

## Runtime Method Dispatch

When `obj1.RateOfIntrent()` is called:

* JVM checks object type (SBI)
* SBI's overridden method is executed

Same logic applies for `Andrabank`.

---

## Key Rules of Runtime Polymorphism

* Method overriding is mandatory
* Inheritance is required
* Method signature must be same
* Return type must be same or covariant
* Access level cannot be reduced

---

## IS-A Relationship

* SBI IS-A Bank
* Andrabank IS-A Bank
* Allows parent reference to hold child object

---

## Memory Behavior

* Reference type decides accessible methods
* Object type decides method implementation
* Only one method executes at runtime

---

## OOP Concepts Used

* Polymorphism
* Runtime Polymorphism
* Method Overriding
* Dynamic Method Dispatch

```
```
---

# Abstraction in Java (Abstract Class & Interface)

---

## Concept

Abstraction means **hiding implementation details and showing only essential features** to the user.

In Java, abstraction is achieved using:
1. **Abstract classes**
2. **Interfaces**

The user knows **what** the object does, not **how** it does it.

---

## Why Abstraction

- To hide internal implementation
- To reduce complexity
- To improve security
- To support loose coupling
- To enable runtime flexibility

---

# Part A: Abstraction using Abstract Class

---

## Abstract Class Concept

An abstract class:
- Is declared using the `abstract` keyword
- Can contain abstract and non-abstract methods
- Cannot be instantiated
- Is used when classes share common behavior with partial implementation

---

## Abstract Class Syntax

```java
abstract class ClassName {
    abstract void method();
    void normalMethod() { }
}
````

---

## Code (From Your Project)

### Abstract Class (ATM)

```java
package AbstractionDemo;

public abstract class ATM {
    double balance = 100000;

    public abstract void withdraw(double Amount);
    public abstract void checkBalance();
}
```

---

### Implementation Class (SBIATM)

```java
package AbstractionDemo;

public class SBIATM extends ATM {

    public void withdraw(double Amount) {

        if (Amount <= balance) {
            balance = balance - Amount;
            System.out.println("Withdraw Successfull");
            System.out.println("Remaning Balance: " + balance);
        } else {
            System.out.println("Insufficent Amount");
            System.out.println("Your Current Balance: " + balance);
        }
    }

    public void checkBalance() {
        System.out.println("Your Current Balance: " + balance);
    }
}
```

---

### Main Class

```java
package AbstractionDemo;
import java.util.Scanner;

public class Main {
    public static void main(String args[]) {

        ATM atm = new SBIATM();

        Scanner sc = new Scanner(System.in);
        System.out.print("Enter Amount for Withdraw : ");
        double money = sc.nextDouble();

        atm.checkBalance();
        atm.withdraw(money);
    }
}
```

---

## Explanation (Abstract Class)

* `ATM` hides balance handling logic
* User interacts using ATM reference
* `SBIATM` provides concrete implementation
* Implementation can change without affecting user code

---

## Key Rules of Abstract Class

* Can have constructors
* Can have variables
* Can have abstract and non-abstract methods
* Cannot create object directly

---

# Part B: Abstraction using Interface

---

## Interface Concept

An interface:

* Is a pure abstraction blueprint
* Contains method declarations (contracts)
* Supports multiple inheritance
* Forces implementation classes to define behavior

---

## Interface Syntax

```java
interface InterfaceName {
    void method();
}
```

---

## Code (From Your Project)

### Interface (FoodApp)

```java
package abstraction;

public interface FoodApp {
    void placeOrder();
    void makePayment();
}
```

---

### Implementation Class (Swiggy)

```java
package abstraction;

public class Swiggy implements FoodApp {

    public void placeOrder() {
        System.out.println("Order Placed Via Swiggy");
    }

    public void makePayment() {
        System.out.println("Payment done using Swiggy Gateway");
    }
}
```

---

### Implementation Class (Zomato)

```java
package abstraction;

public class Zomato implements FoodApp {

    public void placeOrder() {
        System.out.println("Order Placed Via Zomato");
    }

    public void makePayment() {
        System.out.println("Payment done using Zomato Gateway");
    }
}
```

---

### Implementation Class (EatClub)

```java
package abstraction;

public class EatClub implements FoodApp {

    public void placeOrder() {
        System.out.println("Order Placed Via EatClub");
    }

    public void makePayment() {
        System.out.println("Payment done using EatClub Gateway");
    }
}
```

---

### Main Class

```java
package abstraction;

public class Main {
    public static void main(String args[]) {

        FoodApp app;

        app = new Swiggy();
        app.placeOrder();
        app.makePayment();

        System.out.println("-------------------");

        app = new Zomato();
        app.placeOrder();
        app.makePayment();
    }
}
```

---

## Explanation (Interface)

* `FoodApp` defines what actions must be performed
* Implementation classes define how actions are performed
* Main program is independent of implementation
* Switching implementation requires no code change in logic

---

## Abstract Class vs Interface

| Feature              | Abstract Class      | Interface                  |
| -------------------- | ------------------- | -------------------------- |
| Methods              | Abstract + Concrete | Abstract (default allowed) |
| Variables            | Allowed             | public static final        |
| Multiple Inheritance | No                  | Yes                        |
| Object Creation      | No                  | No                         |

---

## OOP Concepts Used

* Abstraction
* Interface
* Abstract Class
* Loose Coupling
---
# Encapsulation in Java

---

## Concept

Encapsulation is the process of **binding data (variables) and methods together** and
**restricting direct access to data** from outside the class.

Data is hidden using `private` access modifier and accessed only through
**public getter and setter methods**.

Encapsulation provides **data protection and controlled access**.

---

## Why Encapsulation

- To protect data from unauthorized access
- To control how data is read and modified
- To improve maintainability
- To follow security and design principles

---

## Encapsulation Syntax

```java
class ClassName {
    private data;

    public void setData(value) { }
    public dataType getData() { }
}
````

---

## Code (From Your Project)

### Encapsulated Class (Car)

```java id="gxj9yq"
package encapsulation;

public class Car {

    private String brand;
    private int speed;

    public String getBrand() {
        return brand;
    }

    public void setBrand(String brand) {
        this.brand = brand;
    }

    public int getSpeed() {
        return speed;
    }

    public void setSpeed(int speed) {
        this.speed = speed;
    }

    public void printinfo() {
        System.out.println("Barnd : " + brand);
        System.out.println("Speed : " + speed);
    }
}
```

---

### Main Class

```java id="r6k5tu"
package encapsulation;

public class Main {
    public static void main(String[] args) {

        Car porsch = new Car();

        porsch.setBrand("Porsch 911");
        porsch.setSpeed(100);

        porsch.printinfo();
    }
}
```

---

## Explanation

* `brand` and `speed` are declared as `private`
* Direct access from outside the class is not allowed
* Setter methods modify the data safely
* Getter methods provide read-only access
* `this` keyword refers to current object

---

## Data Protection Flow

1. Data is hidden inside the class
2. External class cannot access variables directly
3. Access is allowed only through methods
4. Validation logic can be added in setters

---

## Key Rules of Encapsulation

* Variables should be `private`
* Methods should be `public`
* Class should provide controlled access
* Internal data cannot be modified directly

---

## Advantages of Encapsulation

* Better security
* Flexibility to change implementation
* Improved code readability
* Reduced complexity

---

## OOP Concepts Used

* Encapsulation
* Data Hiding
* Getter and Setter Methods

---
# Interface Multiple Inheritance in Java

---

## Concept

Java does not support multiple inheritance using classes because of ambiguity problems.
However, Java **supports multiple inheritance using interfaces**.

A class can implement **more than one interface**, allowing it to inherit multiple behaviors
without ambiguity.

This is called **Multiple Inheritance using Interfaces**.

---

## Why Interface Multiple Inheritance

- To achieve multiple inheritance safely
- To avoid ambiguity present in class multiple inheritance
- To follow abstraction and loose coupling
- To allow a class to follow multiple contracts

---

## Syntax

```java
interface A {
    void methodA();
}

interface B {
    void methodB();
}

class C implements A, B {
    public void methodA() { }
    public void methodB() { }
}
````

---

## Code (From Your Project)

### Interface A

```java
package interfaceconsept;

public interface A {
    void methodA();
}
```

---

### Interface B

```java
package interfaceconsept;

public interface B {
    void methodB();
}
```

---

### Implementation Class (C)

```java
package interfaceconsept;

public class C implements A, B {

    @Override
    public void methodA() {
        System.out.println("This is Interface A ");
    }

    @Override
    public void methodB() {
        System.out.println("This is Interface B ");
    }

    public void methodC() {
        System.out.println(
            "This is Class C implements Interface A , B to form a Multiple-inheritance using interfaces"
        );
    }

    public static void main(String[] args) {
        C cobj = new C();

        cobj.methodA();
        cobj.methodB();
        cobj.methodC();
    }
}
```

---

## Explanation

* `A` and `B` are independent interfaces
* Both define separate method contracts
* Class `C` implements both interfaces
* `C` must provide implementation for all interface methods
* No ambiguity occurs because interfaces do not contain state

---

## Key Rules of Interface Multiple Inheritance

* A class can implement multiple interfaces
* Interfaces contain method declarations
* Implementation class must override all methods
* No multiple inheritance using classes

---

## IS-A Relationship

* C IS-A A
* C IS-A B

This allows polymorphic behavior using interface references.

---

## Memory Behavior

* Only one object of class `C` is created
* Interface references point to same object
* No duplicate data members exist

---

## Advantages

* Solves multiple inheritance problem
* Improves flexibility
* Supports abstraction
* Encourages loose coupling

---

## OOP Concepts Used

* Interface
* Multiple Inheritance
* Abstraction
* Polymorphism


---
# Diamond Problem Handling in Java (Using Interfaces)

---

## Concept

The **Diamond Problem** occurs when a class implements **multiple interfaces** that contain
methods with the **same name and signature**.

Java allows multiple inheritance using interfaces, but when **default methods** are involved,
method ambiguity can arise.  
Java resolves this by forcing the implementing class to **explicitly override the method**.

---

## Why Diamond Problem Occurs

- Java allows a class to implement multiple interfaces
- Interfaces can have `default` methods
- If two interfaces provide the same default method, JVM cannot decide which one to execute

This situation forms a diamond-shaped inheritance structure.

---

## Diamond Structure

```

```
    A
   / \
  B   C
   \ /
    D
```



- Interface `A` defines a method
- Interfaces `B` and `C` extend `A` and override the same method
- Class `D` implements both `B` and `C`

---

## Rule to Handle Diamond Problem

If a class implements two interfaces that have the **same default method**, then:
- The class **must override the method**
- Inside the method, it can explicitly call:
  - `InterfaceName.super.methodName()`

---

## Syntax for Conflict Resolution

```java
InterfaceName.super.methodName();
````

---

## Code (From Your Project)

### Interface A

```java
package interfaceconsept;

public interface A {
    default void method() {
        System.out.println("this is method a for X purpose ");
    }
}
```

---

### Interface B

```java
package interfaceconsept;

public interface B extends A {
    default void method() {
        System.out.println("this is method a for Y purpose");
    }
}
```

---

### Interface C

```java
package interfaceconsept;

public interface C extends A {
    default void method() {
        System.out.println("this is method a for Z purpose");
    }
}
```

---

### Implementation Class (D)

```java
package interfaceconsept;

public class D implements B, C {

    @Override
    public void method() {

        B.super.method();
        C.super.method();
    }

    public static void main(String args[]) {
        D x = new D();
        x.method();
    }
}
```

---

## Explanation

* Interfaces `B` and `C` both provide a default implementation of `method()`
* Class `D` implements both interfaces
* JVM cannot decide which `method()` to call
* Java forces class `D` to override the method
* Inside the overridden method:

  * `B.super.method()` calls B’s version
  * `C.super.method()` calls C’s version

---

## Important Rules

* Diamond problem occurs only with **default methods**
* Interfaces without default methods do not cause ambiguity
* Class method always has higher priority than interface default method
* Explicit override is mandatory to resolve conflict

---

## Key Points

* Java avoids diamond problem using strict rules
* Multiple inheritance is safe with interfaces
* Ambiguity is resolved at compile time
* `InterfaceName.super.method()` is allowed only inside implementing class

---

## OOP Concepts Used

* Interface
* Multiple Inheritance
* Diamond Problem
* Method Conflict Resolution
* Default Methods

```
```
---

# Constructor Injection in Java

---

## Concept

Constructor Injection is a form of **Dependency Injection** where an object receives its
dependency **through its constructor** instead of creating it internally.

The dependent class does **not create** the object it depends on.
Instead, the dependency is **passed from outside**.

This improves **loose coupling** and **testability**.

---

## Why Constructor Injection

- To avoid tight coupling between classes
- To make code flexible and reusable
- To follow Dependency Inversion Principle
- To make unit testing easier
- To control object creation externally

---

## Basic Idea

Instead of this (tight coupling):

```java
class A {
    B obj = new B();
}
````

Use this (constructor injection):

```java
class A {
    B obj;

    A(B obj) {
        this.obj = obj;
    }
}
```

---

## Code (From Your Project)

### Dependent Class (Student)

```java
package basics;

public class Student {

    void StudentInfo() {
        System.out.println("This is Student Class StudentInfo() method ");
    }
}
```

---

### Dependee Class Using Constructor Injection (Address)

```java
package basics;

public class Address {

    private Student name;

    Address(Student name) {
        this.name = name;
    }

    void display() {
        name.StudentInfo();
        System.out.println("display method called in Address Class");
    }
}
```

---

### Main Class (Injecting Dependency)

```java
package basics;

public class Main {
    public static void main(String[] args) {

        Student name = new Student();      // Dependency created
        Address addr = new Address(name);  // Dependency injected

        addr.display();
    }
}
```

---

## Explanation

* `Student` is the dependency
* `Address` depends on `Student`
* `Address` does not create `Student` object
* Dependency is passed through the constructor
* This is called **Constructor Injection**

---

## Flow of Execution

1. JVM starts `main()`
2. `Student` object is created
3. `Address` object is created by passing `Student`
4. `Address` stores dependency reference
5. `Address` uses `Student` methods

---

## HAS-A Relationship with Constructor Injection

* Address HAS-A Student
* Relationship is created externally
* Address does not control dependency lifecycle

---

## Advantages of Constructor Injection

* Clear dependency requirement
* Object is always in valid state
* Easier to test with mock objects
* Promotes loose coupling
* Recommended over field injection

---

## Comparison: Normal HAS-A vs Constructor Injection

| Aspect          | Normal HAS-A | Constructor Injection |
| --------------- | ------------ | --------------------- |
| Object creation | Inside class | Outside class         |
| Coupling        | Tight        | Loose                 |
| Flexibility     | Low          | High                  |
| Testability     | Hard         | Easy                  |

---

## Key Rules

* Dependency is passed via constructor
* Constructor is called only once
* Dependency cannot be null (recommended)
* Preferred DI method in Java

---

## OOP Concepts Used

* Association
* HAS-A relationship
* Dependency Injection
* Constructor Injection

```
```
---

#  Java Collection Framework (JCF) — Student Notes

---

## 1. What is the Java Collection Framework?

The **Java Collection Framework (JCF)** is a set of **classes and interfaces** in Java that provide ready-made data structures to store, manage, and manipulate groups of objects efficiently.

Before JCF, developers had to write their own data structures from scratch. JCF solves this problem by providing:

- **Interfaces** → Define what operations can be performed (e.g., `List`, `Set`, `Map`)
- **Classes** → Actual implementations of those interfaces (e.g., `ArrayList`, `HashSet`, `HashMap`)
- **Algorithms** → Utility methods like sorting and searching (via `Collections` class)

### Why use JCF?

| Without JCF | With JCF |
|---|---|
| Write your own data structures | Ready-made, tested data structures |
| Manual memory management | Automatic resizing |
| No standard API | Consistent, standard methods |
| More bugs | Less code, fewer bugs |

---

## 2. JCF Hierarchy Overview

```
java.util
│
├── Collection (Interface)
│   ├── List (Interface)         → Ordered, allows duplicates
│   │   ├── ArrayList
│   │   ├── LinkedList
│   │   └── Vector
│   │
│   ├── Set (Interface)          → No duplicates
│   │   ├── HashSet
│   │   ├── LinkedHashSet
│   │   └── TreeSet
│   │
│   └── Queue (Interface)        → FIFO order
│       ├── PriorityQueue
│       └── LinkedList
│
└── Map (Interface)              → Key-Value pairs
    ├── HashMap
    ├── LinkedHashMap
    └── TreeMap
```

>   **In these notes**, we will cover **List** and **Set** in detail.

---

## 3. List Interface

### What is a List?

A **List** is an **ordered collection** (also called a sequence) that:

-   Maintains **insertion order** (elements stay in the order you add them)
-   **Allows duplicate** values
-   Allows **null** values
-   Elements are accessed by **index** (starting from 0)

```
List = [10, 20, 20, 30, null, 40]
        ↑                          ↑
      index 0                   index 5
```

---

### Types of List

| Type | Class | Order | Null Allowed | Performance |
|---|---|---|---|---|
| Dynamic Array | `ArrayList` | Insertion order | Yes | Fast for access |
| Doubly Linked | `LinkedList` | Insertion order | Yes | Fast for insert/delete |
| Synchronized Array | `Vector` | Insertion order | Yes | Thread-safe, slower |

>  Most commonly used → **ArrayList**

---

### Creating a List

```java
import java.util.*;

// Method 1: Using interface type (Recommended)
List<String> list = new ArrayList<>();

// Method 2: Using class type directly
ArrayList<String> list = new ArrayList<>();

// Method 3: ArrayList with initial capacity
ArrayList<String> list = new ArrayList<>(10);

// Method 4: Initialize with values directly
List<String> list = new ArrayList<>(Arrays.asList("Aparna", "Navya", "Ramya"));
```

>     **Best Practice:** Always use `List<Type>` on the left side. This makes your code flexible — you can switch between `ArrayList` and `LinkedList` without changing much.

---

### List Methods

---

####   1. `add()`

**Definition:**  
Adds an element to the list. You can add at the **end** or at a **specific index**.

**Syntax:**
```java
listName.add(value);               // Adds at the end
listName.add(index, value);        // Inserts at specific position
```

**Use:**  
Used whenever you want to insert elements into a list.

**Example Program:**
```java
import java.util.*;

public class AddDemo {
    public static void main(String[] args) {
        List<String> list = new ArrayList<>();

        list.add("Maheswaram");        // Adds at end → index 0
        list.add(1, "Sri");            // Inserts "Sri" at index 1

        System.out.println(list);
    }
}
```

**Output:**
```
[Maheswaram, Sri]
```

**Explanation:**  
- `list.add("Maheswaram")` → Adds `"Maheswaram"` at position 0.
- `list.add(1, "Sri")` → Inserts `"Sri"` at position 1, shifting existing elements to the right.

---

####   2. `addAll()`

**Definition:**  
Adds **all elements** from one list into another list at the end.

**Syntax:**
```java
list1.addAll(list2);               // Adds all of list2 into list1 at end
list1.addAll(index, list2);        // Inserts list2 starting at given index
```

**Use:**  
Used when you want to merge two lists together. Returns `true` if the list changed.

**Example Program:**
```java
import java.util.*;

public class AddAllDemo {
    public static void main(String[] args) {
        List<Integer> nums = new ArrayList<>();
        nums.add(1);
        nums.add(2);
        nums.add(3);
        System.out.println("First List  : " + nums);

        List<Integer> nums1 = new ArrayList<>();
        nums1.add(11);
        nums1.add(22);
        nums1.add(33);
        System.out.println("Second List : " + nums1);

        nums.addAll(nums1);

        System.out.println("After addAll: " + nums);
    }
}
```

**Output:**
```
First List  : [1, 2, 3]
Second List : [11, 22, 33]
After addAll: [1, 2, 3, 11, 22, 33]
```

**Explanation:**  
`addAll()` copies every element from `nums1` and appends them to the end of `nums`. The original `nums1` list remains unchanged.

---

####   3. `get()`

**Definition:**  
Retrieves (reads) the element at a specific index. Does **not** remove the element.

**Syntax:**
```java
listName.get(index);
```

>    Index starts from **0** and ends at **size - 1**. Accessing an invalid index throws `IndexOutOfBoundsException`.

**Use:**  
Used when you need to read a specific element without modifying the list.

**Example Program:**
```java
import java.util.*;

public class GetDemo {
    public static void main(String[] args) {
        List<Integer> numbers = new ArrayList<>();
        numbers.add(100);   // index 0
        numbers.add(200);   // index 1
        numbers.add(200);   // index 2
        numbers.add(400);   // index 3

        int value = numbers.get(3);

        System.out.println("Element at index 3 is : " + value);
    }
}
```

**Output:**
```
Element at index 3 is : 400
```

**Explanation:**  
`numbers.get(3)` fetches the element at index 3, which is `400`. The list is not modified.

---

####   4. `set()`

**Definition:**  
**Replaces** the element at a given index with a new value. The size of the list remains the same.

**Syntax:**
```java
listName.set(index, newValue);
```

**Use:**  
Used when you want to **update** an existing element at a particular position.

**Example Program:**
```java
import java.util.*;

public class SetDemo {
    public static void main(String[] args) {
        List<Integer> numbers = new ArrayList<>();
        numbers.add(100);
        numbers.add(200);
        numbers.add(200);   // duplicate — we'll fix this
        numbers.add(400);

        System.out.println("Before updating: " + numbers);

        numbers.set(2, 300);   // replace index 2 (200 → 300)
        numbers.set(3, 999);   // replace index 3 (400 → 999)

        System.out.println("After updating : " + numbers);
    }
}
```

**Output:**
```
Before updating: [100, 200, 200, 400]
After updating : [100, 200, 300, 999]
```

**Explanation:**  
`set(2, 300)` replaces the value `200` at index 2 with `300`. `set(3, 999)` replaces `400` at index 3 with `999`. List size stays at 4.

---

####   5. `remove(int index)`

**Definition:**  
Removes the element at the **specified index**. All elements after it **shift left**, and the list size decreases by 1.

**Syntax:**
```java
listName.remove(index);
```

**Use:**  
Used when you know the **position** of the element you want to delete.

**Example Program:**
```java
import java.util.*;

public class RemoveIndexDemo {
    public static void main(String[] args) {
        List<Integer> numbers = new ArrayList<>();
        numbers.add(100);  // index 0
        numbers.add(200);  // index 1
        numbers.add(200);  // index 2
        numbers.add(400);  // index 3

        System.out.println("Before removing: " + numbers);

        numbers.remove(2);   // removes element at index 2

        System.out.println("After removing : " + numbers);
    }
}
```

**Output:**
```
Before removing: [100, 200, 200, 400]
After removing : [100, 200, 400]
```

**Explanation:**  
`remove(2)` deletes the element at index 2 (the second `200`). The remaining elements shift left: `400` moves from index 3 to index 2.

---

####   6. `remove(Object)`

**Definition:**  
Removes the **first occurrence** of the specified value from the list.

**Syntax:**
```java
listName.remove(Integer.valueOf(value));   // For Integer lists, use Integer.valueOf()
listName.remove("stringValue");            // For String lists
```

>    **Important:** For `List<Integer>`, always use `Integer.valueOf()` to avoid confusion with `remove(int index)`.

**Use:**  
Used when you know the **value** of the element you want to delete (not the position).

**Example Program:**
```java
import java.util.*;

public class RemoveObjectDemo {
    public static void main(String[] args) {
        List<Integer> numbers = new ArrayList<>();
        numbers.add(100);
        numbers.add(200);
        numbers.add(200);
        numbers.add(400);

        System.out.println("Before removing: " + numbers);

        numbers.remove(Integer.valueOf(400));   // removes value 400

        System.out.println("After removing : " + numbers);
    }
}
```

**Output:**
```
Before removing: [100, 200, 200, 400]
After removing : [100, 200, 200]
```

**Explanation:**  
`Integer.valueOf(400)` tells Java to treat `400` as an **object value**, not an index. It finds and removes the first element equal to `400`.

---

####   7. `size()`

**Definition:**  
Returns the **total number of elements** currently in the list.

**Syntax:**
```java
listName.size();
```

**Use:**  
Used in loops, validations, or whenever you need to know how many items are in the list.

**Example Program:**
```java
import java.util.*;

public class SizeDemo {
    public static void main(String[] args) {
        List<Integer> numbers = new ArrayList<>();
        numbers.add(100);
        numbers.add(200);
        numbers.add(300);
        numbers.add(400);

        System.out.println("Size of list: " + numbers.size());
    }
}
```

**Output:**
```
Size of list: 4
```

**Explanation:**  
`size()` counts all elements and returns `4` since we added 4 elements.

---

####   8. `isEmpty()`

**Definition:**  
Checks whether the list has **no elements**. Returns `true` if empty, `false` if it has elements.

**Syntax:**
```java
listName.isEmpty();
```

**Use:**  
Used before performing operations to avoid errors on empty lists.

**Example Program:**
```java
import java.util.*;

public class IsEmptyDemo {
    public static void main(String[] args) {
        List<Integer> numbers = new ArrayList<>();

        System.out.println("Before adding elements: " + numbers.isEmpty());   // true

        numbers.add(100);
        numbers.add(200);
        numbers.add(300);
        numbers.add(400);

        System.out.println("After adding elements : " + numbers.isEmpty());   // false
    }
}
```

**Output:**
```
Before adding elements: true
After adding elements : false
```

**Explanation:**  
Before any `add()`, the list is empty so `isEmpty()` returns `true`. After adding elements, it returns `false`.

---

####   9. `contains()`

**Definition:**  
Checks if a specific **value exists** in the list. Returns `true` if found, `false` if not.

**Syntax:**
```java
listName.contains(value);
```

**Use:**  
Used to verify if an element is present before performing operations like remove or update.

**Example Program:**
```java
import java.util.*;

public class ContainsDemo {
    public static void main(String[] args) {
        List<Integer> numbers = new ArrayList<>();
        numbers.add(100);
        numbers.add(200);
        numbers.add(300);
        numbers.add(400);

        System.out.println("Contains 500? " + numbers.contains(500));   // false
        System.out.println("Contains 400? " + numbers.contains(400));   // true
    }
}
```

**Output:**
```
Contains 500? false
Contains 400? true
```

**Explanation:**  
`500` is not in the list → returns `false`. `400` exists → returns `true`.

---

####   10. `indexOf()`

**Definition:**  
Returns the **index of the first occurrence** of the specified element. Returns `-1` if the element is not found.

**Syntax:**
```java
listName.indexOf(value);
```

**Use:**  
Used when you want to find **where** an element first appears in the list.

**Example Program:**
```java
import java.util.*;

public class IndexOfDemo {
    public static void main(String[] args) {
        List<Integer> numbers = new ArrayList<>();
        numbers.add(100);
        numbers.add(200);
        numbers.add(300);
        numbers.add(1400);
        numbers.add(1400);   // duplicate
        numbers.add(1500);
        numbers.add(1400);   // another duplicate

        System.out.println("First index of 1400 : " + numbers.indexOf(1400));
        System.out.println("First index of 500  : " + numbers.indexOf(500));
    }
}
```

**Output:**
```
First index of 1400 : 3
First index of 500  : -1
```

**Explanation:**  
`1400` appears first at index 3 → returns `3`. Even though `1400` appears 3 times, `indexOf()` only returns the **first** position. `500` doesn't exist → returns `-1`.

---

####   11. `lastIndexOf()`

**Definition:**  
Returns the **index of the last occurrence** of the specified element. Returns `-1` if not found.

**Syntax:**
```java
listName.lastIndexOf(value);
```

**Use:**  
Used when an element appears multiple times and you need its **last position**.

**Example Program:**
```java
import java.util.*;

public class LastIndexOfDemo {
    public static void main(String[] args) {
        List<Integer> numbers = new ArrayList<>();
        numbers.add(100);
        numbers.add(200);
        numbers.add(300);
        numbers.add(1400);   // index 3
        numbers.add(1400);   // index 4
        numbers.add(1500);
        numbers.add(1400);   // index 6

        System.out.println("Last index of 1400 : " + numbers.lastIndexOf(1400));
        System.out.println("Last index of 500  : " + numbers.lastIndexOf(500));
    }
}
```

**Output:**
```
Last index of 1400 : 6
Last index of 500  : -1
```

**Explanation:**  
`1400` appears at indexes 3, 4, and 6. `lastIndexOf()` returns the **last** position, which is `6`. `500` is not found → returns `-1`.

---

####   12. `clear()`

**Definition:**  
**Removes all elements** from the list. The list becomes empty but the list object still exists.

**Syntax:**
```java
listName.clear();
```

**Use:**  
Used to reset or empty a list completely, ready to be reused.

**Example Program:**
```java
import java.util.*;

public class ClearDemo {
    public static void main(String[] args) {
        List<Integer> numbers = new ArrayList<>();
        numbers.add(100);
        numbers.add(200);
        numbers.add(300);
        numbers.add(400);
        numbers.add(500);

        System.out.println("Before clear(): " + numbers);

        numbers.clear();

        System.out.println("After clear() : " + numbers);
        System.out.println("Size after clear: " + numbers.size());
    }
}
```

**Output:**
```
Before clear(): [100, 200, 300, 400, 500]
After clear() : []
Size after clear: 0
```

**Explanation:**  
`clear()` wipes all elements from the list. The list is now empty (`[]`) with size `0`. The list object `numbers` still exists and can be reused.

---

####   13. `removeAll()`

**Definition:**  
Removes **all elements** from the list that are also present in another collection.

**Syntax:**
```java
list1.removeAll(list2);   // Removes from list1 all elements that exist in list2
```

**Use:**  
Used to perform a **set difference** — keep only elements that are NOT in another list.

**Example Program:**
```java
import java.util.*;

public class RemoveAllDemo {
    public static void main(String[] args) {
        List<Integer> list1 = new ArrayList<>();
        list1.add(10);
        list1.add(20);
        list1.add(30);
        list1.add(40);
        System.out.println("Before removeAll(): " + list1);

        List<Integer> list2 = new ArrayList<>();
        list2.add(20);
        list2.add(30);

        list1.removeAll(list2);

        System.out.println("After removeAll() : " + list1);
    }
}
```

**Output:**
```
Before removeAll(): [10, 20, 30, 40]
After removeAll() : [10, 40]
```

**Explanation:**  
`list2` contains `[20, 30]`. `removeAll()` goes through `list1` and removes any element that matches a value in `list2`. So `20` and `30` are deleted, leaving `[10, 40]`.

---

####   14. `retainAll()`

**Definition:**  
Keeps **only the elements** that are also present in another collection. All other elements are removed.

**Syntax:**
```java
list1.retainAll(list2);   // Keeps in list1 only elements that exist in list2
```

**Use:**  
Used to find **common elements** between two lists (intersection).

**Example Program:**
```java
import java.util.*;

public class RetainAllDemo {
    public static void main(String[] args) {
        List<Integer> list1 = new ArrayList<>();
        list1.add(10);
        list1.add(20);
        list1.add(30);
        list1.add(40);
        System.out.println("Before retainAll(): " + list1);

        List<Integer> list2 = new ArrayList<>();
        list2.add(20);
        list2.add(30);

        list1.retainAll(list2);

        System.out.println("After retainAll() : " + list1);
    }
}
```

**Output:**
```
Before retainAll(): [10, 20, 30, 40]
After retainAll() : [20, 30]
```

**Explanation:**  
`list2` contains `[20, 30]`. `retainAll()` keeps only those elements in `list1` that also appear in `list2`. So `10` and `40` are removed, leaving `[20, 30]`.

---

####   15. `subList()`

**Definition:**  
Extracts a **portion** (sub-section) of the list between two indexes.

**Syntax:**
```java
listName.subList(fromIndex, toIndex);
```

>    `fromIndex` is **inclusive** (included), `toIndex` is **exclusive** (not included).

**Use:**  
Used when you need only a portion of a list, like pagination or slicing data.

**Example Program:**
```java
import java.util.*;

public class SubListDemo {
    public static void main(String[] args) {
        List<Integer> list1 = new ArrayList<>();
        list1.add(10);    // index 0
        list1.add(50);    // index 1
        list1.add(70);    // index 2
        list1.add(40);    // index 3
        list1.add(50);    // index 4
        list1.add(90);    // index 5
        list1.add(30);    // index 6
        list1.add(20);    // index 7

        List<Integer> sub = list1.subList(4, 8);

        System.out.println("Full List : " + list1);
        System.out.println("SubList   : " + sub);
    }
}
```

**Output:**
```
Full List : [10, 50, 70, 40, 50, 90, 30, 20]
SubList   : [50, 90, 30, 20]
```

**Explanation:**  
`subList(4, 8)` returns elements from index 4 (inclusive) to index 8 (exclusive). So elements at indexes 4, 5, 6, 7 → `[50, 90, 30, 20]`.

---

####  16. `toArray()`

**Definition:**  
Converts a **List** into an **Array**.

**Syntax:**
```java
Object[] arr = listName.toArray();
```

**Use:**  
Used when you need to pass list data to a method that only accepts arrays, or when working with APIs that require arrays.

**Example Program:**
```java
import java.util.*;

public class ToArrayDemo {
    public static void main(String[] args) {
        List<Integer> list1 = new ArrayList<>();
        list1.add(10);
        list1.add(50);
        list1.add(70);
        list1.add(40);
        list1.add(90);

        Object[] arr = list1.toArray();

        System.out.println("List to Array: " + Arrays.toString(arr));
    }
}
```

**Output:**
```
List to Array: [10, 50, 70, 40, 90]
```

**Explanation:**  
`toArray()` converts the `ArrayList` into an `Object[]` array. We use `Arrays.toString()` to print the array properly.

---

####  17. `sort()` / `Collections.sort()`

**Definition:**  
Sorts the elements of the list in **ascending (natural) order** by default.

**Syntax:**
```java
Collections.sort(listName);      // Sorts in ascending order
listName.sort(null);             // Same result using List's sort method
```

**Use:**  
Used whenever you need the list elements in sorted order.

**Example Program:**
```java
import java.util.*;

public class SortDemo {
    public static void main(String[] args) {
        List<Integer> list1 = new ArrayList<>();
        list1.add(10);
        list1.add(50);
        list1.add(70);
        list1.add(40);
        list1.add(50);
        list1.add(90);
        list1.add(30);
        list1.add(20);

        System.out.println("Before sort(): " + list1);

        Collections.sort(list1);

        System.out.println("After sort() : " + list1);
    }
}
```

**Output:**
```
Before sort(): [10, 50, 70, 40, 50, 90, 30, 20]
After sort() : [10, 20, 30, 40, 50, 50, 70, 90]
```

**Explanation:**  
`Collections.sort()` arranges all elements in ascending order. Duplicate values like `50` remain and are preserved in sorted position.

---

####  18. `replaceAll()`

**Definition:**  
Replaces **every element** in the list using a given expression or logic (Lambda Expression).

**Syntax:**
```java
listName.replaceAll(element -> expression);   // Lambda expression
```

**Use:**  
Used when you want to apply a transformation to every element — like doubling numbers, converting to uppercase, etc.

**Example Program:**
```java
import java.util.*;

public class ReplaceAllDemo {
    public static void main(String[] args) {
        List<Integer> list1 = new ArrayList<>();
        list1.add(10);
        list1.add(50);
        list1.add(70);
        list1.add(40);

        System.out.println("Before replaceAll(): " + list1);

        list1.replaceAll(n -> n * 2);   // Multiply every element by 2

        System.out.println("After replaceAll() : " + list1);
    }
}
```

**Output:**
```
Before replaceAll(): [10, 50, 70, 40]
After replaceAll() : [20, 100, 140, 80]
```

**Explanation:**  
`replaceAll(n -> n * 2)` is a **Lambda Expression** that takes each element `n` and replaces it with `n * 2`. Every element in the list is doubled in place.

---

###  Quick Reference — List Methods Summary

| Method | Purpose | Returns |
|---|---|---|
| `add(value)` | Add at end | — |
| `add(index, value)` | Insert at position | — |
| `addAll(list)` | Add all from another list | `boolean` |
| `get(index)` | Read element at index | `element` |
| `set(index, value)` | Update element at index | old value |
| `remove(index)` | Delete by position | removed element |
| `remove(Object)` | Delete by value | `boolean` |
| `size()` | Count elements | `int` |
| `isEmpty()` | Check if empty | `boolean` |
| `contains(value)` | Check if value exists | `boolean` |
| `indexOf(value)` | First position of value | `int` |
| `lastIndexOf(value)` | Last position of value | `int` |
| `clear()` | Remove all elements | — |
| `removeAll(list)` | Remove matched elements | `boolean` |
| `retainAll(list)` | Keep only matched elements | `boolean` |
| `subList(from, to)` | Get portion of list | `List` |
| `toArray()` | Convert to array | `Object[]` |
| `sort()` | Sort in ascending order | — |
| `replaceAll(lambda)` | Transform all elements | — |

---

## 4. Set Interface

### What is a Set?

A **Set** is a collection that:

-  Does **NOT allow duplicate** values
-  Allows **at most one null** (in `HashSet` and `LinkedHashSet`)
-  `TreeSet` does **NOT allow null**
-  Elements are **NOT accessible by index**
-  Best used when you need **unique values only**

```
Set = {10, 20, 30, 40}
// If you try to add 20 again → it is IGNORED
```

>  **Key Difference from List:**  
> List allows `[10, 20, 20, 30]` but Set only stores `{10, 20, 30}` — duplicates are silently ignored.

---

### Types of Set

| Type | Class | Order | Null | Performance | Underlying Structure |
|---|---|---|---|---|---|
| Hash-based | `HashSet` | **No order** (random) | One null allowed | Fastest | Hash Table |
| Linked Hash | `LinkedHashSet` | **Insertion order** | One null allowed | Slightly slower | Hash Table + Linked List |
| Tree-based | `TreeSet` | **Sorted order** |  No null | Slowest | Red-Black Tree |

---

### Creating a Set

```java
import java.util.*;

// HashSet — no guaranteed order
Set<Integer> set1 = new HashSet<>();
HashSet<Integer> set2 = new HashSet<>();
HashSet<Integer> set3 = new HashSet<>(10);   // initial capacity of 10

// LinkedHashSet — maintains insertion order
LinkedHashSet<String> lhs = new LinkedHashSet<>();
Set<String> lhs2 = new LinkedHashSet<>();

// TreeSet — maintains sorted order
TreeSet<Integer> treeSet = new TreeSet<>();
Set<Integer> treeSet2 = new TreeSet<>();
```

**Full Example:**
```java
import java.util.*;

public class SetCreationDemo {
    public static void main(String[] args) {

        // HashSet — random order
        HashSet<Integer> set = new HashSet<>();
        set.add(10);
        set.add(20);
        set.add(30);
        set.add(40);
        System.out.println("HashSet       : " + set);   // order not guaranteed

        // LinkedHashSet — insertion order
        LinkedHashSet<String> lhs = new LinkedHashSet<>();
        lhs.add("Andra");
        lhs.add("Karnataka");
        lhs.add("Tamilnadu");
        System.out.println("LinkedHashSet : " + lhs);   // insertion order maintained

        // TreeSet — sorted order
        TreeSet<Integer> treeSet = new TreeSet<>();
        treeSet.add(20);
        treeSet.add(10);
        treeSet.add(50);
        treeSet.add(8);
        treeSet.add(11);
        System.out.println("TreeSet       : " + treeSet);   // always sorted
    }
}
```

**Output:**
```
HashSet       : [20, 40, 10, 30]     ← random (may vary each run)
LinkedHashSet : [Andra, Karnataka, Tamilnadu]
TreeSet       : [8, 10, 11, 20, 50]
```

---

### Set Methods

---

####  1. `add()`

**Definition:**  
Adds an element to the set. If the element **already exists**, it is **ignored** (no error, no duplicate stored).

**Syntax:**
```java
set.add(element);
```

**Use:**  
Used to insert unique values into the set.

**Example Program:**
```java
import java.util.*;

public class SetAddDemo {
    public static void main(String[] args) {
        Set<Integer> set = new HashSet<>();
        set.add(10);
        set.add(20);
        set.add(30);
        set.add(20);   // duplicate — will be ignored

        System.out.println("Set: " + set);
        System.out.println("Size: " + set.size());   // Still 3, not 4
    }
}
```

**Output:**
```
Set: [20, 10, 30]
Size: 3
```

**Explanation:**  
`add(20)` is called twice but the set only stores it once. The duplicate `20` is automatically ignored. Size remains 3.

---

####  2. `addAll()`

**Definition:**  
Adds **all elements** from one collection (Set or List) into another set. Duplicates are still ignored.

**Syntax:**
```java
set1.addAll(set2);    // Adds all elements of set2 into set1
```

**Use:**  
Used to combine two sets (union operation).

**Example Program:**
```java
import java.util.*;

public class SetAddAllDemo {
    public static void main(String[] args) {
        Set<Integer> set1 = new HashSet<>();
        set1.add(1);
        set1.add(2);
        set1.add(3);
        System.out.println("Set1 before addAll: " + set1);

        Set<Integer> set2 = new HashSet<>();
        set2.add(4);
        set2.add(5);
        set2.add(3);   // duplicate — will be ignored
        System.out.println("Set2              : " + set2);

        set1.addAll(set2);

        System.out.println("Set1 after addAll : " + set1);
    }
}
```

**Output:**
```
Set1 before addAll: [1, 2, 3]
Set2              : [3, 4, 5]
Set1 after addAll : [1, 2, 3, 4, 5]
```

**Explanation:**  
All elements from `set2` are merged into `set1`. The duplicate `3` is ignored since it already exists. Result is the **union** of both sets.

---

####  3. `remove()`

**Definition:**  
Removes the specified element from the set if it exists. Returns `true` if removed, `false` if not found.

**Syntax:**
```java
set.remove(element);
```

**Use:**  
Used to delete a specific value from the set.

**Example Program:**
```java
import java.util.*;

public class SetRemoveDemo {
    public static void main(String[] args) {
        Set<String> names = new HashSet<>();
        names.add("Aradhana");
        names.add("Maha");
        System.out.println("Set: " + names);

        System.out.println("Removing 'Maha' : " + names.remove("Maha"));   // true
        System.out.println("Set after remove: " + names);

        System.out.println("Removing 'Arya' : " + names.remove("Arya"));   // false (doesn't exist)
        System.out.println("Set after remove: " + names);
    }
}
```

**Output:**
```
Set: [Aradhana, Maha]
Removing 'Maha' : true
Set after remove: [Aradhana]
Removing 'Arya' : false
Set after remove: [Aradhana]
```

**Explanation:**  
`remove("Maha")` finds `"Maha"` and deletes it → returns `true`. `remove("Arya")` doesn't find it → returns `false`, set unchanged.

---

####  4. `removeAll()`

**Definition:**  
Removes from the set **all elements** that are also present in another collection. (Set Difference)

**Syntax:**
```java
set1.removeAll(set2);   // Removes from set1 all values found in set2
```

**Use:**  
Used to find elements in one set that are **not** in another (set difference operation).

**Example Program:**
```java
import java.util.*;

public class SetRemoveAllDemo {
    public static void main(String[] args) {
        Set<Integer> set1 = new HashSet<>(Arrays.asList(1, 2, 3, 4));
        Set<Integer> set2 = new HashSet<>(Arrays.asList(3, 4));

        System.out.println("Before removeAll(): " + set1);

        set1.removeAll(set2);

        System.out.println("After removeAll() : " + set1);
    }
}
```

**Output:**
```
Before removeAll(): [1, 2, 3, 4]
After removeAll() : [1, 2]
```

**Explanation:**  
`set2` contains `{3, 4}`. `removeAll()` deletes `3` and `4` from `set1`. Only `{1, 2}` remain.

---

####  5. `retainAll()`

**Definition:**  
Keeps **only** the elements in the set that are also present in another collection. All others are removed. (Set Intersection)

**Syntax:**
```java
set1.retainAll(set2);   // Keeps in set1 only values found in set2
```

**Use:**  
Used to find **common elements** between two sets (intersection operation).

**Example Program:**
```java
import java.util.*;

public class SetRetainAllDemo {
    public static void main(String[] args) {
        Set<Integer> set1 = new HashSet<>(Arrays.asList(1, 2, 3, 4));
        Set<Integer> set2 = new HashSet<>(Arrays.asList(3, 4));

        System.out.println("Before retainAll(): " + set1);

        set1.retainAll(set2);

        System.out.println("After retainAll() : " + set1);
    }
}
```

**Output:**
```
Before retainAll(): [1, 2, 3, 4]
After retainAll() : [3, 4]
```

**Explanation:**  
Only `3` and `4` exist in both `set1` and `set2`. `retainAll()` removes everything else (`1` and `2`), leaving only the common elements `{3, 4}`.

---

####  6. `contains()`

**Definition:**  
Checks if a specific element **exists** in the set. Returns `true` or `false`.

**Syntax:**
```java
set.contains(value);
```

**Use:**  
Used to verify the presence of an element before operations.

**Example Program:**
```java
import java.util.*;

public class SetContainsDemo {
    public static void main(String[] args) {
        Set<String> cities = new HashSet<>();
        cities.add("Hyderabad");
        cities.add("Bangalore");
        cities.add("Chennai");

        System.out.println("Contains 'Bangalore'? " + cities.contains("Bangalore"));   // true
        System.out.println("Contains 'Mumbai'?    " + cities.contains("Mumbai"));       // false
    }
}
```

**Output:**
```
Contains 'Bangalore'? true
Contains 'Mumbai'?    false
```

**Explanation:**  
`"Bangalore"` is in the set → `true`. `"Mumbai"` is not → `false`.

---

####   7. `size()`

**Definition:**  
Returns the **number of unique elements** in the set.

**Syntax:**
```java
set.size();
```

**Example Program:**
```java
import java.util.*;

public class SetSizeDemo {
    public static void main(String[] args) {
        Set<Integer> set = new HashSet<>();
        set.add(10);
        set.add(20);
        set.add(30);
        set.add(20);   // duplicate — ignored
        set.add(10);   // duplicate — ignored

        System.out.println("Set  : " + set);
        System.out.println("Size : " + set.size());   // 3, not 5
    }
}
```

**Output:**
```
Set  : [20, 10, 30]
Size : 3
```

**Explanation:**  
Even though `add()` is called 5 times, only 3 unique values are stored. `size()` returns `3`.

---

####   8. `isEmpty()`

**Definition:**  
Returns `true` if the set has **no elements**, `false` otherwise.

**Syntax:**
```java
set.isEmpty();
```

**Example Program:**
```java
import java.util.*;

public class SetIsEmptyDemo {
    public static void main(String[] args) {
        Set<String> set = new HashSet<>();

        System.out.println("Is empty (before add): " + set.isEmpty());   // true

        set.add("Java");
        set.add("Python");

        System.out.println("Is empty (after add) : " + set.isEmpty());   // false
    }
}
```

**Output:**
```
Is empty (before add): true
Is empty (after add) : false
```

---

####   9. `clear()`

**Definition:**  
**Removes all elements** from the set. Set becomes empty but the object still exists.

**Syntax:**
```java
set.clear();
```

**Example Program:**
```java
import java.util.*;

public class SetClearDemo {
    public static void main(String[] args) {
        Set<Integer> set = new HashSet<>(Arrays.asList(1, 2, 3, 4, 5));

        System.out.println("Before clear(): " + set);
        System.out.println("Size          : " + set.size());

        set.clear();

        System.out.println("After clear() : " + set);
        System.out.println("Size          : " + set.size());
    }
}
```

**Output:**
```
Before clear(): [1, 2, 3, 4, 5]
Size          : 5
After clear() : []
Size          : 0
```

---

###  Set Types Comparison Summary

| Feature | HashSet | LinkedHashSet | TreeSet |
|---|---|---|---|
| Order |  No order |  Insertion order |  Sorted order |
| Duplicates |  No |  No |  No |
| Null value |  One null |  One null |  No null |
| Speed |  Fastest |  Medium |  Slowest |
| Use case | Fast lookup | Ordered uniqueness | Sorted uniqueness |

---

###  Set Operations — Visual Summary

```
set1 = {1, 2, 3, 4}
set2 = {3, 4, 5}

addAll()     → Union        → {1, 2, 3, 4, 5}
retainAll()  → Intersection → {3, 4}
removeAll()  → Difference   → {1, 2}
```

---

###  Quick Reference — Set Methods Summary

| Method | Purpose | Returns |
|---|---|---|
| `add(element)` | Add unique element | `boolean` |
| `addAll(collection)` | Add all from collection | `boolean` |
| `remove(element)` | Remove specific element | `boolean` |
| `removeAll(set)` | Remove all matching elements | `boolean` |
| `retainAll(set)` | Keep only matching elements | `boolean` |
| `contains(value)` | Check if element exists | `boolean` |
| `size()` | Count of unique elements | `int` |
| `isEmpty()` | Check if set is empty | `boolean` |
| `clear()` | Remove all elements | — |

---

##  Key Differences: List vs Set

| Feature | List | Set |
|---|---|---|
| Duplicates |  Allowed |  Not allowed |
| Order |  Insertion order maintained | Depends on type |
| Index access |  Yes (`get(index)`) |  No index |
| Null values |  Multiple nulls allowed | At most one null |
| Use case | Ordered sequences | Unique collections |
| Main classes | `ArrayList`, `LinkedList` | `HashSet`, `LinkedHashSet`, `TreeSet` |

---

>  **Next Topics to Cover:**
> - Map Interface (HashMap, LinkedHashMap, TreeMap)
> - Queue Interface (PriorityQueue, Deque)
> - Iterator and for-each with Collections
> - Collections utility class methods

---

*Notes prepared for Java students — Java Collection Framework (JCF)*
