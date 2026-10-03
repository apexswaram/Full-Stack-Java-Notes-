# Day 3 — JSP Implicit Objects & Directives

## Objectives
By the end of this class, students should be able to:
- Explain what implicit objects are and why JSP provides them automatically
- Use all major implicit objects with working code
- Understand the `page`, `include`, and `taglib` directives in depth, with complete examples

## Quick Recap of Day 2
- Four scripting elements: directive `<%@ %>`, declaration `<%! %>`, scriptlet `<% %>`, expression `<%= %>`
- Declarations = class level, once. Scriptlets = method level, per request.
- Ask 2 students to answer Day 2's recap questions before starting.

---

## 1. What Are Implicit Objects?

When the container converts a JSP page into a servlet, it automatically generates certain objects inside the `_jspService()` method — **we don't create them, they're already available to use directly in scriptlets and expressions.** That's why they're called "implicit" (silent/automatic).

There are **9 implicit objects** in JSP. Today we'll cover the 6 most commonly used ones in real projects; the remaining 3 (`pageContext`, `page`, `exception`) are mentioned briefly since they're used less often at this stage.

| Implicit Object | Type | Purpose |
|---|---|---|
| `request` | `HttpServletRequest` | Access data sent by the client (form data, parameters, headers) |
| `response` | `HttpServletResponse` | Control the response sent back to the client |
| `out` | `JspWriter` | Write output to the response body |
| `session` | `HttpSession` | Store data specific to one user across multiple requests |
| `application` | `ServletContext` | Store data shared across the entire web application (all users) |
| `config` | `ServletConfig` | Access servlet/JSP initialization parameters |
| `pageContext` | `PageContext` | Access all other scopes/objects from one place (used more with JSTL) |
| `exception` | `Throwable` | Access the exception object — only available in error pages |
| `page` | `Object` (this) | Refers to the current JSP page instance itself |

---

## 2. `request` Object — Getting Data From the Client

**Concept:** Every time a user submits a form or calls a URL with parameters, that data arrives in the `request` object. We read it using `request.getParameter("name")`.

**Full Example — `loginForm.jsp`** (the form)
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<html>
<head><title>Login Form</title></head>
<body>
    <h2>Login</h2>
    <form action="welcome.jsp" method="post">
        Username: <input type="text" name="username"><br><br>
        Password: <input type="password" name="password"><br><br>
        <input type="submit" value="Login">
    </form>
</body>
</html>
```

**Full Example — `welcome.jsp`** (reads the request data)
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<html>
<head><title>Welcome</title></head>
<body>
<%
    String uname = request.getParameter("username");
    String pass = request.getParameter("password");

    if (uname != null && uname.equals("admin") && pass.equals("admin123")) {
%>
        <h2>Welcome, <%= uname %>! Login successful.</h2>
<%
    } else {
%>
        <h2>Invalid username or password.</h2>
<%
    }
%>
</body>
</html>
```

**Explanation:**
- `request.getParameter("username")` fetches the value typed in the `username` field of the form.
- Notice how the scriptlet `<% %>` and HTML are interleaved — this is a very common real-world pattern for conditional output.
- Also mention `request.getParameterNames()` (returns all parameter names) and `request.getAttribute()/setAttribute()` (used for forwarding data between JSP/Servlet — will matter a lot in Day 5).

---

## 3. `response` Object — Controlling the Output

**Concept:** Used to modify the response — commonly for redirecting to another page or setting response headers.

**Full Example — `redirectDemo.jsp`**
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<%
    String uname = request.getParameter("username");
    if (uname == null || uname.equals("")) {
        response.sendRedirect("loginForm.jsp");
    }
%>
<html>
<body>
    <h2>Hello <%= uname %>, you reached this page directly with a name.</h2>
</body>
</html>
```

**Explanation:**
- `response.sendRedirect("loginForm.jsp")` sends a fresh request to `loginForm.jsp` from the browser itself (URL changes in the address bar) — different from a forward, which happens on the server side (URL doesn't change). We'll compare forward vs redirect properly on Day 5.

---

## 4. `out` Object — Writing to the Response

**Concept:** `out` is used to print content directly, similar to `System.out.println()` but writes to the HTML response instead of the console.

**Full Example — `outDemo.jsp`**
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<html>
<body>
<%
    out.println("<h2>Printing using the out object</h2>");
    for (int i = 1; i <= 5; i++) {
        out.println("<p>Line number " + i + "</p>");
    }
%>
</body>
</html>
```

**Explanation:**
- `out.println()` behaves like `<%= %>` but is more useful inside loops/conditions where we're generating multiple lines of dynamic HTML.
- Point out: this is exactly what expressions (`<%= %>`) do internally — expressions are shorthand for `out.print(...)`.

---

## 5. `session` Object — Data for One Specific User

**Concept:** HTTP is stateless — the server doesn't remember a user between requests by default. `session` lets us store user-specific data (like login info) that persists across multiple pages **for that one user only**.

**Full Example — `setSession.jsp`**
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<%
    String uname = request.getParameter("username");
    session.setAttribute("user", uname);
%>
<html>
<body>
    <h3>Session created for: <%= uname %></h3>
    <a href="profile.jsp">Go to Profile Page</a>
</body>
</html>
```

**Full Example — `profile.jsp`** (reads the session on a different page)
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<html>
<body>
<%
    String uname = (String) session.getAttribute("user");
    if (uname != null) {
%>
        <h2>Profile Page — Welcome back, <%= uname %>!</h2>
<%
    } else {
%>
        <h2>No active session. Please log in first.</h2>
<%
    }
%>
</body>
</html>
```

**Explanation:**
- `session.setAttribute("key", value)` stores data tied to that user's browser session (via a cookie called `JSESSIONID` behind the scenes).
- `session.getAttribute("key")` retrieves it — notice the typecast to `String`, since `getAttribute()` returns `Object`.
- This is the foundation of login systems — very important, spend extra time here.
- Mention `session.invalidate()` for logout — we'll use this in the Day 5 mini practice.

---

## 6. `application` Object — Data Shared Across ALL Users

**Concept:** Unlike `session` (one user), `application` data is shared by **every user** of the web app — it's created once when the app starts and destroyed when it stops.

**Full Example — `visitorCounter.jsp`**
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<%
    Integer count = (Integer) application.getAttribute("totalVisitors");
    if (count == null) {
        count = 1;
    } else {
        count = count + 1;
    }
    application.setAttribute("totalVisitors", count);
%>
<html>
<body>
    <h2>Total visitors to this site so far: <%= count %></h2>
</body>
</html>
```

**Explanation:**
- Every time ANY user (not just one) opens this page, the counter increases — because `application` scope is shared across the whole app, not per-user like `session`.
- Good moment to reinforce the scope hierarchy:
  - **page** scope < **request** scope < **session** scope < **application** scope (in order of how long data lives / how widely it's shared)

---

## 7. `config` Object — Init Parameters (Brief)

**Concept:** Used to read initialization parameters configured for a servlet/JSP in `web.xml`. Less commonly used directly in JSP — just introduce the idea, no deep example needed today.

```jsp
<%
    String siteName = config.getInitParameter("siteName");
%>
```

---

## 8. Directives — Full Detail

### 8.1 `page` Directive
Already introduced briefly on Day 2 — today we go deeper into its useful attributes.

```jsp
<%@ page import="java.util.*, java.text.SimpleDateFormat" %>
<%@ page errorPage="error.jsp" %>
<%@ page isELIgnored="false" %>
```

| Attribute | Purpose |
|---|---|
| `import` | Import Java classes/packages needed in scriptlets |
| `errorPage` | Redirect to a custom error page if an exception occurs |
| `isErrorPage` | Marks the current page as an error-handling page (gives access to `exception` object) |
| `contentType` | Sets response MIME type, e.g. `text/html; charset=UTF-8` |

**Full Example — error handling with `page` directive**

`buggy.jsp`
```jsp
<%@ page errorPage="error.jsp" %>
<html>
<body>
<%
    int a = 10, b = 0;
    int result = a / b;   // will throw ArithmeticException
%>
    <p>Result: <%= result %></p>
</body>
</html>
```

`error.jsp`
```jsp
<%@ page isErrorPage="true" %>
<html>
<body>
    <h2>Oops! Something went wrong.</h2>
    <p>Error details: <%= exception.getMessage() %></p>
</body>
</html>
```

**Explanation:**
- `buggy.jsp` divides by zero, throwing an exception.
- Because `errorPage="error.jsp"` is set, the container automatically forwards to `error.jsp` instead of showing a raw server error.
- `error.jsp` has `isErrorPage="true"`, which unlocks the implicit `exception` object so we can display what went wrong.

### 8.2 `include` Directive
Used to insert the content of another file **at translation time** (before compiling) — think of it as copy-pasting the file's content into this one.

**Full Example**

`header.jsp`
```jsp
<div style="background-color:lightblue;padding:10px;">
    <h2>JFS Batch 2 — Student Portal</h2>
</div>
```

`footer.jsp`
```jsp
<div style="background-color:lightgray;padding:10px;">
    <p>&copy; 2026 JFS Batch 2. All rights reserved.</p>
</div>
```

`home.jsp`
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<%@ include file="header.jsp" %>
<html>
<body>
    <h3>Welcome to the homepage!</h3>
    <p>This is the main content of the page.</p>
</body>
</html>
<%@ include file="footer.jsp" %>
```

**Explanation:**
- At translation time, the container merges `header.jsp` and `footer.jsp` directly into `home.jsp` before generating the servlet — result is a single combined page.
- Useful for common headers/footers/navbars reused across many pages.
- Mention (don't deep-dive yet): there's also a `<jsp:include>` **action** tag that includes at *request* time instead of translation time — we'll compare the two properly in a later class once we cover JSP actions.

### 8.3 `taglib` Directive
Used to bring in a custom/standard tag library (like JSTL) so we can use tags instead of writing raw Java in scriptlets.

```jsp
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
```

**Explanation:**
- We're only introducing the syntax today — full usage with JSTL core tags (`c:if`, `c:forEach`, etc.) is covered in detail on **Day 4**, so don't spend more time here than this.

---

## 9. In-Class Activity
Ask students to build a **3-page mini flow**:
1. `loginForm.jsp` — takes username & password
2. `home.jsp` — on successful login, stores username in `session`, includes a common `header.jsp`/`footer.jsp` using the `include` directive
3. `visitorCount.jsp` — shows a running total of visits using `application` scope

This activity touches `request`, `session`, `application`, and the `include` directive all together — good consolidation exercise.

## 10. Recap Questions (End of Class)
1. What's the difference between `session` and `application` scope? Give a real example of when you'd use each.
2. Why does `home.jsp` need to typecast the result of `session.getAttribute("user")`?
3. At what point is the `include` directive's content merged into the page — translation time or request time?
4. What object becomes available only inside a page marked `isErrorPage="true"`?

## 11. Homework
- Read about Expression Language (EL) and JSTL core tags — covered Day 4.
- Extend the 3-page mini activity: add a logout link that calls `session.invalidate()` and redirects back to `loginForm.jsp`.

---
*Prepared for JFS Batch 2 — Day 3 of 15 (JSP & Hibernate Module)*
