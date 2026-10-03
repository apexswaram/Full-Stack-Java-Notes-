# Day 6 — Mini Practice Project & JSP Wrap-Up

## Objectives
By the end of this class, students should be able to:
- Combine everything learned in Days 1–5 into one working multi-page application
- Confidently explain every JSP concept covered so far, with working code
- Walk into Day 7 (Hibernate) with JSP fundamentals fully solid

## Quick Recap of Days 1–5 (Go Through This on the Board First)

| Day | Topic |
|---|---|
| 1 | JSP intro, life cycle, first program |
| 2 | Scripting elements: directive, declaration, scriptlet, expression |
| 3 | Implicit objects (`request`, `response`, `out`, `session`, `application`), `page`/`include`/`taglib` directives |
| 4 | EL (`${ }`, `param`, scopes, operators) + JSTL core (`c:if`, `c:choose`, `c:forEach`, `c:set`) |
| 5 | Form handling, forward vs redirect, session-based login/logout |

Today: no new theory — we build **one connected mini project** — "Student Portal" — using everything above, then do a rapid-fire Q&A to close out the JSP module before starting Hibernate on Day 7.

---

## 1. Mini Project: "Student Portal"

**Flow:** Register → Login → Dashboard (view student list) → Profile → Logout

This mirrors the exact structure of every real login-based web app students will build for the rest of the course (and eventually rebuild with Hibernate + a real database starting Day 9).

### 1.1 `register.jsp` — Registration Form

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<html>
<body>
    <h2>Student Portal — Register</h2>
    <form action="registerProcess.jsp" method="post">
        Name: <input type="text" name="name" required><br><br>
        Username: <input type="text" name="username" required><br><br>
        Password: <input type="password" name="password" required><br><br>
        Course:
        <select name="course">
            <option value="Java Full Stack">Java Full Stack</option>
            <option value="Python Full Stack">Python Full Stack</option>
            <option value="Data Analytics">Data Analytics</option>
        </select><br><br>
        <input type="submit" value="Register">
    </form>
    <p>Already registered? <a href="login.jsp">Login here</a></p>
</body>
</html>
```

### 1.2 `registerProcess.jsp` — Store Student in Application Scope

We don't have a database yet (that starts Day 7+ with Hibernate), so today we simulate storage using the **`application` object** — a `List` shared by the whole app, exactly as learned on Day 3.

```jsp
<%@ page import="java.util.*" %>
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<%
    // Get the shared student list from application scope, or create it if this is the first registration
    List<Map<String, String>> studentList = (List<Map<String, String>>) application.getAttribute("studentList");
    if (studentList == null) {
        studentList = new ArrayList<>();
    }

    Map<String, String> student = new HashMap<>();
    student.put("name", request.getParameter("name"));
    student.put("username", request.getParameter("username"));
    student.put("password", request.getParameter("password"));
    student.put("course", request.getParameter("course"));

    studentList.add(student);
    application.setAttribute("studentList", studentList);

    response.sendRedirect("login.jsp");
%>
```

**Explanation (ties back to earlier days):**
- `application.getAttribute()`/`setAttribute()` → Day 3's `application` object — shared across **all** users, so every registered student is visible to everyone (this is exactly why a real database will replace this starting Day 7 — `application` scope resets when the server restarts and doesn't scale, but it's perfect for today's teaching purpose).
- `response.sendRedirect("login.jsp")` → Day 5's rule: always redirect after a form submission that changes data, to avoid resubmission on refresh.

### 1.3 `login.jsp` — Login Form (with Error Message using JSTL)

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<html>
<body>
    <h2>Student Portal — Login</h2>

    <c:if test="${param.error == 1}">
        <p style="color:red;">Invalid username or password.</p>
    </c:if>

    <form action="loginProcess.jsp" method="post">
        Username: <input type="text" name="username"><br><br>
        Password: <input type="password" name="password"><br><br>
        <input type="submit" value="Login">
    </form>
    <p>New student? <a href="register.jsp">Register here</a></p>
</body>
</html>
```

**Explanation:**
- `<c:if test="${param.error == 1}">` → Day 4's JSTL + Day 5's error-flag-in-URL pattern combined — shows the error message only when redirected back with `?error=1`.

### 1.4 `loginProcess.jsp` — Validate Against the Student List

```jsp
<%@ page import="java.util.*" %>
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<%
    String uname = request.getParameter("username");
    String pass = request.getParameter("password");

    List<Map<String, String>> studentList = (List<Map<String, String>>) application.getAttribute("studentList");
    Map<String, String> matchedStudent = null;

    if (studentList != null) {
        for (Map<String, String> s : studentList) {
            if (s.get("username").equals(uname) && s.get("password").equals(pass)) {
                matchedStudent = s;
                break;
            }
        }
    }

    if (matchedStudent != null) {
        session.setAttribute("loggedInUser", matchedStudent);
        response.sendRedirect("dashboard.jsp");
    } else {
        response.sendRedirect("login.jsp?error=1");
    }
%>
```

**Explanation:**
- We loop through the shared `studentList` (application scope) checking for a username+password match — a simplified stand-in for what a database query will do starting Day 9 (`SELECT * FROM student WHERE username=? AND password=?`, effectively).
- On match: store the **entire student `Map`** (not just the username this time) in `session` — Day 3/Day 5's `session.setAttribute()`, now storing a richer object.
- Redirect logic is identical to Day 5's login flow.

### 1.5 `dashboard.jsp` — Protected Page + Full Student List Table

```jsp
<%@ page import="java.util.*" %>
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<html>
<body>
<c:choose>
    <c:when test="${empty sessionScope.loggedInUser}">
        <p>You are not logged in. <a href="login.jsp">Login here</a></p>
    </c:when>
    <c:otherwise>
        <h2>Welcome, ${sessionScope.loggedInUser.name}!</h2>
        <p>Course: ${sessionScope.loggedInUser.course}</p>
        <p><a href="profile.jsp">My Profile</a> | <a href="logout.jsp">Logout</a></p>

        <h3>All Registered Students</h3>
        <table border="1" cellpadding="6">
            <tr><th>Name</th><th>Username</th><th>Course</th></tr>
            <c:forEach var="s" items="${applicationScope.studentList}">
                <tr>
                    <td>${s.name}</td>
                    <td>${s.username}</td>
                    <td>${s.course}</td>
                </tr>
            </c:forEach>
        </table>
    </c:otherwise>
</c:choose>
</body>
</html>
```

**Explanation:**
- `<c:choose>`/`<c:when>`/`<c:otherwise>` with `empty sessionScope.loggedInUser` → Day 5's protected-page pattern, unchanged.
- `${sessionScope.loggedInUser.name}` → EL automatically calls `.get("name")` on the `Map` we stored — same dot-syntax students already used for `Map.Entry` on Day 4 (`entry.key`/`entry.value`).
- `<c:forEach var="s" items="${applicationScope.studentList}">` → Day 4's collection-looping pattern, now looping over live data built through the whole mini project instead of a hardcoded list — this is the exact same technique that will display real database rows once Hibernate is introduced.

### 1.6 `profile.jsp` — Simple Read-Only Profile Page (Forward Example)

`profile.jsp`
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<c:choose>
    <c:when test="${empty sessionScope.loggedInUser}">
        <c:redirect url="login.jsp"/>
    </c:when>
    <c:otherwise>
        <jsp:forward page="profileView.jsp"/>
    </c:otherwise>
</c:choose>
```

`profileView.jsp`
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<html>
<body>
    <h2>My Profile</h2>
    <p>Name: ${sessionScope.loggedInUser.name}</p>
    <p>Username: ${sessionScope.loggedInUser.username}</p>
    <p>Course: ${sessionScope.loggedInUser.course}</p>
    <a href="dashboard.jsp">Back to Dashboard</a>
</body>
</html>
```

**Explanation:**
- New tag introduced here: `<c:redirect>` — the JSTL tag version of `response.sendRedirect()`, used so we can stay scriptlet-free even for redirect logic.
- `<jsp:forward page="profileView.jsp"/>` → Day 5's forward action tag — used here (instead of redirect) because we want `profile.jsp` to hand off to `profileView.jsp` **within the same request**, keeping it fast and internal since there's no form submission involved this time.
- This page is a nice small quiz moment: ask students "why forward here but redirect for login?" — answer ties directly to Day 5's rule of thumb (forward = internal handoff, no data-changing submission involved; redirect = after form submission, or to prevent access when not logged in).

### 1.7 `logout.jsp` — Destroy Session

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<%
    session.invalidate();
    response.sendRedirect("login.jsp");
%>
```

Identical to Day 5 — no change needed, reused as-is.

---

## 2. Build Order for Class (Live-Coding Sequence)

Recommended order to build this live with students, so it always runs at each step:
1. `register.jsp` + `registerProcess.jsp` → test registering 2–3 students
2. `login.jsp` + `loginProcess.jsp` → test login with correct and wrong credentials (check the error message shows)
3. `dashboard.jsp` → test the student table renders correctly
4. `profile.jsp` + `profileView.jsp` → test forward works, URL stays on `profile.jsp`
5. `logout.jsp` → test session is destroyed and dashboard redirects to login afterward

---

## 3. In-Class / Take-Home Extension Activity
Ask students to extend the mini project with:
1. A "Course-wise count" section on the dashboard — use `<c:forEach>` + a counter variable (via `<c:set>`) to show how many students registered per course.
2. Prevent duplicate usernames at registration — check the `studentList` in `registerProcess.jsp` before adding a new student, and redirect back to `register.jsp?error=duplicate` with a JSTL error message if the username already exists.

---

## 4. Full JSP Module Recap — Rapid Fire Q&A (End of Class)

Go around the room, one question per student, quick answers only:
1. What are the 4 phases of the JSP life cycle (name them in order)?
2. Difference between a declaration and a scriptlet?
3. Name 3 implicit objects and what each is used for.
4. What does the `include` directive do, and when is it merged into the page?
5. What is EL, and what problem does it solve compared to scriptlets?
6. Difference between `<c:if>` and `<c:choose>`?
7. Two ways to loop with `<c:forEach>` — when would you use each?
8. Forward vs redirect — 2 differences.
9. Why do we redirect after a successful login instead of forwarding?
10. What does `session.invalidate()` do?

## 5. Looking Ahead
- Day 7 begins the **Hibernate** half of the module — ORM concept, why we move away from raw JDBC, and Hibernate's architecture.
- Mention to students: the `studentList` we simulated today using `application` scope is exactly the kind of data that a real `Student` table in a database will hold starting Day 9 — today's project was intentionally designed to make that transition feel natural.

---
*Prepared for JFS Batch 2 — Day 6 of 15 (JSP & Hibernate Module) — End of JSP Section*
