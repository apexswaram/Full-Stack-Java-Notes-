
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
# Expression Language (EL) & JSTL Core Tags

## Objectives
By the end of this class, students should be able to:
- Explain why EL and JSTL exist and what problem they solve
- Read and write EL expressions to access data from different scopes
- Use the most important JSTL core tags with full working examples


## 1. Why EL and JSTL? (The Problem We're Solving)

So far, every dynamic value we printed used scriptlets (`<% %>`) and expressions (`<%= %>`) — this means **raw Java code mixed inside HTML**. This is exactly the problem JSP was meant to solve compared to Servlets, but scriptlets bring the same mess back in a smaller form.

**Bad practice (what we've been doing so far):**
```jsp
<%
    String uname = (String) session.getAttribute("user");
%>
<p>Welcome, <%= uname %></p>
```

**Better practice (what we learn today):**
```jsp
<p>Welcome, ${sessionScope.user}</p>
```

- **EL (Expression Language)** — a simple syntax `${ }` to access data without loss Java code.
- **JSTL (JSP Standard Tag Library)** — ready-made tags (`c:if`, `c:forEach`, etc.) that replace `if`, `for`, loops written in scriptlets.

Together, EL + JSTL let us write JSP pages with **zero scriptlets** — this is considered the correct, professional way to write JSP in real projects (scriptlets are now considered bad practice in the industry).

---

## 2. Expression Language (EL) Basics

### 2.1 Syntax
```
${ expression }
```

### 2.2 Accessing Scoped Data — Full Example

`setData.jsp`
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<%
    request.setAttribute("course", "Java Full Stack");
    session.setAttribute("studentName", "Ravi Kumar");
    application.setAttribute("collegeName", "ApexSwaram Institute");
%>
<html>
<body>
    <a href="showData.jsp">View Data using EL</a>
</body>
</html>
```

`showData.jsp`
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<html>
<body>
    <h3>Course: ${requestScope.course}</h3>
    <h3>Student: ${sessionScope.studentName}</h3>
    <h3>College: ${applicationScope.collegeName}</h3>
</body>
</html>
```

**Explanation:**
- `${requestScope.course}` reads the `course` attribute directly from `request` — no need for `request.getAttribute("course")` + typecasting.
- Similarly `sessionScope` and `applicationScope` map directly to the `session` and `application` objects from Day 3.
- **Important gotcha to mention:** `request.setAttribute()` only lives for that one request. If a user directly opens `showData.jsp` in a new tab (a fresh request), `${requestScope.course}` will be empty — but `${sessionScope.studentName}` will still work because session data persists. This is a great moment to reinforce the scope hierarchy from last class.
- If you don't specify a scope prefix, EL automatically searches **page → request → session → application** in that order. Example: `${studentName}` (without `sessionScope.`) would still work here.

### 2.3 EL with Request Parameters — Full Example

`searchForm.jsp`
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<html>
<body>
    <form action="searchResult.jsp" method="get">
        Enter roll number: <input type="text" name="rollNo">
        <input type="submit" value="Search">
    </form>
</body>
</html>
```

`searchResult.jsp`
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<html>
<body>
    <h3>You searched for roll number: ${param.rollNo}</h3>
</body>
</html>
```

**Explanation:**
- `${param.rollNo}` is EL's shortcut for `request.getParameter("rollNo")` — no scriptlet, no typecasting, much shorter.
- This is the EL equivalent of the `request.getParameter()` pattern we used heavily on Day 3.

### 2.4 EL Operators — Full Example

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<%
    request.setAttribute("marks", 78);
%>
<html>
<body>
    <p>Marks: ${marks}</p>
    <p>Marks + 5 bonus: ${marks + 5}</p>
    <p>Is pass (marks >= 35)? ${marks >= 35}</p>
    <p>Grade check: ${marks >= 75 ? "Distinction" : "Pass"}</p>
</body>
</html>
```

**Explanation:**
- EL supports arithmetic (`+ - * /`), relational (`>= <= == !=`), logical (`&& || !`), and the ternary operator `? :` — all without a single scriptlet.
- This alone replaces a huge number of scriptlet `if` blocks we'd otherwise write.

---

## 3. JSTL — Setup First

Before using JSTL tags, we must declare the `taglib` directive (introduced briefly on Day 3):

```jsp
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
```

**Setup note :** the JSTL library JAR (`jstl-1.2.jar` or the Jakarta equivalent depending on server version) must be present in `WEB-INF/lib`. Confirm this is already added to the project (should be, since we set up the project structure earlier in the course).

---

## 4. JSTL Core Tags

### 4.1 `<c:out>` — Safe Printing

```jsp
<c:out value="${sessionScope.studentName}" default="Guest"/>
```

**Explanation:**
- Similar to `${ }` but safer — escapes special HTML characters (prevents basic HTML/script injection) and supports a `default` value if the expression is null. Prefer `<c:out>` over raw `${ }` when printing user-submitted data.

### 4.2 `<c:if>` — Conditional Logic — Full Example

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<%
    request.setAttribute("marks", 42);
%>
<html>
<body>
    <c:if test="${marks >= 35}">
        <p>Result: PASS</p>
    </c:if>
    <c:if test="${marks < 35}">
        <p>Result: FAIL</p>
    </c:if>
</body>
</html>
```

**Explanation:**
- `<c:if test="condition">` replaces a scriptlet `if` block. The `test` attribute takes an EL boolean expression.
- **Important limitation to point out:** `<c:if>` has **no else** — that's why we wrote it twice with the opposite condition. For proper if-else, we use `<c:choose>` next.

### 4.3 `<c:choose>`, `<c:when>`, `<c:otherwise>` — If-Else Logic — Full Example

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<%
    request.setAttribute("marks", 68);
%>
<html>
<body>
    <c:choose>
        <c:when test="${marks >= 75}">
            <p>Grade: Distinction</p>
        </c:when>
        <c:when test="${marks >= 60}">
            <p>Grade: First Class</p>
        </c:when>
        <c:when test="${marks >= 35}">
            <p>Grade: Pass</p>
        </c:when>
        <c:otherwise>
            <p>Grade: Fail</p>
        </c:otherwise>
    </c:choose>
</body>
</html>
```

**Explanation:**
- `<c:choose>` is the JSTL equivalent of `if-else if-else` in Java.
- Each `<c:when>` is checked top to bottom — the first one that matches runs, rest are skipped (like a switch/if-else chain).
- `<c:otherwise>` runs only if none of the `<c:when>` conditions matched — equivalent to the final `else`.

### 4.4 `<c:forEach>` — Loops — Full Example

**Simple counting loop:**
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<html>
<body>
    <h3>Multiplication Table of 5</h3>
    <c:forEach var="i" begin="1" end="10">
        <p>5 x ${i} = ${5 * i}</p>
    </c:forEach>
</body>
</html>
```

**Looping over a Java collection (very commonly used in real projects):**

```jsp
<%@ page import="java.util.*" %>
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<%
    List<String> students = new ArrayList<>();
    students.add("Ravi Kumar");
    students.add("Priya Sharma");
    students.add("Anil Reddy");
    request.setAttribute("studentList", students);
%>
<html>
<body>
    <h3>Student List</h3>
    <ul>
        <c:forEach var="student" items="${studentList}">
            <li>${student}</li>
        </c:forEach>
    </ul>
</body>
</html>
```

**Explanation:**
- `begin`/`end` version: like a Java `for (int i = 1; i <= 10; i++)` loop — good for counters, tables, pagination-style numbering.
- `items` version: loops over a `List`/array/`Map` stored in any scope — `var="student"` becomes the loop variable for each item, very similar to Java's enhanced for-loop (`for (String student : studentList)`).

### 4.5 `<c:set>` and `<c:remove>` — Working with Variables

```jsp
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<c:set var="collegeName" value="ApexSwaram Institute" scope="session"/>
<p>College: ${sessionScope.collegeName}</p>
<c:remove var="collegeName" scope="session"/>
```

**Explanation:**
- `<c:set>` is the JSTL way of doing `session.setAttribute()` — set `var`, `value`, and optionally `scope` (`page`, `request`, `session`, `application`; defaults to `page` if omitted).
- `<c:remove>` deletes the attribute — JSTL equivalent of `session.removeAttribute()`.

---


# Form Handling, Forward vs Redirect, Session Tracking

## 1. Form Handling — GET vs POST Recap

you already know `request.getParameter()` from Day 3 and `${param.x}` from Day 4. Today we formalize **when to use GET vs POST** and build a complete registration form using JSTL/EL style (industry-preferred, no scriptlets).

| Aspect | GET | POST |
|---|---|---|
| Data visibility | Appended to URL (visible, bookmarkable) | Sent in request body (hidden) |
| Data size limit | Limited (URL length restriction) | Large data allowed |
| Use case | Search, filters, navigation | Login, registration, forms with sensitive/large data |
| Idempotent | Yes (safe to repeat/cache) | No (submitting again may repeat an action) |

### 1.1 Full Registration Form Example

`registerForm.jsp`
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<html>
<body>
    <h2>Student Registration</h2>
    <form action="registerProcess.jsp" method="post">
        Name: <input type="text" name="name" required><br><br>
        Email: <input type="text" name="email" required><br><br>
        Course:
        <select name="course">
            <option value="Java Full Stack">Java Full Stack</option>
            <option value="Python Full Stack">Python Full Stack</option>
            <option value="Data Analytics">Data Analytics</option>
        </select><br><br>
        <input type="submit" value="Register">
    </form>
</body>
</html>
```

`registerProcess.jsp`
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<html>
<body>
    <h2>Registration Successful</h2>
    <p>Name: ${param.name}</p>
    <p>Email: ${param.email}</p>
    <p>Course: ${param.course}</p>

    <c:if test="${param.course == 'Java Full Stack'}">
        <p>Great choice! Classes start Monday 10 AM.</p>
    </c:if>
</body>
</html>
```

**Explanation:**
- `method="post"` is used because registration data shouldn't sit in the URL.
- `${param.name}`, `${param.email}`, `${param.course}` directly read the submitted form fields — no scriptlet, no `request.getParameter()` needed (though it works identically underneath).
- The `<c:if>` shows we can combine form data with JSTL conditional logic immediately, tying together Day 4's lesson with real form data.

---

## 2. Forward vs Redirect — The Most Important Concept Today

This is a favorite interview question — spend real time here with the browser open, showing the URL bar change (or not).

### 2.1 Conceptual Difference

| Aspect | Forward | Redirect |
|---|---|---|
| Where it happens | Server-side | Client-side (browser makes a new request) |
| URL in browser | Stays the same | Changes to the new page's URL |
| Request object | Same request object continues | New request object (data lost unless stored elsewhere) |
| Speed | Faster (one round trip) | Slower (two round trips: server tells browser → browser requests again) |
| Can forward/redirect to | Only within the same application | Any URL, even external sites |
| How to do it | `RequestDispatcher` | `response.sendRedirect()` |

### 2.2 Forward — Full Example (using `<jsp:forward>` action tag)

`checkMarks.jsp`
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<%
    request.setAttribute("marks", 42);
%>
<jsp:forward page="resultPage.jsp"/>
```

`resultPage.jsp`
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<html>
<body>
    <h2>Your marks: ${requestScope.marks}</h2>
</body>
</html>
```

**Explanation:**
- `<jsp:forward page="resultPage.jsp"/>` is a JSP **action tag** — it hands off processing to `resultPage.jsp` entirely on the server. The browser never even knows `resultPage.jsp` was involved — the URL bar still shows `checkMarks.jsp`.
- Because it's the **same request**, `${requestScope.marks}` set in `checkMarks.jsp` is still available in `resultPage.jsp` — this is the key reason forward is used so often for passing data between pages (we used `request.setAttribute()` this same way back on Day 3, now paired with an actual forward).
- Run this in class and point at the browser's URL bar — it will NOT change to `resultPage.jsp`.

### 2.3 Redirect — Full Example

`checkMarksRedirect.jsp`
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<%
    response.sendRedirect("resultPageRedirect.jsp?marks=42");
%>
```

`resultPageRedirect.jsp`
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<html>
<body>
    <h2>Your marks: ${param.marks}</h2>
</body>
</html>
```

**Explanation:**
- `response.sendRedirect(...)` tells the **browser** "go request this other URL" — the browser then makes a brand-new request.
- Because it's a new request, the old `request` object (and anything set with `request.setAttribute()`) is gone — that's why we had to pass `marks` as a **query parameter** in the URL instead, and read it with `${param.marks}` on the other side.
- Run this in class and point at the browser's URL bar — it WILL change to `resultPageRedirect.jsp?marks=42`, visibly proving it's a fresh request.
- Mention: redirect can go to any external URL too, e.g. `response.sendRedirect("https://www.google.com")` — forward cannot do this.

### 2.4 When to Use Which (Practical Rule of Thumb)
- **Forward** → when moving internally within the app and you want to preserve request data (e.g., Servlet processes form data, then forwards to a JSP to display results).
- **Redirect** → after a form submission that changes data (like login, registration, or a purchase) — this prevents the classic "resubmit form on refresh" problem, since refreshing after a redirect just re-requests the new page, not re-submits the form.

---

## 3. Session Tracking — Full Login/Logout Flow

We used `session.setAttribute()`/`getAttribute()` briefly on Day 3. Today we build the **complete flow**: login → protected page → logout, which is the realistic pattern used in almost every project.

### 3.1 `login.jsp` — The Form

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<html>
<body>
    <h2>Login</h2>
    <form action="loginProcess.jsp" method="post">
        Username: <input type="text" name="username"><br><br>
        Password: <input type="password" name="password"><br><br>
        <input type="submit" value="Login">
    </form>
</body>
</html>
```

### 3.2 `loginProcess.jsp` — Validate and Create Session

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<%
    String uname = request.getParameter("username");
    String pass = request.getParameter("password");

    if (uname != null && uname.equals("admin") && pass.equals("admin123")) {
        session.setAttribute("loggedInUser", uname);
        response.sendRedirect("dashboard.jsp");
    } else {
        response.sendRedirect("login.jsp?error=1");
    }
%>
```

**Explanation:**
- On success: we store the username in `session` (persists across pages for this user) and **redirect** to `dashboard.jsp` — redirect is correct here because this follows a form submission (see rule of thumb above), preventing resubmission on refresh.
- On failure: redirect back to `login.jsp` with an error flag in the URL.

### 3.3 `dashboard.jsp` — Protected Page (Session Check)

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<html>
<body>
    <c:choose>
        <c:when test="${empty sessionScope.loggedInUser}">
            <p>You are not logged in. <a href="login.jsp">Login here</a></p>
        </c:when>
        <c:otherwise>
            <h2>Welcome, ${sessionScope.loggedInUser}!</h2>
            <p>This is your protected dashboard.</p>
            <a href="logout.jsp">Logout</a>
        </c:otherwise>
    </c:choose>
</body>
</html>
```

**Explanation:**
- `empty sessionScope.loggedInUser` is EL's `empty` operator — checks if the value is `null` or an empty string in one clean expression, avoiding a scriptlet null-check.
- This pattern — checking session at the top of every protected page — is exactly what real login-gated pages do. (Mention: in a full project, this check is usually centralized using a Filter, which is beyond today's scope but worth a one-line mention since some students may already know Servlet Filters.)

### 3.4 `logout.jsp` — Destroy the Session

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<%
    session.invalidate();
    response.sendRedirect("login.jsp");
%>
```

**Explanation:**
- `session.invalidate()` destroys the entire session — all data stored in it (`loggedInUser` etc.) is wiped out.
- Redirect back to `login.jsp` afterward so the user lands on a clean login screen.
-   students: "What happens if you click browser Back after logout?" — good discussion point (answer: without a session, `dashboard.jsp`'s `<c:when>` check will correctly show "not logged in" instead of the cached dashboard).

---
