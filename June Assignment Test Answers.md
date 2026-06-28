# Movie Ticket Booking Management System (Servlet CRUD Project)

## Student 1 (RamyaSri) - Practical Assignment Solution

---

# Project Overview

Develop a complete **Movie Ticket Booking Management System** using:

* HTML
* Java Servlets
* JDBC
* MySQL
* Apache Tomcat 9
* Eclipse IDE

The application should perform all CRUD operations.

---

# Technologies Used

| Technology    | Purpose               |
| ------------- | --------------------- |
| Java          | Backend Development   |
| Servlets      | Handle HTTP Requests  |
| JDBC          | Database Connectivity |
| MySQL         | Database              |
| HTML          | User Interface        |
| Apache Tomcat | Web Server            |
| Eclipse IDE   | Development           |

---

# Software Required

* JDK 8 or Above
* Eclipse Enterprise Edition
* Apache Tomcat 9
* MySQL Server
* MySQL Connector JAR

Place MySQL Connector inside

```
WEB-INF/lib
```

---

# Project Structure

```text
MovieBookingCRUD
│
├── src
│
│   └── com.movie
│
│       ├── DBConnect.java
│       ├── BookTicketServlet.java
│       ├── ViewBookingsServlet.java
│       ├── EditBookingServlet.java
│       ├── UpdateBookingServlet.java
│       └── DeleteBookingServlet.java
│
├── WebContent
│
│   ├── BookTicket.html
│   ├── BookingSuccess.html
│   └── ViewBookings.html
│
└── WEB-INF
    └── lib
         └── mysql-connector-j.jar
```

---

# Database Setup

## Step 1

```sql
CREATE DATABASE MOVIEBOOKING;
```

---

## Step 2

```sql
USE MOVIEBOOKING;
```

---

## Step 3

```sql
CREATE TABLE BOOKINGS
(
    id INT PRIMARY KEY AUTO_INCREMENT,
    customer_name VARCHAR(100),
    movie_name VARCHAR(100),
    seat_number VARCHAR(20),
    ticket_price DOUBLE
);
```

---

# CRUD Operations

| Operation | Meaning |
| --------- | ------- |
| C         | Create  |
| R         | Read    |
| U         | Update  |
| D         | Delete  |

---

# Application Flow

```text
BookTicket.html
        │
        ▼
BookTicketServlet
        │
        ▼
MySQL Database
        │
        ▼
BookingSuccess.html

--------------------------------------

ViewBookings.html
        │
        ▼
ViewBookingsServlet
        │
        ▼
Display All Bookings

--------------------------------------

Edit
        │
        ▼
EditBookingServlet
        │
        ▼
Update Form
        │
        ▼
UpdateBookingServlet
        │
        ▼
Database Updated

--------------------------------------

Delete
        │
        ▼
DeleteBookingServlet
        │
        ▼
Record Deleted
```

---

# Assignment Requirements

Students must develop the following files.

## Java Files

```
DBConnect.java

BookTicketServlet.java

ViewBookingsServlet.java

EditBookingServlet.java

UpdateBookingServlet.java

DeleteBookingServlet.java
```

---

## HTML Files

```
BookTicket.html

BookingSuccess.html

ViewBookings.html
```

---

# Frontend Requirements

## BookTicket.html

Create a booking form containing:

* Customer Name
* Movie Name
* Seat Number
* Ticket Price

Form Method

```html
POST
```

Form Action

```html
BookTicket
```

---

## BookingSuccess.html

Display

```
Movie Ticket Booked Successfully
```

---

## ViewBookings.html

Display one hyperlink

```
View All Bookings
```

---

# Backend Requirements

## BookTicketServlet

Responsibilities

* Read form data
* Connect database
* Insert booking
* Redirect to success page

---

## ViewBookingsServlet

Display HTML Table

Columns

```
ID

Customer Name

Movie Name

Seat Number

Ticket Price

Delete

Edit
```

---

## EditBookingServlet

* Receive Booking ID
* Fetch booking
* Display update form

---

## UpdateBookingServlet

Update

* Customer Name
* Movie Name
* Seat Number
* Ticket Price

---

## DeleteBookingServlet

Delete booking using ID.

Redirect

```
viewbookings
```

---

# Expected Output

## Booking Page

```
Movie Ticket Booking

Customer Name

Movie Name

Seat Number

Ticket Price

[ Book Ticket ]
```

---

## View Booking

```
-------------------------------------------------------------
ID

Customer

Movie

Seat

Price

Delete

Edit
-------------------------------------------------------------
```

---

# URL Testing

```
http://localhost:8080/MovieBookingCRUD/BookTicket.html
```

```
http://localhost:8080/MovieBookingCRUD/ViewBookings.html
```

```
http://localhost:8080/MovieBookingCRUD/viewbookings
```

---

# Practical Checklist

Complete all the following:

* Create Database
* Create Table
* Create HTML Pages
* Insert Booking
* View All Bookings
* Edit Booking
* Update Booking
* Delete Booking
* Test Every Module

---

# Evaluation Scheme

| Module    |   Marks |
| --------- | ------: |
| Database  |      30 |
| Frontend  |      30 |
| Backend   |      30 |
| Viva      |      10 |
| **Total** | **100** |

---

## Viva Questions & Answers 

### 1. What is JDBC?

**Answer:**

JDBC (Java Database Connectivity) is a Java API used to connect Java applications with databases like MySQL, Oracle, PostgreSQL, etc. It allows Java programs to perform database operations such as Insert, Update, Delete, and Select.

---

### 2. What is a Servlet?

**Answer:**

A Servlet is a Java class that runs on a web server and handles HTTP requests from clients (browsers) and generates HTTP responses.

---

### 3. What is the purpose of `DBConnect.java`?

**Answer:**

`DBConnect.java` is used to establish a connection between the Java application and the MySQL database. It loads the JDBC driver and returns a `Connection` object.

---

### 4. Why do we use `PreparedStatement`?

**Answer:**

`PreparedStatement` is used to execute SQL queries safely and efficiently.

**Advantages:**

* Prevents SQL Injection
* Executes faster for repeated queries
* Supports dynamic values using `?`

Example:

```java
PreparedStatement ps =
con.prepareStatement(
"INSERT INTO BOOKINGS(customer_name,movie_name,seat_number,ticket_price) VALUES(?,?,?,?)");
```

---

### 5. What is the difference between `executeQuery()` and `executeUpdate()`?

**Answer:**

| executeQuery()          | executeUpdate()                 |
| ----------------------- | ------------------------------- |
| Used for SELECT queries | Used for INSERT, UPDATE, DELETE |
| Returns ResultSet       | Returns int                     |
| Retrieves records       | Modifies records                |

---

### 6. What is `ResultSet`?

**Answer:**

`ResultSet` is an object that stores the data returned from a SELECT query. It is used to read records one by one using `rs.next()`.

Example:

```java
ResultSet rs = ps.executeQuery();

while(rs.next())
{
    System.out.println(rs.getString("customer_name"));
}
```

---

### 7. What is the difference between GET and POST?

**Answer:**

| GET                         | POST                        |
| --------------------------- | --------------------------- |
| Data is visible in the URL  | Data is hidden from the URL |
| Used to retrieve data       | Used to send data           |
| Less secure                 | More secure                 |
| Used for View, Edit, Delete | Used for Insert and Update  |

---

### 8. Why do we use `response.sendRedirect()`?

**Answer:**

`response.sendRedirect()` redirects the user to another page after completing an operation like Insert, Update, or Delete.

Example:

```java
response.sendRedirect("viewbookings");
```

---

### 9. What is `AUTO_INCREMENT`?

**Answer:**

`AUTO_INCREMENT` automatically generates a unique value for the primary key whenever a new record is inserted into the table.

Example:

```sql
id INT PRIMARY KEY AUTO_INCREMENT
```

---

### 10. What is CRUD?

**Answer:**

CRUD stands for:

* **C** – Create (Insert Data)
* **R** – Read (View Data)
* **U** – Update (Modify Existing Data)
* **D** – Delete (Remove Data)

These are the four basic database operations used in most web applications.




## Project Structure

```text
MovieBookingCRUD
│
├── src
│   └── com.movie
│       ├── DBConnect.java
│       ├── BookTicketServlet.java
│       ├── ViewBookingsServlet.java
│       ├── EditBookingServlet.java
│       ├── UpdateBookingServlet.java
│       └── DeleteBookingServlet.java
│
├── WebContent
│   ├── BookTicket.html
│   ├── BookingSuccess.html
│   └── ViewBookings.html
│
└── Database.sql
```

---

# 1. Database.sql

```sql
CREATE DATABASE MOVIEBOOKING;

USE MOVIEBOOKING;

CREATE TABLE BOOKINGS
(
    id INT PRIMARY KEY AUTO_INCREMENT,
    customer_name VARCHAR(100),
    movie_name VARCHAR(100),
    seat_number VARCHAR(20),
    ticket_price DOUBLE
);
```

---

# 2. DBConnect.java

```java
package com.movie;

import java.sql.Connection;
import java.sql.DriverManager;

public class DBConnect
{
	public static Connection getConnection()
	{
		Connection con = null;

		try
		{
			Class.forName("com.mysql.cj.jdbc.Driver");

			con = DriverManager.getConnection(
					"jdbc:mysql://localhost:3306/MOVIEBOOKING",
					"root",
					"password");
		}
		catch(Exception e)
		{
			System.out.println(e);
		}

		return con;
	}
}
```

---

# 3. BookTicket.html

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Movie Ticket Booking</title>
</head>
<body>

<h1>Movie Ticket Booking</h1>

<form action="BookTicket" method="post">

Customer Name :
<input type="text" name="customer_name">

<br><br>

Movie Name :
<input type="text" name="movie_name">

<br><br>

Seat Number :
<input type="text" name="seat_number">

<br><br>

Ticket Price :
<input type="text" name="ticket_price">

<br><br>

<input type="submit" value="Book Ticket">

</form>

</body>
</html>
```

---

# 4. BookTicketServlet.java

```java
package com.movie;

import java.io.IOException;
import java.sql.Connection;
import java.sql.PreparedStatement;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

@WebServlet("/BookTicket")
public class BookTicketServlet extends HttpServlet
{
	private static final long serialVersionUID = 1L;

	@Override
	protected void doPost(
			HttpServletRequest request,
			HttpServletResponse response)
			throws IOException, ServletException
	{
		String customer =
				request.getParameter("customer_name");

		String movie =
				request.getParameter("movie_name");

		String seat =
				request.getParameter("seat_number");

		double price =
				Double.parseDouble(
				request.getParameter("ticket_price"));

		try
		{
			Connection con =
					DBConnect.getConnection();

			PreparedStatement ps =
					con.prepareStatement(
			"INSERT INTO BOOKINGS(customer_name,movie_name,seat_number,ticket_price) VALUES(?,?,?,?)");

			ps.setString(1, customer);
			ps.setString(2, movie);
			ps.setString(3, seat);
			ps.setDouble(4, price);

			int rows = ps.executeUpdate();

			if(rows > 0)
			{
				System.out.println("Booking Successful");
			}
			else
			{
				System.out.println("Booking Failed");
			}

			con.close();
		}
		catch(Exception e)
		{
			System.out.println(e);
		}

		response.sendRedirect("BookingSuccess.html");
	}
}
```

---
## 5. BookingSuccess.html

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Booking Success</title>
</head>
<body>

<h1>Movie Ticket Booked Successfully</h1>

</body>
</html>
```

---

# 6. ViewBookings.html

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>View Bookings</title>
</head>
<body>

<h1>Movie Ticket Bookings</h1>

<a href="viewbookings">View All Bookings</a>

</body>
</html>
```

---

# 7. ViewBookingsServlet.java

```java
package com.movie;

import java.io.IOException;
import java.io.PrintWriter;
import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

@WebServlet("/viewbookings")
public class ViewBookingsServlet extends HttpServlet
{
	private static final long serialVersionUID = 1L;

	@Override
	protected void doGet(
			HttpServletRequest request,
			HttpServletResponse response)
			throws ServletException, IOException
	{
		response.setContentType("text/html");

		PrintWriter out = response.getWriter();

		out.println("<html>");
		out.println("<body>");

		out.println("<h1>Movie Ticket Bookings</h1>");

		out.println("<table border='1'>");

		out.println(
				"<tr>"
				+ "<th>ID</th>"
				+ "<th>CUSTOMER NAME</th>"
				+ "<th>MOVIE NAME</th>"
				+ "<th>SEAT NUMBER</th>"
				+ "<th>TICKET PRICE</th>"
				+ "<th>DELETE</th>"
				+ "<th>EDIT</th>"
				+ "</tr>");

		try
		{
			Connection con = DBConnect.getConnection();

			PreparedStatement ps =
					con.prepareStatement(
							"SELECT * FROM BOOKINGS");

			ResultSet rs = ps.executeQuery();

			while(rs.next())
			{
				out.println("<tr>");

				out.println("<td>"+rs.getInt("id")+"</td>");
				out.println("<td>"+rs.getString("customer_name")+"</td>");
				out.println("<td>"+rs.getString("movie_name")+"</td>");
				out.println("<td>"+rs.getString("seat_number")+"</td>");
				out.println("<td>"+rs.getDouble("ticket_price")+"</td>");

				out.println("<td>");
				out.println("<a href='delete?id="
						+ rs.getInt("id")
						+ "'>Delete</a>");
				out.println("</td>");

				out.println("<td>");
				out.println("<a href='edit?id="
						+ rs.getInt("id")
						+ "'>Edit</a>");
				out.println("</td>");

				out.println("</tr>");
			}

			con.close();
		}
		catch(Exception e)
		{
			e.printStackTrace();
		}

		out.println("</table>");

		out.println("</body>");
		out.println("</html>");
	}
}
```

---

# 8. EditBookingServlet.java

```java
package com.movie;

import java.io.IOException;
import java.io.PrintWriter;
import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

@WebServlet("/edit")
public class EditBookingServlet extends HttpServlet
{
	private static final long serialVersionUID = 1L;

	@Override
	protected void doGet(
			HttpServletRequest request,
			HttpServletResponse response)
			throws ServletException, IOException
	{
		int id = Integer.parseInt(request.getParameter("id"));

		response.setContentType("text/html");

		PrintWriter out = response.getWriter();

		try
		{
			Connection con = DBConnect.getConnection();

			PreparedStatement ps =
					con.prepareStatement(
							"SELECT * FROM BOOKINGS WHERE ID=?");

			ps.setInt(1, id);

			ResultSet rs = ps.executeQuery();

			if(rs.next())
			{
				out.println("<html>");
				out.println("<body>");

				out.println("<h1>Update Booking</h1>");

				out.println("<form action='update' method='post'>");

				out.println("<input type='hidden' name='id' value='"
						+ rs.getInt("id") + "'>");

				out.println("Customer Name:<br>");
				out.println("<input type='text' name='customer_name' value='"
						+ rs.getString("customer_name") + "'>");

				out.println("<br><br>");

				out.println("Movie Name:<br>");
				out.println("<input type='text' name='movie_name' value='"
						+ rs.getString("movie_name") + "'>");

				out.println("<br><br>");

				out.println("Seat Number:<br>");
				out.println("<input type='text' name='seat_number' value='"
						+ rs.getString("seat_number") + "'>");

				out.println("<br><br>");

				out.println("Ticket Price:<br>");
				out.println("<input type='text' name='ticket_price' value='"
						+ rs.getDouble("ticket_price") + "'>");

				out.println("<br><br>");

				out.println("<input type='submit' value='Update'>");

				out.println("</form>");

				out.println("</body>");
				out.println("</html>");
			}

			con.close();
		}
		catch(Exception e)
		{
			e.printStackTrace();
		}
	}
}
```
---

## 9. UpdateBookingServlet.java

```java
package com.movie;

import java.io.IOException;
import java.sql.Connection;
import java.sql.PreparedStatement;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

@WebServlet("/update")
public class UpdateBookingServlet extends HttpServlet
{
	private static final long serialVersionUID = 1L;

	@Override
	protected void doPost(
			HttpServletRequest request,
			HttpServletResponse response)
			throws ServletException, IOException
	{
		int id = Integer.parseInt(
				request.getParameter("id"));

		String customer =
				request.getParameter("customer_name");

		String movie =
				request.getParameter("movie_name");

		String seat =
				request.getParameter("seat_number");

		double price =
				Double.parseDouble(
				request.getParameter("ticket_price"));

		try
		{
			Connection con = DBConnect.getConnection();

			PreparedStatement ps = con.prepareStatement(
					"UPDATE BOOKINGS "
					+ "SET CUSTOMER_NAME=?,MOVIE_NAME=?,SEAT_NUMBER=?,TICKET_PRICE=? "
					+ "WHERE ID=?");

			ps.setString(1, customer);
			ps.setString(2, movie);
			ps.setString(3, seat);
			ps.setDouble(4, price);
			ps.setInt(5, id);

			int rows = ps.executeUpdate();

			if(rows > 0)
			{
				System.out.println("Booking Updated Successfully");
			}
			else
			{
				System.out.println("Update Failed");
			}

			con.close();
		}
		catch(Exception e)
		{
			e.printStackTrace();
		}

		response.sendRedirect("viewbookings");
	}
}
```

---

# 10. DeleteBookingServlet.java

```java
package com.movie;

import java.io.IOException;
import java.sql.Connection;
import java.sql.PreparedStatement;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

@WebServlet("/delete")
public class DeleteBookingServlet extends HttpServlet
{
	private static final long serialVersionUID = 1L;

	@Override
	protected void doGet(
			HttpServletRequest request,
			HttpServletResponse response)
			throws ServletException, IOException
	{
		int id = Integer.parseInt(
				request.getParameter("id"));

		try
		{
			Connection con = DBConnect.getConnection();

			PreparedStatement ps = con.prepareStatement(
					"DELETE FROM BOOKINGS WHERE ID=?");

			ps.setInt(1, id);

			int rows = ps.executeUpdate();

			if(rows > 0)
			{
				System.out.println("Booking Deleted Successfully");
			}
			else
			{
				System.out.println("Deletion Failed");
			}

			con.close();
		}
		catch(Exception e)
		{
			System.out.println(e);
		}

		response.sendRedirect("viewbookings");
	}
}
```
---
