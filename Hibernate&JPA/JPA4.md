# Day 4 — Expression Language (EL) & JSTL Core Tags

## Objectives
By the end of this class, students should be able to:
- Explain why EL and JSTL exist and what problem they solve
- Read and write EL expressions to access data from different scopes
- Use the most important JSTL core tags with full working examples

## Quick Recap of Day 3
- Implicit objects: `request`, `response`, `out`, `session`, `application`, `config`, `pageContext`, `exception`, `page`
- `session` = per user, `application` = shared across all users
- `page`, `include`, `taglib` directives
- Ask 2 students to answer Day 3's recap questions before starting.

---

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

- **EL (Expression Language)** — a simple syntax `${ }` to access data without Java code.
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
- **Important gotcha to mention:** `request.setAttribute()` only lives for that one request. If a user directly opens `showData.jsp` in a new tab (a fresh request), `${requestScope.course}` will be empty — but `${sessionScope.studentName}` will still work because session data persists. This is a great moment to reinforce the scope hierarchy from Day 3.
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

**Setup note for students:** the JSTL library JAR (`jstl-1.2.jar` or the Jakarta equivalent depending on server version) must be present in `WEB-INF/lib`. Confirm this is already added to the project (should be, since we set up the project structure earlier in the course) — if not, walk students through adding it before continuing.

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
- This second pattern is exactly how we'll display data fetched from a database later in the Hibernate module — worth telling students this is a preview of what's coming.

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

## 5. Full Combined Example — Everything Together

`studentReport.jsp`
```jsp
<%@ page import="java.util.*" %>
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<%
    Map<String, Integer> marksMap = new LinkedHashMap<>();
    marksMap.put("Ravi Kumar", 82);
    marksMap.put("Priya Sharma", 55);
    marksMap.put("Anil Reddy", 28);
    request.setAttribute("marksMap", marksMap);
%>
<html>
<body>
    <h2>Student Report — JFS Batch 2</h2>
    <table border="1" cellpadding="6">
        <tr>
            <th>Name</th>
            <th>Marks</th>
            <th>Result</th>
        </tr>
        <c:forEach var="entry" items="${marksMap}">
            <tr>
                <td>${entry.key}</td>
                <td>${entry.value}</td>
                <td>
                    <c:choose>
                        <c:when test="${entry.value >= 35}">Pass</c:when>
                        <c:otherwise>Fail</c:otherwise>
                    </c:choose>
                </td>
            </tr>
        </c:forEach>
    </table>
</body>
</html>
```

**Explanation:**
- Loops over a `Map` — `entry.key` and `entry.value` are how EL accesses `Map.Entry` fields (works because EL calls the getter-style methods automatically, no `entry.getKey()` needed).
- Combines `<c:forEach>` + `<c:choose>` + EL in one realistic report page — zero scriptlets used for the actual output logic.
- Ask students: "Compare this to how much scriptlet code Day 1–3 style would have needed for the same table." Good moment to emphasize why the industry prefers this style.

---

## 6. In-Class Activity
Ask students to build `resultCard.jsp`:
1. In a scriptlet, create a `List<Map<String,Object>>` (or reuse the `Map<String,Integer>` pattern above) with 5 students and their marks.
2. Display them in a table using `<c:forEach>`.
3. Use `<c:choose>` to show Distinction / First Class / Pass / Fail per student (same grade bands as section 4.3).
4. Use `<c:set>` to store the count of "Fail" students in a variable and display it below the table using EL.

## 7. Recap Questions (End of Class)
1. What is the EL shortcut for `request.getParameter("x")`?
2. Why doesn't `<c:if>` support an else block, and what tag do we use instead when we need one?
3. What's the difference between the `begin/end` form and `items` form of `<c:forEach>`?
4. Why is `<c:out>` considered safer than plain `${ }` when printing user input?

## 8. Homework
- Read about JSP form handling and forward vs redirect (we touched redirect briefly on Day 3) — covered in detail Day 5.
- Convert one of your earlier scriptlet-heavy JSP pages (from Day 1–3) to use EL + JSTL instead, removing as many scriptlets as possible.

---
*Prepared for JFS Batch 2 — Day 4 of 15 (JSP & Hibernate Module)*
