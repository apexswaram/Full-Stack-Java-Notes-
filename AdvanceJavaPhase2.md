

# HTML Forms for Java Web Applications

---

# Why Do We Need Forms?

### Instagram

```text
Username
Email
Phone Number
Password
```

How does Instagram collect this information?


Using a **Form**.

---

# Definition of Form

> A form is used to collect data from users and send that data to a server.

Examples:

* Login Form
* Registration Form
* Feedback Form
* Contact Form

---

# Basic Form Syntax

```html
<form>

</form>
```

Everything that collects user data should be inside the form tag.

---

# Instagram Registration Example

```html
<form>

Username :
<input type="text">

<br><br>

Password :
<input type="password">

<br><br>

<input type="submit">

</form>
```

---

# Form Tag

## Syntax

```html
<form action="" method="">

</form>
```

Two important attributes:

### action

### method

---

# action Attribute

## Syntax

```html
<form action="register">
```

Meaning:

```text
After clicking submit,
send data to register servlet
```

Visualization:

```text
HTML Form
      ↓
action="register"
      ↓
RegisterServlet
```

---

# method Attribute

## Syntax

```html
<form action="register"
      method="post">
```

Two methods:

### GET

### POST

---

# GET Method

```html
method="get"
```

Data visible in URL.

Example:

```text
localhost:8080/register?
username=mahesh
```

Not secure.

---

# POST Method

```html
method="post"
```

Data hidden.

Used for:

* Login
* Registration
* Banking
* Payment Applications

Instagram uses POST.

---

# Input Tag

## Syntax

```html
<input>
```

Used to collect user input.

---

# Text Box

## Syntax

```html
<input type="text">
```

Used for:

* Username
* Name
* City

Example:

```html
Username:
<input type="text">
```

---

# Password Field

## Syntax

```html
<input type="password">
```

Output:

```text
*****
```

Used for passwords.

---

# Email Field

## Syntax

```html
<input type="email">
```

Used for email addresses.

Example:

```html
Email:
<input type="email">
```

---

# Submit Button

## Syntax

```html
<input type="submit">
```

Used to send data to server.

Visualization:

```text
User fills form
       ↓
Clicks Submit
       ↓
Data goes to Servlet
```

---

# The Most Important Attribute

# name

Students usually miss this concept.

---

## Syntax

```html
<input type="text"
       name="username">
```

---

### Why name is important?

Servlet reads data using name.

HTML

```html
<input type="text"
       name="username">
```

Servlet

```java
String username =
request.getParameter("username");
```

Both names must match.

---

# Example

HTML

```html
<input type="text"
       name="username">
```

Servlet

```java
request.getParameter("username");
```

Works.

---

HTML

```html
<input type="text"
       name="username">
```

Servlet

```java
request.getParameter("name");
```

Returns:

```text
null
```

Because names are different.

---


# Connect Form With Servlet

HTML

```html
<form action="register"
      method="post">
```

↓

Servlet

```java
@WebServlet("/register")
```

↓

Receive Data

```java
String username =
request.getParameter("username");
```

---

# Full Flow Diagram

```text
User
 ↓
HTML Form
 ↓
Username
Email
Phone
Password
 ↓
Submit Button
 ↓
action="register"
 ↓
Tomcat Server
 ↓
RegisterServlet
 ↓
request.getParameter()
 ↓
Java Variables
 ↓
Console Output

```

# Project Structure

```text
InstagramRegistration
│
├── src
│   └── main
│       │
│       ├── java
│       │   └── com.instagram
│       │       └── RegistrationServlet.java
│       │
│       └── webapp
│           ├── register.html
│           └── WEB-INF
│
└── Tomcat v9.0
```

---

# register.html

Location:

```text
src/main/webapp/register.html
```

```html
<!DOCTYPE html>
<html>

<head>
<meta charset="UTF-8">
<title>Instagram Registration</title>
</head>

<body>

<h1>Create Instagram Account</h1>

<form action="register" method="post">

    Username :
    <input type="text" name="username">

    <br><br>

    Email :
    <input type="email" name="email">

    <br><br>

    Phone :
    <input type="text" name="phone">

    <br><br>

    Password :
    <input type="password" name="password">

    <br><br>

    <input type="submit" value="Create Account">

</form>

</body>
</html>
```

---

# RegistrationServlet.java

Location:

```text
src/main/java/com/instagram/RegistrationServlet.java
```

```java
package com.instagram;

import java.io.IOException;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

@WebServlet("/register")
public class RegistrationServlet extends HttpServlet {

    private static final long serialVersionUID = 1L;

    @Override
    protected void doGet(HttpServletRequest request,
                         HttpServletResponse response)
            throws ServletException, IOException {

        response.getWriter().println(
                "Registration Servlet Working");
    }

    @Override
    protected void doPost(HttpServletRequest request,
                          HttpServletResponse response)
            throws ServletException, IOException {

        String username =
                request.getParameter("username");

        String email =
                request.getParameter("email");

        String phone =
                request.getParameter("phone");

        String password =
                request.getParameter("password");

        System.out.println();
        System.out.println("================================");

        System.out.println("USER DATA RECEIVED");

        System.out.println("Username : " + username);

        System.out.println("Email    : " + email);

        System.out.println("Phone    : " + phone);

        System.out.println("Password : " + password);

        System.out.println("================================");

        response.sendRedirect("register.html");
    }
}
```

---

# Run URL

After starting Tomcat:

Open:

```text
http://localhost:8080/InstagramRegistration/register.html
```

Fill:

```text
Username : Mahesh
Email : mahesh@gmail.com
Phone : 9876543210
Password : 12345
```

Click:

```text
Create Account
```

---

# Output In Eclipse Console

```text
================================

USER DATA RECEIVED

Username : Mahesh

Email    : mahesh@gmail.com

Phone    : 9876543210

Password : 12345

================================
```

---



```text
Project
  ↓
Properties
  ↓
Java Build Path
  ↓
Libraries
  ↓
Add Library
  ↓
Server Runtime
  ↓
Apache Tomcat v9.0
```

---


# Draw this flow:

```text
Instagram Registration Form
            ↓
       register.html
            ↓
       Submit Button
            ↓
        HTTP POST
            ↓
   RegistrationServlet
            ↓
request.getParameter()
            ↓
      Java Variables
            ↓
   System.out.println()
            ↓
      Eclipse Console
```

