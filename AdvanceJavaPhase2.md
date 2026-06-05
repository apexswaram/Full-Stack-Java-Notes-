
```text
src/main/java
src/main/webapp
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

