
# JSP Introduction

## Objectives
By the end of this class, students should be able to:
- Explain what JSP is and why it exists
- Compare JSP with Servlets
- Understand the JSP life cycle
- Write and run their first JSP program
- Identify and use the four JSP scripting elements
- Understand the difference between declarations and scriptlets
- Write JSP pages using directives, declarations, scriptlets, and expressions together

## 1. What is JSP?
- JSP (JavaServer Pages) is a server-side technology used to create dynamic, platform-independent web pages.
- It allows embedding Java code inside HTML using special tags.
- JSP is built **on top of Servlet technology** - every JSP page is internally converted into a servlet by the container (Tomcat).

## 2. Why JSP? (Problem with Servlets)
- In Servlets, HTML is written inside Java code using `out.println()` - messy and hard to maintain for UI-heavy pages.
- JSP flips this: Java code is embedded inside HTML - easier for designing the view/presentation layer.
- Separation of concerns: Servlet = logic (Controller), JSP = presentation (View) → foundation for MVC (covered later in course).

## 3. JSP vs Servlet (Quick Comparison)

| Aspect | Servlet | JSP |
|---|---|---|
| Nature | Java code with embedded HTML | HTML with embedded Java |
| Use case | Business logic / Controller | Presentation / View |
| Compilation | Compiled by developer | Auto-converted to servlet & compiled by container |
| Ease of UI design | Difficult | Easy |

## 4. JSP Life Cycle
1. **Translation** - JSP file is translated into a Servlet (`.java`) by the container.
2. **Compilation** - The generated servlet is compiled into a `.class` file.
3. **Class Loading** - Servlet class is loaded into memory.
4. **Instantiation** - Object of the servlet is created.
5. **Initialization** - `jspInit()` is called (once).
6. **Request Processing** - `_jspService()` is called for every request.
7. **Destroy** - `jspDestroy()` is called when the container shuts down/unloads the JSP.


## 5. Setting Up a JSP Project
- Use the same Dynamic Web Project / Maven webapp structure used earlier in the course (you already know this from Servlets).
- JSP files go inside `webapp` (or `WebContent`) folder - **not** inside `WEB-INF` (else it can't be accessed directly via browser).
- Server: Apache Tomcat (already configured from Servlet classes).

## 6. First JSP Program

**hello.jsp**
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<html>
<head><title>My First JSP</title></head>
<body>
    <h2>Hello from JSP!</h2>
    <%
        String name = "JFS Batch 2";
        out.println("Welcome, " + name);
    %>
</body>
</html>
```

- Deploy on Tomcat, run `http://localhost:8080/<project>/hello.jsp`

#  JSP Scripting Elements

## 7. What are Scripting Elements?
- Scripting elements are the tags that let us insert Java code into a JSP page.
- Four types:
  1. Directives
  2. Declarations
  3. Scriptlets
  4. Expressions

## 8. Directives - `<%@ %>`
- Give instructions to the container about the page itself (not executed per request, just configuration).
- Three types:

| Directive | Purpose | Example |
|---|---|---|
| `page` | Page-level settings (import, content type, error page) | `<%@ page import="java.util.*" %>` |
| `include` | Static include of another file at translation time | `<%@ include file="header.jsp" %>` |
| `taglib` | Declare a tag library (used later with JSTL) | `<%@ taglib uri="..." prefix="c" %>` |

- Focus mainly on `page` directive today - `taglib` will be revisited on (JSTL).

## 9. Declarations - `<%! %>`
- Used to declare **variables and methods** at the class level (outside `_jspService()`).
- Memory allocated once - shared across all requests (like instance variables of the generated servlet).

```jsp
<%!
    int counter = 0;
    int incrementCounter() {
        return ++counter;
    }
%>
```


## 10. Scriptlets - `<% %>`
- Used to write **Java code blocks** that go inside `_jspService()` - executed on every request.
- Local variables, loops, conditions, etc.

```jsp
<%
    int a = 10, b = 20;
    int sum = a + b;
%>
<p>Sum is: <%= sum %></p>
```

- Can mix with HTML:
```jsp
<%
    for (int i = 1; i <= 5; i++) {
%>
    <p>Row <%= i %></p>
<%
    }
%>
```

## 11. Expressions - `<%= %>`
- Used to directly print a value to the output - shorthand for `out.print(...)`.
- No semicolon at the end.

```jsp
<p>Today's date: <%= new java.util.Date() %></p>
```

## 12. Declarations vs Scriptlets - Key Difference (Important, students often confuse this)

| Aspect | Declaration `<%! %>` | Scriptlet `<% %>` |
|---|---|---|
| Where it goes in generated servlet | Class level (outside methods) | Inside `_jspService()` method |
| Executed | Once (per variable/method definition) | On every request |
| Can declare methods? | Yes | No |
| Thread safety | Not thread-safe (shared) | Thread-safe (local to each request) |

## 13. Putting It All Together - Example

```jsp
<%@ page import="java.util.Date" %>
<html>
<body>
<%! int visitCount = 0; %>
<%
    visitCount++;
%>
<h3>Welcome!</h3>
<p>Current time: <%= new Date() %></p>
<p>You are visitor number: <%= visitCount %></p>
</body>
</html>
```
- Run this and refresh the browser a few times - students will see `visitCount` increasing, which nicely demonstrates the declaration's shared/class-level nature.

## 14. In-Class Activity
  - Displays their name and today's date using `<% %>` scriptlet
  - Prints "Welcome to JSP" using `<%= %>` expression
  - `page` directive to import `java.util.*`
  - A declaration for a method `isEven(int n)`
  - A scriptlet loop printing numbers 1–10
  - An expression that prints "Even" or "Odd" next to each number using the declared method

## 15. Recap Questions 

1. What is the first phase of the JSP life cycle?
2. Why is JSP considered better than Servlets for the view layer?
3. Where should `.jsp` files be placed in a project?
4. Which scripting element executes only once, regardless of how many requests come in?
5. Why can't we declare a method inside a scriptlet?
6. What is the shorthand tag for printing a value directly in JSP?

---
