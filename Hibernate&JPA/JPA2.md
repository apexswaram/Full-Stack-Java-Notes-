# Day 2 — JSP Scripting Elements

## Objectives
By the end of this class, students should be able to:
- Identify and use the four JSP scripting elements
- Understand the difference between declarations and scriptlets
- Write JSP pages using directives, declarations, scriptlets, and expressions together

## Quick Recap of Day 1
- JSP = HTML + embedded Java, converted to a servlet by the container
- Life cycle: Translation → Compilation → Init → Service → Destroy
- Ask 2–3 students the recap questions from Day 1 before moving on

## 1. What are Scripting Elements?
- Scripting elements are the tags that let us insert Java code into a JSP page.
- Four types:
  1. Directives
  2. Declarations
  3. Scriptlets
  4. Expressions

## 2. Directives — `<%@ %>`
- Give instructions to the container about the page itself (not executed per request, just configuration).
- Three types:

| Directive | Purpose | Example |
|---|---|---|
| `page` | Page-level settings (import, content type, error page) | `<%@ page import="java.util.*" %>` |
| `include` | Static include of another file at translation time | `<%@ include file="header.jsp" %>` |
| `taglib` | Declare a tag library (used later with JSTL) | `<%@ taglib uri="..." prefix="c" %>` |

- Focus mainly on `page` directive today — `taglib` will be revisited on Day 4 (JSTL).

## 3. Declarations — `<%! %>`
- Used to declare **variables and methods** at the class level (outside `_jspService()`).
- Memory allocated once — shared across all requests (like instance variables of the generated servlet).

```jsp
<%!
    int counter = 0;
    int incrementCounter() {
        return ++counter;
    }
%>
```

- Important teaching point: declarations are NOT thread-safe since they're shared across requests — good moment to mention why we avoid heavy logic here.

## 4. Scriptlets — `<% %>`
- Used to write **Java code blocks** that go inside `_jspService()` — executed on every request.
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

## 5. Expressions — `<%= %>`
- Used to directly print a value to the output — shorthand for `out.print(...)`.
- No semicolon at the end.

```jsp
<p>Today's date: <%= new java.util.Date() %></p>
```

## 6. Declarations vs Scriptlets — Key Difference (Important, students often confuse this)

| Aspect | Declaration `<%! %>` | Scriptlet `<% %>` |
|---|---|---|
| Where it goes in generated servlet | Class level (outside methods) | Inside `_jspService()` method |
| Executed | Once (per variable/method definition) | On every request |
| Can declare methods? | Yes | No |
| Thread safety | Not thread-safe (shared) | Thread-safe (local to each request) |

## 7. Putting It All Together — Example

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
- Run this and refresh the browser a few times — students will see `visitCount` increasing, which nicely demonstrates the declaration's shared/class-level nature.

## 8. In-Class Activity
- Ask students to build a JSP page using all four elements:
  - `page` directive to import `java.util.*`
  - A declaration for a method `isEven(int n)`
  - A scriptlet loop printing numbers 1–10
  - An expression that prints "Even" or "Odd" next to each number using the declared method

## 9. Recap Questions (End of Class)
1. Which scripting element executes only once, regardless of how many requests come in?
2. Why can't we declare a method inside a scriptlet?
3. What is the shorthand tag for printing a value directly in JSP?

## 10. Homework
- Read about JSP implicit objects (`request`, `response`, `session`, `out`, `application`) — covered Day 3.
- Modify the visitor-count example to also print whether the visit count is odd or even, using the method from the in-class activity.

---
*Prepared for JFS Batch 2 — Day 2 of 15 (JSP & Hibernate Module)*
