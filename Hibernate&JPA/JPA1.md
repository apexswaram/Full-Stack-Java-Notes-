
# Day 1 — JSP Introduction

## Objectives
By the end of this class, students should be able to:
- Explain what JSP is and why it exists
- Compare JSP with Servlets
- Understand the JSP life cycle
- Write and run their first JSP program

## 1. What is JSP?
- JSP (JavaServer Pages) is a server-side technology used to create dynamic, platform-independent web pages.
- It allows embedding Java code inside HTML using special tags.
- JSP is built **on top of Servlet technology** — every JSP page is internally converted into a servlet by the container (Tomcat).

## 2. Why JSP? (Problem with Servlets)
- In Servlets, HTML is written inside Java code using `out.println()` — messy and hard to maintain for UI-heavy pages.
- JSP flips this: Java code is embedded inside HTML — easier for designing the view/presentation layer.
- Separation of concerns: Servlet = logic (Controller), JSP = presentation (View) → foundation for MVC (covered later in course).

## 3. JSP vs Servlet (Quick Comparison)

| Aspect | Servlet | JSP |
|---|---|---|
| Nature | Java code with embedded HTML | HTML with embedded Java |
| Use case | Business logic / Controller | Presentation / View |
| Compilation | Compiled by developer | Auto-converted to servlet & compiled by container |
| Ease of UI design | Difficult | Easy |

## 4. JSP Life Cycle
1. **Translation** — JSP file is translated into a Servlet (`.java`) by the container.
2. **Compilation** — The generated servlet is compiled into a `.class` file.
3. **Class Loading** — Servlet class is loaded into memory.
4. **Instantiation** — Object of the servlet is created.
5. **Initialization** — `jspInit()` is called (once).
6. **Request Processing** — `_jspService()` is called for every request.
7. **Destroy** — `jspDestroy()` is called when the container shuts down/unloads the JSP.

> Teaching tip: Draw this as a simple flow diagram on the board — Translation → Compilation → Init → Service (repeats per request) → Destroy.

## 5. Setting Up a JSP Project
- Use the same Dynamic Web Project / Maven webapp structure used earlier in the course (students already know this from Servlets).
- JSP files go inside `webapp` (or `WebContent`) folder — **not** inside `WEB-INF` (else it can't be accessed directly via browser).
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
- Show students the auto-generated servlet source (if container allows access to `work` folder) — helps them visually connect JSP → Servlet conversion.

## 7. In-Class Activity
- Ask each student to create a JSP page that:
  - Displays their name and today's date using `<% %>` scriptlet
  - Prints "Welcome to JSP" using `<%= %>` expression (just introduce this briefly — full scripting elements covered Day 2)

## 8. Recap Questions (End of Class)
1. What is the first phase of the JSP life cycle?
2. Why is JSP considered better than Servlets for the view layer?
3. Where should `.jsp` files be placed in a project?

## 9. Homework
- Read about JSP scripting elements (directive, declaration, scriptlet, expression) — will be covered in detail on Day 2.
- Try modifying `hello.jsp` to print a small multiplication table using a scriptlet loop.

---
*Prepared for JFS Batch 2 — Day 1 of 15 (JSP & Hibernate Module)*
