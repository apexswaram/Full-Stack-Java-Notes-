# Day 5 — Form Handling, Forward vs Redirect, Session Tracking

## Objectives
By the end of this class, students should be able to:
- Handle GET and POST form submissions in JSP using EL/JSTL (no scriptlets)
- Explain and demonstrate the difference between forward and redirect
- Implement a complete login/logout flow using session tracking

## Quick Recap of Day 4
- EL: `${ }`, `${param.x}`, `${sessionScope.x}`, operators, ternary
- JSTL core: `c:if`, `c:choose/when/otherwise`, `c:forEach`, `c:set/remove`
- Ask 2 students to answer Day 4's recap questions before starting.

---

## 1. Form Handling — GET vs POST Recap

Students already know `request.getParameter()` from Day 3 and `${param.x}` from Day 4. Today we formalize **when to use GET vs POST** and build a complete registration form using JSTL/EL style (industry-preferred, no scriptlets).

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
- Ask students: "What happens if you click browser Back after logout?" — good discussion point (answer: without a session, `dashboard.jsp`'s `<c:when>` check will correctly show "not logged in" instead of the cached dashboard).

---

## 4. In-Class Activity
Extend the login flow above:
1. Add a `role` field to the login form (`student` or `admin`, using a `<select>`).
2. Store `role` in the session alongside `loggedInUser`.
3. In `dashboard.jsp`, use `<c:choose>` to show a different welcome message depending on `${sessionScope.role}` ("Welcome Admin" vs "Welcome Student").
4. Bonus: on `login.jsp`, use `<c:if test="${param.error == 1}">` to show an error message when redirected back after a failed login.

## 5. Recap Questions (End of Class)
1. Does the browser's URL change with forward or with redirect? Why?
2. Why is `request.setAttribute()` data lost after a redirect but not after a forward?
3. Why do we use redirect (not forward) right after a successful login form submission?
4. What does `session.invalidate()` do, and where should it be called from?

## 6. Homework
- Read ahead lightly on Hibernate basics (ORM concept) — Day 6 will be a mini practice/wrap-up day combining everything from Days 1–5, then Day 7 starts Hibernate.
- Finish the in-class activity (role-based dashboard) if not completed in class.

---
*Prepared for JFS Batch 2 — Day 5 of 15 (JSP & Hibernate Module)*
