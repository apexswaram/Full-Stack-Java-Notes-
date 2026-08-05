
# Introduction to Frontend Development

Frontend Development is used to create the visible part of a website that users interact with.

### Frontend Technologies

| Technology | Full Form                  | Purpose                         |
| ---------- | -------------------------- | ------------------------------- |
| HTML       | Hyper Text Markup Language | Structure of Web Page           |
| CSS        | Cascading Style Sheets     | Styling and Design              |
| JavaScript | JavaScript                 | Functionality and Interactivity |

---

# What is HTML?

HTML stands for **Hyper Text Markup Language**.

HTML is used to create the structure of web pages.

HTML consists of **Tags**.

Example:

```html
<h1>Welcome to HTML</h1>
```

Here:

```html
<h1>
```

is Opening Tag

```html
</h1>
```

is Closing Tag

Everything between them is called Content.

---

# Basic Structure of HTML Document

```html
<!DOCTYPE html>
<html>

<head>
    <title>My First Website</title>
</head>

<body>

</body>

</html>
```

## Explanation

### 1. DOCTYPE

```html
<!DOCTYPE html>
```

Tells browser that the document is HTML5.

---

### 2. HTML Tag

```html
<html>
</html>
```

Root element of the webpage.

Everything should be written inside this tag.

---

### 3. Head Tag

```html
<head>
</head>
```

Contains information about webpage.

Examples:

* Title
* CSS Links
* Meta Tags

---

### 4. Title Tag

```html
<title>My Website</title>
```

Displays title in browser tab.

---

### 5. Body Tag

```html
<body>
</body>
```

Contains all visible content.

Examples:

* Headings
* Paragraphs
* Images
* Links
* Lists

---

# Heading Tags

Used to display headings.

HTML provides 6 heading tags.

```html
<h1>Heading 1</h1>
<h2>Heading 2</h2>
<h3>Heading 3</h3>
<h4>Heading 4</h4>
<h5>Heading 5</h5>
<h6>Heading 6</h6>
```

## Output Size

Largest → Smallest

```text
h1
h2
h3
h4
h5
h6
```

### Example

```html
<h1>Frontend Development</h1>
<h2>HTML</h2>
<h3>CSS</h3>
<h4>JavaScript</h4>
```

---

# Paragraph Tag

Used to write paragraphs.

Syntax:

```html
<p>Content</p>
```

Example:

```html
<p>
HTML is used to create web pages.
</p>
```

---

# Line Break Tag

Used to move content to next line.

Syntax:

```html
<br>
```

Example:

```html
HTML<br>
CSS<br>
JavaScript
```

Output:

```text
HTML
CSS
JavaScript
```

---

# Horizontal Rule Tag

Used to create horizontal line.

Syntax:

```html
<hr>
```

Example:

```html
<p>Section 1</p>

<hr>

<p>Section 2</p>
```

Output:

---

---

# Text Formatting Tags

HTML provides various tags to format text.

---

## Bold Tag

Makes text bold.

Syntax:

```html
<b>Content</b>
```

Example:

```html
<b>Java Programming</b>
```

Output:

**Java Programming**

---

## Italic Tag

Makes text italic.

Syntax:

```html
<i>Content</i>
```

Example:

```html
<i>Java Programming</i>
```

Output:

*Java Programming*

---

## Underline Tag

Adds underline.

Syntax:

```html
<u>Content</u>
```

Example:

```html
<u>Java Programming</u>
```

Output:

<u>Java Programming</u>

---

## Mark Tag

Used to highlight text.

Syntax:

```html
<mark>Content</mark>
```

Example:

```html
<mark>Important Topic</mark>
```

Output:

Highlighted Text

---

# Superscript Tag

Displays content above normal text.

Used for powers.

Syntax:

```html
<sup></sup>
```

Example:

```html
x<sup>2</sup>
```

Output:

x²

More Examples:

```html
a<sup>2</sup> + b<sup>2</sup>
```

---

# Subscript Tag

Displays content below normal text.

Used in Chemistry formulas.

Syntax:

```html
<sub></sub>
```

Example:

```html
H<sub>2</sub>O
```

Output:

H₂O

More Examples:

```html
CO<sub>2</sub>

O<sub>2</sub>

NH<sub>3</sub>
```

---

# Lists in HTML

Lists are used to display grouped items.

Types:

1. Ordered List
2. Unordered List

---

# Ordered List

Displays items with sequence.

Syntax:

```html
<ol>

   <li>Item</li>

</ol>
```

Example:

```html
<ol>

   <li>Java</li>
   <li>Python</li>
   <li>SQL</li>

</ol>
```

Output:

1. Java
2. Python
3. SQL

---

# Ordered List Types

Using type attribute.

---

## Numbers

```html
<ol type="1">
```

Output:

```text
1
2
3
```

---

## Capital Letters

```html
<ol type="A">
```

Output:

```text
A
B
C
```

---

## Small Letters

```html
<ol type="a">
```

Output:

```text
a
b
c
```

---

## Capital Roman Numbers

```html
<ol type="I">
```

Output:

```text
I
II
III
```

---

## Small Roman Numbers

```html
<ol type="i">
```

Output:

```text
i
ii
iii
```

---

# Start Attribute

Used to start list from specific value.

Example:

```html
<ol type="1" start="5">

   <li>Java</li>
   <li>Python</li>
   <li>SQL</li>

</ol>
```

Output:

```text
5. Java
6. Python
7. SQL
```

---

# Unordered List

Displays bullet points.

Syntax:

```html
<ul>

   <li>Item</li>

</ul>
```

Example:

```html
<ul>

   <li>Java</li>
   <li>Python</li>
   <li>SQL</li>

</ul>
```

Output:

• Java

• Python

• SQL

---

# Types of Unordered List

---

## Disc

```html
<ul type="disc">
```

Output:

●

---

## Circle

```html
<ul type="circle">
```

Output:

○

---

## Square

```html
<ul type="square">
```

Output:

■

---

# Nested List

List inside another list is called Nested List.

Example:

```html
<ol>

   <li>Frontend</li>

   <ul>

      <li>HTML</li>
      <li>CSS</li>
      <li>JavaScript</li>

   </ul>

   <li>Backend</li>

   <ul>

      <li>Java</li>
      <li>Spring</li>
      <li>MySQL</li>

   </ul>

</ol>
```

Output:

```text
1. Frontend
   ■ HTML
   ■ CSS
   ■ JavaScript

2. Backend
   ○ Java
   ○ Spring
   ○ MySQL
```

---

# Hyperlinks

Hyperlinks are used to navigate from one page to another page.

Syntax:

```html
<a href="URL">Content</a>
```

Example:

```html
<a href="https://www.flipkart.com">
    Flipkart
</a>
```

When user clicks Flipkart text, browser opens Flipkart website.

---

# Images in HTML

Used to display pictures.

Syntax:

```html
<img src="image.jpg">
```

Example:

```html
<img src="myimage.jpeg">
```

---

# Width and Height

Used to control image size.

Example:

```html
<img
src="myimage.jpeg"
width="200px"
height="200px">
```

## Pixel (px)

px = Pixel

Pixel is the smallest unit on screen.

Example:

```html
width="100px"
height="100px"
```

Small image

```html
width="500px"
height="500px"
```

Large image

---

# Mini Student Profile Project

```html
<!DOCTYPE html>
<html>

<head>
    <title>Student Profile</title>
</head>

<body>

<h1>Udhay Profile</h1>

<hr>

<p>
I am <b>Udhay</b>,
<u>B.Tech Final Year Student</u>
at
<i>SRM University</i>.
</p>

<p>
Skilled in
<mark>
Core Java,
Advanced Java,
JDBC,
MySQL
</mark>
</p>

<hr>

<h2>Skills</h2>

<ul type="square">
    <li>Core Java</li>
    <li>Advanced Java</li>
    <li>MySQL</li>
</ul>

<hr>

<h2>Education</h2>

<ol>
    <li>SSC</li>
    <li>Intermediate</li>
    <li>B.Tech</li>
</ol>

<hr>

<a href="https://www.flipkart.com">
Visit Flipkart
</a>

<br><br>

<img
src="myimage.jpeg"
width="200px"
height="200px">

</body>

</html>
```

---

#   Practice Tasks

## Task 1

Create webpage containing:

* Your Name
* College Name
* Course
* Skills

Using:

* h1
* p
* b
* i
* u

---

## Task 2

Create webpage showing:

* H₂O
* CO₂
* x²
* y³

Using:

* sub
* sup

---

## Task 3

Create Ordered List using:

* Numbers
* Capital Letters
* Small Letters
* Roman Numbers

---

## Task 4

Create Unordered List using:

* Disc
* Circle
* Square

---

## Task 5

Create Nested List for:

```text
Frontend
    HTML
    CSS
    JavaScript

Backend
    Core Java
    Spring
    MySQL
```

---

#   Interview Questions

### Q1. What is HTML?

HTML stands for Hyper Text Markup Language used to create structure of web pages.

---

### Q2. What is a tag?

A tag is a predefined keyword enclosed inside angle brackets.

Example:

```html
<h1>
```

---

### Q3. Difference between Ordered List and Unordered List?

Ordered List:

```html
<ol>
```

Displays sequence.

Unordered List:

```html
<ul>
```

Displays bullets.

---

### Q4. What is Hyperlink?

A hyperlink is used to navigate from one webpage to another webpage.

---

### Q5. What is the use of img tag?

Used to display images on webpage.

---

#   Summary

Topics Covered:

 HTML Introduction

HTML Document Structure

Heading Tags

Paragraph Tag

Line Break Tag

Horizontal Rule

Bold Tag

Italic Tag

Underline Tag

Mark Tag

Superscript Tag

Subscript Tag

Ordered Lists

Unordered Lists

Nested Lists

Hyperlinks

Images

Width & Height Attributes

---

**End of   Notes**
# HTML Complete Notes -  

# Advanced HTML

## Topics Covered

1. HTML Attributes
2. Global Attributes
3. Hyperlinks Advanced
4. Absolute vs Relative Paths
5. Images Advanced
6. Tables Advanced
7. Rowspan and Colspan
8. Semantic HTML
9. HTML Entities
10. Audio Tag
11. Video Tag
12. iframe
13. Meta Tags
14. Mini Projects
15. Practice Tasks
16. Interview Questions

---

# What are Attributes?

Attributes provide additional information about HTML elements.

Syntax:

```html
<tag attribute="value">
```

Example:

```html
<a href="https://www.google.com">Google</a>
```

Here `href` is an attribute.

---

# Global Attributes

## id

Used to uniquely identify an element.

```html
<h1 id="heading1">Frontend</h1>
```

## class

Used to group multiple elements.

```html
<p class="student">Rahul</p>
<p class="student">Kiran</p>
```

## title

Shows tooltip on hover.

```html
<p title="Student Name">Rahul</p>
```

## hidden

Hides content.

```html
<p hidden>This is hidden</p>
```

## contenteditable

Allows editing.

```html
<p contenteditable="true">Edit me</p>
```

## draggable

Makes element draggable.

```html
<img src="image.jpg" draggable="true">
```

---

# Hyperlinks Advanced

## External Link

```html
<a href="https://www.google.com">Google</a>
```

## Internal Link

```html
<a href="about.html">About</a>
```

## Open in New Tab

```html
<a href="https://google.com" target="_blank">
Google
</a>
```

## Email Link

```html
<a href="mailto:test@gmail.com">
Send Mail
</a>
```

## Telephone Link

```html
<a href="tel:9876543210">
Call Now
</a>
```

## Download Link

```html
<a href="resume.pdf" download>
Download Resume
</a>
```

## Bookmark Link

```html
<a href="#contact">
Go To Contact
</a>
```

Destination:

```html
<h2 id="contact">
Contact Section
</h2>
```

---

# Absolute vs Relative Paths

## Absolute Path

```html
<img src="https://picsum.photos/200">
```

## Relative Path

```html
<img src="images/profile.jpg">
```

---

# Images Advanced

```html
<img
src="profile.jpg"
alt="Student Image"
title="Profile"
width="200"
height="200">
```

### alt

Alternative text when image fails.

### width

Controls image width.

### height

Controls image height.

### title

Tooltip on hover.

---

# Tables Advanced

## Table Structure

```html
<table border="1">

<tr>
<th>Name</th>
<th>Marks</th>
</tr>

<tr>
<td>Rahul</td>
<td>95</td>
</tr>

</table>
```

## caption

```html
<table>
<caption>Student Details</caption>
</table>
```

## thead

Header section.

## tbody

Body section.

## tfoot

Footer section.

---

# Rowspan

```html
<td rowspan="2">Rahul</td>
```

Used to merge rows vertically.

---

# Colspan

```html
<th colspan="2">
Student Details
</th>
```

Used to merge columns horizontally.

---

# Semantic HTML

## Why Semantic HTML?

Semantic tags clearly describe their meaning.

### header

```html
<header>
Website Header
</header>
```

### nav

```html
<nav>
Home About Contact
</nav>
```

### main

```html
<main>
Main Content
</main>
```

### section

```html
<section>
Course Information
</section>
```

### article

```html
<article>
Blog Content
</article>
```

### aside

```html
<aside>
Latest Updates
</aside>
```

### footer

```html
<footer>
Copyright 2026
</footer>
```

---

# HTML Entities

## Less Than

```html
&lt;
```

## Greater Than

```html
&gt;
```

## Copyright

```html
&copy;
```

## Registered

```html
&reg;
```

## Rupee

```html
&#8377;
```

## Non Breaking Space

```html
&nbsp;
```

---

# Audio Tag

```html
<audio controls>
<source src="song.mp3" type="audio/mp3">
</audio>
```

Attributes:

- controls
- autoplay
- loop
- muted

---

# Video Tag

```html
<video width="500" controls>
<source src="video.mp4" type="video/mp4">
</video>
```

Attributes:

- controls
- autoplay
- muted
- loop

---

# iframe

## YouTube

```html
<iframe
width="500"
height="300"
src="https://www.youtube.com/embed/VIDEO_ID">
</iframe>
```

## Google Maps

```html
<iframe src="MAP_URL"></iframe>
```

---

# Meta Tags

```html
<meta charset="UTF-8">
```

```html
<meta
name="viewport"
content="width=device-width, initial-scale=1.0">
```

```html
<meta
name="description"
content="Frontend Course">
```

```html
<meta
name="keywords"
content="HTML,CSS,JavaScript">
```

```html
<meta
name="author"
content="Maheswaram">
```

---

# Practice Tasks

1. Create Employee Table.
2. Create Student Result Sheet.
3. Create Bookmark Navigation.
4. Add Image Hyperlink.
5. Embed YouTube Video.
6. Create Semantic Layout.
7. Add Audio and Video.

---

# Interview Questions

## What is an attribute?

Additional information provided to an HTML element.

## Difference between id and class?

id → unique

class → reusable

## What is rowspan?

Merges rows vertically.

## What is colspan?

Merges columns horizontally.

## What is semantic HTML?

HTML tags that describe their purpose.

## What is iframe?

Used to embed another webpage.

## What is alt attribute?

Alternative text displayed when image fails.

---

#   Summary

Topics Covered:

- Attributes
- Hyperlinks
- Paths
- Images
- Tables
- Rowspan
- Colspan
- Semantic HTML
- HTML Entities
- Audio
- Video
- iframe
- Meta Tags



Save as:

```text
day2.html
```

```html
<!DOCTYPE html>
<html lang="en">

<head>

    <meta charset="UTF-8">

    <meta
        name="viewport"
        content="width=device-width, initial-scale=1.0">

    <meta
        name="description"
        content="Advanced HTML  ">

    <meta
        name="keywords"
        content="HTML,CSS,JavaScript">

    <meta
        name="author"
        content="Maheswaram">

    <title>Advanced HTML -  </title>

</head>

<body>

    <!-- =============================== -->
    <!-- HEADER -->
    <!-- =============================== -->

    <header>

        <h1 align="center">
            HTML Advanced Concepts
        </h1>

        <p align="center">
            Complete   Demonstration File
        </p>

    </header>

    <hr>

    <!-- =============================== -->
    <!-- ATTRIBUTES -->
    <!-- =============================== -->

    <section>

        <h2>1. Global Attributes</h2>

        <p title="Tooltip Example">
            Hover over me
        </p>

        <p contenteditable="true">
            Edit this content
        </p>

        <p hidden>
            Hidden Paragraph
        </p>

        <img
            src="https://picsum.photos/150"
            draggable="true">

    </section>

    <hr>

    <!-- =============================== -->
    <!-- HYPERLINKS -->
    <!-- =============================== -->

    <section>

        <h2>2. Hyperlinks</h2>

        <a href="https://www.google.com">
            Open Google
        </a>

        <br><br>

        <a
            href="https://www.flipkart.com"
            target="_blank">

            Open Flipkart New Tab

        </a>

        <br><br>

        <a href="mailto:test@gmail.com">

            Send Email

        </a>

        <br><br>

        <a href="tel:9876543210">

            Call Now

        </a>

        <br><br>

        <a href="resume.pdf" download>

            Download Resume

        </a>

    </section>

    <hr>

    <!-- =============================== -->
    <!-- BOOKMARK LINKS -->
    <!-- =============================== -->

    <section>

        <h2>3. Bookmark Navigation</h2>

        <a href="#contact">

            Go To Contact Section

        </a>

    </section>

    <hr>

    <!-- =============================== -->
    <!-- ABSOLUTE PATH -->
    <!-- =============================== -->

    <section>

        <h2>4. Absolute Path Image</h2>

        <img
            src="https://picsum.photos/200"
            width="200"
            height="200">

    </section>

    <hr>

    <!-- =============================== -->
    <!-- RELATIVE PATH -->
    <!-- =============================== -->

    <section>

        <h2>5. Relative Path Example</h2>

        <img
            src="images/profile.jpg"
            alt="Local Image"
            width="200">

    </section>

    <hr>

    <!-- =============================== -->
    <!-- IMAGE ATTRIBUTES -->
    <!-- =============================== -->

    <section>

        <h2>6. Image Attributes</h2>

        <img
            src="https://picsum.photos/250"
            alt="Sample Image"
            title="Profile Picture"
            width="250"
            height="250">

    </section>

    <hr>

    <!-- =============================== -->
    <!-- IMAGE HYPERLINK -->
    <!-- =============================== -->

    <section>

        <h2>7. Image Hyperlink</h2>

        <a href="https://www.google.com">

            <img
                src="https://picsum.photos/300"
                width="300">

        </a>

    </section>

    <hr>

    <!-- =============================== -->
    <!-- TABLE BASIC -->
    <!-- =============================== -->

    <section>

        <h2>8. Student Table</h2>

        <table border="1">

            <caption>

                Student Details

            </caption>

            <thead>

                <tr>

                    <th>ID</th>
                    <th>Name</th>
                    <th>Course</th>

                </tr>

            </thead>

            <tbody>

                <tr>

                    <td>101</td>
                    <td>Rahul</td>
                    <td>Java</td>

                </tr>

                <tr>

                    <td>102</td>
                    <td>Kiran</td>
                    <td>Python</td>

                </tr>

            </tbody>

            <tfoot>

                <tr>

                    <td colspan="3">

                        Total Students : 2

                    </td>

                </tr>

            </tfoot>

        </table>

    </section>

    <hr>

    <!-- =============================== -->
    <!-- ROWSPAN -->
    <!-- =============================== -->

    <section>

        <h2>9. Rowspan Example</h2>

        <table border="1">

            <tr>

                <th>Name</th>
                <th>Subject</th>

            </tr>

            <tr>

                <td rowspan="2">

                    Rahul

                </td>

                <td>Java</td>

            </tr>

            <tr>

                <td>Python</td>

            </tr>

        </table>

    </section>

    <hr>

    <!-- =============================== -->
    <!-- COLSPAN -->
    <!-- =============================== -->

    <section>

        <h2>10. Colspan Example</h2>

        <table border="1">

            <tr>

                <th colspan="2">

                    Student Information

                </th>

            </tr>

            <tr>

                <td>Name</td>
                <td>Rahul</td>

            </tr>

        </table>

    </section>

    <hr>

    <!-- =============================== -->
    <!-- ROWSPAN + COLSPAN -->
    <!-- =============================== -->

    <section>

        <h2>11. Rowspan + Colspan</h2>

        <table border="1">

            <tr>

                <th rowspan="2">

                    Student

                </th>

                <th colspan="2">

                    Marks

                </th>

            </tr>

            <tr>

                <th>HTML</th>
                <th>CSS</th>

            </tr>

            <tr>

                <td>Rahul</td>
                <td>95</td>
                <td>90</td>

            </tr>

        </table>

    </section>

    <hr>

    <!-- =============================== -->
    <!-- HTML ENTITIES -->
    <!-- =============================== -->

    <section>

        <h2>12. HTML Entities</h2>

        <p>Less Than : &lt;</p>

        <p>Greater Than : &gt;</p>

        <p>Copyright : &copy;</p>

        <p>Registered : &reg;</p>

        <p>Rupee : &#8377;</p>

        <p>Heart : &#10084;</p>

        <p>Hello&nbsp;&nbsp;&nbsp;World</p>

    </section>

    <hr>

    <!-- =============================== -->
    <!-- AUDIO -->
    <!-- =============================== -->

    <section>

        <h2>13. Audio Tag</h2>

        <audio controls>

            <source
                src="sample.mp3"
                type="audio/mp3">

        </audio>

    </section>

    <hr>

    <!-- =============================== -->
    <!-- VIDEO -->
    <!-- =============================== -->

    <section>

        <h2>14. Video Tag</h2>

        <video
            width="400"
            controls>

            <source
                src="sample.mp4"
                type="video/mp4">

        </video>

    </section>

    <hr>

    <!-- =============================== -->
    <!-- IFRAME -->
    <!-- =============================== -->

    <section>

        <h2>15. YouTube iframe</h2>

        <iframe
            width="560"
            height="315"
            src="https://www.youtube.com/embed/tgbNymZ7vqY">

        </iframe>

    </section>

    <hr>

    <!-- =============================== -->
    <!-- GOOGLE MAP -->
    <!-- =============================== -->

    <section>

        <h2>16. Google Maps iframe</h2>

        <iframe
            src="https://maps.google.com/maps?q=hyderabad&t=&z=13&ie=UTF8&iwloc=&output=embed"
            width="500"
            height="300">

        </iframe>

    </section>

    <hr>

    <!-- =============================== -->
    <!-- SEMANTIC HTML -->
    <!-- =============================== -->

    <section>

        <h2>17. Semantic HTML Layout</h2>

        <header>

            <h3>Website Header</h3>

        </header>

        <nav>

            <a href="#">Home</a> |

            <a href="#">About</a> |

            <a href="#">Courses</a> |

            <a href="#">Contact</a>

        </nav>

        <main>

            <section>

                <h3>Frontend Course</h3>

                <p>
                    HTML CSS JavaScript
                </p>

            </section>

            <article>

                <h3>Blog Article</h3>

                <p>
                    This is article content.
                </p>

            </article>

            <aside>

                Latest Updates Section

            </aside>

        </main>

        <footer>

            <p>

                Copyright 2026

            </p>

        </footer>

    </section>

    <hr>

    <!-- =============================== -->
    <!-- MINI PROJECT -->
    <!-- =============================== -->

    <section>

        <h2>18. College Timetable</h2>

        <table border="1">

            <tr>

                <th>Day</th>
                <th>9-10</th>
                <th>10-11</th>
                <th>11-12</th>

            </tr>

            <tr>

                <td>Monday</td>
                <td>HTML</td>
                <td>CSS</td>
                <td>JavaScript</td>

            </tr>

            <tr>

                <td>Tuesday</td>
                <td>Java</td>
                <td>SQL</td>
                <td>Spring</td>

            </tr>

        </table>

    </section>

    <hr>

    <!-- =============================== -->
    <!-- CONTACT -->
    <!-- =============================== -->

    <section id="contact">

        <h2>Contact Section</h2>

        <p>Email : support@gmail.com</p>

        <p>Phone : 9876543210</p>

    </section>

    <hr>

    <h2 align="center">

          Advanced HTML Completed

    </h2>

</body>

</html>
```
---

# Mini Project 1

Student Details Table

# Mini Project 2

College Timetable

# Mini Project 3

Semantic Webpage Layout

Header + Nav + Main + Footer

---

# Mini Project 1: Student Details Table

## Objective

Create a student information table using HTML tables.

## Requirements

Create a webpage with the title:

```html
Student Details
```

Add a table containing:

| ID  | Name  | Course            | Email                                     | Phone      |
| --- | ----- | ----------------- | ----------------------------------------- | ---------- |
| 101 | Ravi  | Java Full Stack   | [ravi@gmail.com](mailto:ravi@gmail.com)   | 9876543210 |
| 102 | Priya | Python Full Stack | [priya@gmail.com](mailto:priya@gmail.com) | 9876543211 |
| 103 | Arjun | Data Science      | [arjun@gmail.com](mailto:arjun@gmail.com) | 9876543212 |
| 104 | Sneha | UI/UX Design      | [sneha@gmail.com](mailto:sneha@gmail.com) | 9876543213 |
| 105 | Kiran | Cyber Security    | [kiran@gmail.com](mailto:kiran@gmail.com) | 9876543214 |

---

## Concepts Student Must Use

### Table Tags

```html
<table>
<tr>
<th>
<td>
```

### Formatting

```html
<h1>
<hr>
```

### Table Attributes

```html
border
cellpadding
cellspacing
```

Example:

```html
<table border="1" cellpadding="10" cellspacing="0">
```

---

## Expected Output

```text
Student Details

-------------------------------------------------

+-----+---------+-----------------+-------------------+------------+
| ID  | Name    | Course          | Email             | Phone      |
+-----+---------+-----------------+-------------------+------------+
|101  | Ravi    | Java Full Stack | ravi@gmail.com    |9876543210  |
|102  | Priya   | Python Full Stack|priya@gmail.com   |9876543211  |
|103  | Arjun   | Data Science    | arjun@gmail.com   |9876543212  |
|104  | Sneha   | UI/UX Design    | sneha@gmail.com   |9876543213  |
|105  | Kiran   | Cyber Security  | kiran@gmail.com   |9876543214  |
+-----+---------+-----------------+-------------------+------------+
```

---

# Mini Project 2: College Timetable

## Objective

Create a weekly college timetable using HTML tables.

---

## Requirements

Create a table with:

```text
Monday
Tuesday
Wednesday
Thursday
Friday
Saturday
```

Time slots:

```text
9:00 - 10:00
10:00 - 11:00
11:00 - 12:00
12:00 - 1:00
2:00 - 3:00
3:00 - 4:00
```

Subjects:

```text
HTML
CSS
JavaScript
Core Java
SQL
Aptitude
```

Include:

```text
Lunch Break
```

using:

```html
colspan
```

---

## Concepts Student Must Use

### Table Tags

```html
<table>
<tr>
<th>
<td>
```

### Table Attributes

```html
border
cellpadding
cellspacing
```

### Special Table Feature

```html
colspan
```

Example:

```html
<td colspan="6">Lunch Break</td>
```

---

## Expected Learning

Students understand:

* Large Tables
* Row & Column Management
* colspan
* Data Organization

---

# Mini Project 3: Semantic Webpage Layout

## Objective

Create a complete webpage structure using semantic HTML tags.

---

## Requirements

Create the following layout:

```text
---------------------------------
            HEADER
---------------------------------

HOME | ABOUT | COURSES | CONTACT

---------------------------------
              MAIN
---------------------------------

Welcome to Our Training Institute

We provide:

• Java Full Stack
• Python Full Stack
• Data Science
• UI/UX Design

---------------------------------
             FOOTER
---------------------------------

© 2026 Training Institute
```

---

## Mandatory Semantic Tags

Students must use:

```html
<header>
<nav>
<main>
<section>
<footer>
```

---

## Concepts Student Must Use

### Headings

```html
<h1>
<h2>
```

### Paragraph

```html
<p>
```

### Lists

```html
<ul>
<li>
```

### Horizontal Line

```html
<hr>
```

### Links

```html
<a>
```

Example:

```html
<a href="#">Home</a>
<a href="#">About</a>
<a href="#">Courses</a>
<a href="#">Contact</a>
```

---

# Skills Covered by These 3 Projects

| Topic                | Project      |
| -------------------- | ------------ |
| Headings             | 3            |
| Paragraphs           | 3            |
| Horizontal Line      | 1,2,3        |
| Lists                | 3            |
| Links                | 3            |
| Tables               | 1,2          |
| Rows & Columns       | 1,2          |
| colspan              | 2            |
| Semantic Tags        | 3            |
| Basic Page Structure | 3            |
| HTML Boilerplate     | All Projects |


**End of Day2**


#   - HTML Semantic Tags & CSS Basics

## Topics Covered

* `<div>` Tag
* `<span>` Tag
* `data-*` Attributes
* `<details>` & `<summary>` Tags
* Progress Bar
* Meter Tag
* Figure & Figcaption
* Abbreviation Tag
* Code Tag
* Introduction to CSS
* CSS Selectors

  * Tag Selector
  * ID Selector
  * Class Selector

---

# HTML DIV Tag

The `<div>` tag is a block-level container used to group multiple HTML elements together.

### Syntax

```html
<div>
    <h1>Student Service Community</h1>
    <p>SSC is a community for student services.</p>
</div>
```

### Output

Student Service Community

SSC is a community for student services.

### Uses

* Group related elements
* Create webpage sections
* Apply CSS styling to multiple elements

---

# HTML SPAN Tag

The `<span>` tag is an inline container used to style or manipulate a portion of text.

### Syntax

```html
<p>
    <span>SSC</span> is a community for student services.
</p>
```

### CSS Example

```css
span{
    color: blue;
    font-weight: bold;
}
```

### Uses

* Style specific text
* Apply colors
* Highlight words
* Inline content formatting

---

# HTML data-* Attribute

Used to store custom data inside HTML elements.

### Syntax

```html
<button data-id="101">
    Click Me
</button>
```

### Why Use?

Custom data can later be accessed using JavaScript.

Example:

```javascript
let id = button.dataset.id;
```

### Uses

* Store IDs
* Product information
* User information
* Dynamic content handling

---

# HTML Details Tag

Creates collapsible content sections.

### Syntax

```html
<details>
    <summary>Register</summary>

    <p>
        Register for the challenge.
    </p>
</details>
```

### Output

> Register

(Click to expand)

### Uses

* FAQ Sections
* Instructions
* Hidden content
* Read More functionality

---

# HTML Summary Tag

Used inside the `<details>` tag as the clickable heading.

### Syntax

```html
<details>

    <summary>Start Coding</summary>

    <p>Begin solving problems.</p>

</details>
```

---

# HTML Progress Bar

Represents task completion progress.

### Syntax

```html
<progress value="70" max="100"></progress>
```

### Example

```html
Java

<progress value="90" max="100"></progress>
```

### Uses

* Course completion
* Download progress
* Project tracking
* Task completion

---

# HTML Meter Tag

Represents a measurement within a known range.

### Syntax

```html
<meter value="8" min="0" max="10"></meter>
```

### Example

```html
Skill Level

<meter value="9" min="0" max="10"></meter>
```

### Uses

* Skill rating
* Battery level
* Performance score
* Temperature indicator

---

# HTML Figure Tag

Represents self-contained content such as images, diagrams, charts, etc.

### Syntax

```html
<figure>

    <img src="image.jpg">

</figure>
```

### Uses

* Images
* Charts
* Diagrams
* Illustrations

---

# HTML Figcaption Tag

Adds a caption to a figure.

### Syntax

```html
<figure>

    <img src="image.jpg">

    <figcaption>
        Professional Image
    </figcaption>

</figure>
```

### Output

Image

Professional Image

---

# HTML Abbreviation Tag

Displays abbreviated text with a tooltip explanation.

### Syntax

```html
<abbr title="HyperText Markup Language">
    HTML
</abbr>
```

### Example

```html
<abbr title="World Health Organization">
    WHO
</abbr>
```

### Uses

* Short forms
* Technical terms
* Organization names

---

# HTML Code Tag

Used to display code snippets.

### Syntax

```html
<code>
System.out.println("Hello Java");
</code>
```

### Example

Output:

```java
System.out.println("Hello Java");
```

### Uses

* Programming tutorials
* Documentation
* Technical blogs

---

# Introduction to CSS

CSS stands for:

```text
Cascading Style Sheets
```

CSS is used to design and style webpages.

It controls:

* Colors
* Fonts
* Spacing
* Layout
* Borders
* Animations

---

# Internal CSS

CSS written inside the `<style>` tag.

### Syntax

```html
<head>

<style>

h1{
    color:red;
}

</style>

</head>
```

---

# CSS Syntax

```css
selector{
    property:value;
}
```

Example:

```css
h1{
    color:red;
}
```

### Components

* Selector → Target Element
* Property → What to change
* Value → New value

---

# CSS Selectors

Selectors are used to target HTML elements.

There are 3 important selectors:

1. Tag Selector
2. ID Selector
3. Class Selector

---

# 1. Tag Selector

Targets all elements with the same tag name.

### Syntax

```css
h1{
    color:red;
}
```

### HTML

```html
<h1>Hello</h1>
<h1>Welcome</h1>
```

### Output

Both headings become red.

---

# 2. ID Selector

Used to uniquely style a single element.

### HTML

```html
<h1 id="title">
    Welcome
</h1>
```

### CSS

```css
#title{
    color:green;
}
```

### Rules

* ID should be unique.
* One element should have one ID.

---

# 3. Class Selector

Used to style multiple elements together.

### HTML

```html
<h1 class="heading">
    HTML
</h1>

<h2 class="heading">
    CSS
</h2>
```

### CSS

```css
.heading{
    color:blue;
}
```

### Output

Both elements become blue.

---

# Difference Between ID and Class

| Feature           | ID  | Class |
| ----------------- | --- | ----- |
| Symbol            | #   | .     |
| Unique            | Yes | No    |
| Multiple Elements | No  | Yes   |
| Reusable          | No  | Yes   |

### Example

```html
<h1 id="mainHeading">
    Welcome
</h1>

<p class="content">
    Paragraph 1
</p>

<p class="content">
    Paragraph 2
</p>
```

```css
#mainHeading{
    color:red;
}

.content{
    color:blue;
}
```

---
#   - HTML Semantic Tags & CSS Basics

## Complete Example Project

This project demonstrates:

* Div Tag
* Span Tag
* data-* Attribute
* Details Tag
* Summary Tag
* Progress Bar
* Meter Tag
* Figure & Figcaption
* Abbreviation Tag
* Code Tag
* Internal CSS
* Tag Selector
* ID Selector
* Class Selector

---

## Complete Code

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>  HTML & CSS Concepts</title>

    <style>

        /* Tag Selector */
        span{
            color: blue;
            font-weight: bold;
            font-size: 20px;
        }

        h1{
            color: brown;
        }

        button{
            background-color: blue;
            color: white;
            border: none;
            padding: 10px;
            border-radius: 10px;
            cursor: pointer;
        }

        /* Class Selector */
        .leetcode{
            color: blue;
            font-size: 40px;
            font-weight: bold;
        }

        .heading{
            color: blue;
            font-size: 20px;
        }

        /* ID Selector */
        #h1-dis{
            color: black;
            font-size: 40px;
            font-weight: bold;
        }

    </style>

</head>

<body>

    <!-- DIV TAG -->

    <h2>DIV Tag</h2>

    <div>
        <h1>Student Service Community SSC</h1>
        <p>SSC is a community for student services.</p>
    </div>

    <hr>

    <!-- SPAN TAG -->

    <h2>SPAN Tag</h2>

    <p>
        <span>SSC</span> is a community for student services.
    </p>

    <p>
        <span>Student Service Community</span>
    </p>

    <hr>

    <!-- CLASS AND ID SELECTOR EXAMPLE -->

    <section>

        <h1 class="heading">
            #DSAwithApexSwaram
        </h1>

        <h1 id="h1-dis">
            100 Days
            <span class="leetcode">LeetCode</span>
            Challenge
        </h1>

        <p>
            By <span>ApexSwaram</span>
        </p>

        <p>
            Join the 100 Days LeetCode Challenge and improve your
            coding skills by solving problems daily.
        </p>

        <button>
            LeetCode Problems
        </button>

    </section>

    <hr>

    <!-- DATA ATTRIBUTE -->

    <h2>data-* Attribute</h2>

    <button data-id="101">
        Click Me
    </button>

    <hr>

    <!-- DETAILS TAG -->

    <h2>Details Tag</h2>

    <details>

        <summary>Register</summary>

        <p>
            Register for the challenge and confirm participation.
        </p>

    </details>

    <details>

        <summary>Start Coding</summary>

        <p>
            Begin solving the assigned coding problems.
        </p>

    </details>

    <details>

        <summary>Submit Progress</summary>

        <p>
            Share your progress on LinkedIn.
        </p>

    </details>

    <details>

        <summary>Learn & Grow</summary>

        <p>
            Participate in discussions and clear doubts.
        </p>

    </details>

    <details>

        <summary>Certification</summary>

        <p>
            Complete the challenge to receive a certificate.
        </p>

    </details>

    <hr>

    <!-- PROGRESS BAR -->

    <h2>Progress Bar</h2>

    HTML <br>
    <progress value="70" max="100"></progress>

    <br><br>

    CSS <br>
    <progress value="60" max="100"></progress>

    <br><br>

    JavaScript <br>
    <progress value="40" max="100"></progress>

    <br><br>

    Core Java <br>
    <progress value="90" max="100"></progress>

    <br><br>

    MySQL <br>
    <progress value="80" max="100"></progress>

    <hr>

    <!-- METER TAG -->

    <h2>Meter Tag</h2>

    Skill Rating

    <br><br>

    <meter value="8" min="0" max="10"></meter>

    <hr>

    <!-- FIGURE AND FIGCAPTION -->

    <h2>Figure & Figcaption</h2>

    <figure>

        <img
            src="https://res.cloudinary.com/doogigafl/image/upload/v1781450206/Passport_Size_Photo_cwtt3p.jpg"
            height="200"
            width="200"
        >

        <figcaption>
            Professional Image
        </figcaption>

    </figure>

    <hr>

    <!-- ABBR TAG -->

    <h2>Abbreviation Tag</h2>

    <abbr title="HyperText Markup Language">
        HTML
    </abbr>

    <br><br>

    <abbr title="World Health Organization">
        WHO
    </abbr>

    <hr>

    <!-- CODE TAG -->

    <h2>Code Tag</h2>

    <code>
        System.out.println("Hello Java");
    </code>

</body>

</html>
```

---
# Assignment 1: Student Portfolio Website

## Objective

Create a complete Student Portfolio Website using all concepts learned in  ,  , and  .

---

## Requirements

### Header Section

Display:

* Student Name using Heading Tag
* Short Introduction using Paragraph Tag
* Horizontal Rule

---

### About Me Section

Use:

* div
* span
* bold
* italic
* underline
* mark

Example:

* Name
* Course
* Career Goal
* Skills

---

### Skills Section

Use:

* Ordered List
* Unordered List
* Nested List

Example:

Frontend Skills

* HTML
* CSS

Backend Skills

* Java
* JDBC
* Servlets

---

### Education Section

Create a Table containing:

* Qualification
* Institution
* Year
* Percentage

Use:

* table
* rowspan
* colspan

---

### Learning Progress Section

Use Progress Bars for:

* HTML
* CSS
* JavaScript
* Java
* SQL

Use Meter Tag for:

* Communication Skills
* Problem Solving
* Team Work

---

### Certifications Section

Use Details Tag.

Each certificate should open when clicked.

Example:

* Java Certificate
* SQL Certificate
* DSA Certificate

---

### Project Section

Use:

* figure
* img
* figcaption

Display at least 3 projects.

---

### Contact Section

Add Hyperlinks:

* GitHub
* LinkedIn
* Email

---

## Expected Output

A complete personal portfolio website.
```
--------------------------------------------------
          STUDENT PORTFOLIO
--------------------------------------------------

Student Photo

Name: John Doe
Course: Full Stack Java Development

About Me
--------------------------------
Short introduction paragraph

Skills
--------------------------------
Frontend
 - HTML
 - CSS
 - JavaScript

Backend
 - Core Java
 - JDBC
 - Servlets

Education
--------------------------------
Table displaying qualification details

Learning Progress
--------------------------------
HTML      [=====80%=====]
CSS       [=====70%=====]
Java      [=====60%=====]

Projects
--------------------------------
Project Images with Captions

Certificates
--------------------------------
▶ Java Certificate
▶ SQL Certificate
▶ DSA Certificate

Contact
--------------------------------
GitHub
LinkedIn
Email
```
---
# Assignment 2: Full Stack Developer Learning Dashboard

## Objective

Build a learning dashboard that tracks your Full Stack Development journey.

---

## Sections

### Dashboard Title

Example:

# Full Stack Developer Roadmap

---

### Technologies Table

Create a table containing:

| Technology | Category | Status |
| ---------- | -------- | ------ |

Categories:

* Frontend
* Backend
* Database

Use rowspan and colspan.

---

### Learning Roadmap

Use Details Tag.

Example:

Frontend

* HTML
* CSS
* JavaScript

Backend

* Java
* JDBC
* Servlets

Database

* MySQL

Each category should expand and collapse.

---

### Progress Tracking

Use Progress Bars.

Example:

HTML → 80%

CSS → 60%

JavaScript → 40%

Java → 50%

MySQL → 70%

---

### Skill Rating

Use Meter Tag.

Rate yourself:

* Communication
* Coding
* Problem Solving
* Team Work

---

### Resource Section

Add Hyperlinks:

* W3Schools
* MDN
* GitHub

---

### Code Snippet Section

Use Code Tag.

Example:

```java
System.out.println("Hello World");
```

Display at least 5 code snippets.

---

### Styling Requirements

Create:

* One Tag Selector
* Two Class Selectors
* Two ID Selectors

---

## Expected Output
```

--------------------------------------------------
      FULL STACK LEARNING DASHBOARD
--------------------------------------------------

Roadmap Table

Frontend
Backend
Database

----------------------------------
Progress Tracking

HTML         [90%]
CSS          [80%]
JavaScript   [60%]
Java         [70%]

----------------------------------
Skill Ratings

Coding         [8/10]
Problem Solving[8/10]

----------------------------------
Learning Resources

GitHub
MDN
W3Schools

----------------------------------
Code Snippets

System.out.println("Hello Java");
```
# Assignment 3: Student Service Community (Mini Project)

## Objective

Create a landing page for "Student Service Community".

This project combines all concepts learned so far.

---

## Page Sections

### Hero Section

Display:

* Community Name
* Tagline
* Description
* Join Button

Use:

* Heading
* Paragraph
* Span
* Button

---

### Community Features

Create a list showing:

* Coding Practice
* Mock Interviews
* Resume Building
* Placement Training

Use nested lists.

---

### Learning Tracks

Create a table:

Frontend

Backend

Database

DSA

Use rowspan and colspan.

---

### Community Progress

Use progress bars.

Example:

Students Completed HTML

Students Completed CSS

Students Completed Java

Students Completed SQL

---

### Success Meter

Use meter tags showing:

* Placement Rate
* Course Completion Rate
* Student Satisfaction

---

### Community Gallery

Use:

* figure
* figcaption
* images

Minimum 4 images.

---

### FAQ Section

Use details and summary.

Minimum 5 FAQs.

---

### Resources Section

Add hyperlinks.

Example:

* GitHub Repository
* YouTube Channel
* LinkedIn Page

---

### Footer

Include:

* Copyright
* Contact Information
* Social Links

---

## Styling Requirements

Must use:

### Tag Selectors

Style:

* h1
* p
* button

### Class Selectors

Create:

* hero-section
* feature-card
* footer-section

### ID Selectors

Create:

* main-title
* contact-section

---

## Bonus Challenge

Add:

* Audio Tag
* Video Tag
* iframe (YouTube Video)

---

## Expected Output

```
--------------------------------------------------
       STUDENT SERVICE COMMUNITY
--------------------------------------------------

Learn • Build • Grow Together

Community Description

[ Join Community ]

----------------------------------
Features

✓ Coding Practice
✓ Resume Building
✓ Mock Interviews

----------------------------------
Learning Tracks Table

Frontend
Backend
Database
DSA

----------------------------------
Community Progress

HTML [80%]
CSS  [75%]
JAVA [65%]

----------------------------------
Community Gallery

Image 1
Image 2
Image 3
Image 4

----------------------------------
FAQ

▶ How do I join SSC?
▶ Is DSA mandatory?
▶ Will certificates be provided?

----------------------------------
Footer
```
#   Summary

Topics Covered:

* Div Tag
* Span Tag
* data-* Attribute
* Details Tag
* Summary Tag
* Progress Bar
* Meter Tag
* Figure Tag
* Figcaption Tag
* Abbreviation Tag
* Code Tag
* Internal CSS
* Tag Selector
* ID Selector
* Class Selector

---
#   CSS Complete Notes — Topics 1 to 25

> Prepared for JFS Batch students. Each topic includes: **Definition**, **HTML snippet**, and **Corresponding CSS**.

---

## 1. Color Property

**Definition:** The `color` property sets the text (foreground) color of an element.

```html
<p class="color-demo">This text is red.</p>
```

```css
.color-demo {
  color: red;
}
```

---

## 2. Background Color

**Definition:** The `background-color` property sets the background color of an element.

```html
<div class="bg-demo">Background Color Example</div>
```

```css
.bg-demo {
  background-color: yellow;
}
```

---

## 3. Font Family

**Definition:** The `font-family` property specifies the typeface used for text.

```html
<p class="font-family-demo">Times New Roman Font</p>
```

```css
.font-family-demo {
  font-family: 'Times New Roman';
}
```

---

## 4. Font Size

**Definition:** The `font-size` property controls the size of the text.

```html
<p class="font-size-demo">Font Size 30px</p>
```

```css
.font-size-demo {
  font-size: 30px;
}
```

---

## 5. Font Weight

**Definition:** The `font-weight` property controls the thickness/boldness of text.

```html
<p class="font-weight-demo">Bold Text Example</p>
```

```css
.font-weight-demo {
  font-weight: bold;
}
```

---

## 6. Font Style

**Definition:** The `font-style` property is mainly used to set italic text.

```html
<p class="font-style-demo">Italic Text Example</p>
```

```css
.font-style-demo {
  font-style: italic;
}
```

---

## 7. Text Align

**Definition:** The `text-align` property sets the horizontal alignment of text inside an element.

```html
<div class="text-align-demo">Centered Text</div>
```

```css
.text-align-demo {
  text-align: center;
}
```

---

## 8. Text Decoration

**Definition:** The `text-decoration` property adds or removes decoration lines from text (underline, overline, line-through, none).

```html
<p class="underline">Underline</p>
<p class="overline">Overline</p>
<p class="line-through">Line Through</p>
<a href="#" class="none">Link Without Underline</a>
```

```css
.underline {
  text-decoration: underline;
}
.overline {
  text-decoration: overline;
}
.line-through {
  text-decoration: line-through;
}
.none {
  text-decoration: none;
}
```

---

## 9. Text Transform

**Definition:** The `text-transform` property changes the capitalization of text (uppercase, lowercase, capitalize).

```html
<p class="uppercase">hello world</p>
<p class="lowercase">HELLO WORLD</p>
<p class="capitalize">hello world css</p>
```

```css
.uppercase {
  text-transform: uppercase;
}
.lowercase {
  text-transform: lowercase;
}
.capitalize {
  text-transform: capitalize;
}
```

---

## 10. Letter Spacing

**Definition:** The `letter-spacing` property controls the space between individual characters.

```html
<p class="letter-spacing-demo">LETTER SPACING</p>
```

```css
.letter-spacing-demo {
  letter-spacing: 5px;
}
```

---

## 11. Word Spacing

**Definition:** The `word-spacing` property controls the space between words.

```html
<p class="word-spacing-demo">Word Spacing Example</p>
```

```css
.word-spacing-demo {
  word-spacing: 15px;
}
```

---

## 12. Line Height

**Definition:** The `line-height` property sets the height of a line of text, affecting spacing between lines.

```html
<p class="line-height-demo">
  Line 1<br>
  Line 2<br>
  Line 3
</p>
```

```css
.line-height-demo {
  line-height: 3;
}
```

---

## 13. Border Property

**Definition:** The `border` property sets the width, style, and color of an element's border. Styles include solid, dotted, dashed, and double.

```html
<div class="border-demo">Solid Border</div>
<div class="dotted">Dotted Border</div>
<div class="dashed">Dashed Border</div>
<div class="double">Double Border</div>
```

```css
.border-demo {
  border: 3px solid red;
}
.dotted {
  border: 3px dotted blue;
}
.dashed {
  border: 3px dashed green;
}
.double {
  border: 5px double black;
}
```

---

## 14. Border Radius

**Definition:** The `border-radius` property rounds the corners of an element's border. A value of `50%` on an equal width/height element creates a circle.

```html
<div class="radius-demo">Rounded Corners</div>
<div class="circle">Circle</div>
```

```css
.radius-demo {
  border: 2px solid black;
  border-radius: 20px;
  padding: 20px;
}
.circle {
  width: 150px;
  height: 150px;
  border-radius: 50%;
  background-color: lightblue;
  text-align: center;
  line-height: 150px;
}
```

---

## 15. Width and Height

**Definition:** The `width` and `height` properties set the dimensions of an element's content box.

```html
<div class="size-demo">300 x 100</div>
```

```css
.size-demo {
  width: 300px;
  height: 100px;
  background-color: lightgreen;
}
```

---

## 16. Padding

**Definition:** The `padding` property creates space *inside* an element, between its content and its border.

```html
<div class="padding-demo">Padding Creates Space Inside Border</div>
```

```css
.padding-demo {
  border: 2px solid black;
  padding: 30px;
}
```

---

## 17. Margin

**Definition:** The `margin` property creates space *outside* an element, between its border and neighboring elements.

```html
<div class="margin-demo">Margin Creates Space Outside Border</div>
```

```css
.margin-demo {
  border: 2px solid red;
  margin: 40px;
}
```

---

## 18. Box Shadow

**Definition:** The `box-shadow` property adds a shadow effect around an element's frame.

```html
<div class="shadow-demo">Shadow Effect</div>
```

```css
.shadow-demo {
  padding: 20px;
  box-shadow: 0px 0px 15px gray;
}
```

---

## 19. Cursor Property

**Definition:** The `cursor` property sets the type of mouse cursor shown when hovering over an element.

```html
<button class="cursor-demo-1">Hover Mouse Here</button>
```

```css
.cursor-demo-1 {
  cursor: pointer;
}
```

---

## 20. Opacity

**Definition:** The `opacity` property sets the transparency level of an element (0 = fully transparent, 1 = fully opaque).

```html
<div class="opacity-demo">Opacity 0.5 Example</div>
```

```css
.opacity-demo {
  opacity: 0.5;
}
```

---

## 21. Display Property

**Definition:** The `display` property defines how an element is rendered in the document flow — `inline` (no line break, only content width), `block` (full width, line break before/after), or `inline-block` (sits inline but can have width/height).

```html
<span class="inline">Inline</span>
<span class="inline">Inline</span>

<div class="block">Block Element</div>

<div class="inline-block">Inline Block</div>
```

```css
.inline {
  display: inline;
  background: yellow;
}
.block {
  display: block;
  background: lightblue;
}
.inline-block {
  display: inline-block;
  background: lightgreen;
  width: 150px;
}
```

---

## 22. Hover Effect

**Definition:** The `:hover` pseudo-class applies styles when the user places the mouse pointer over an element.

```html
<button class="hover-btn">Hover Me</button>
```

```css
.hover-btn {
  padding: 10px 20px;
  border: none;
  background-color: blue;
  color: white;
}
.hover-btn:hover {
  background-color: red;
}
```

---

## 23. CSS Box Model

**Definition:** The Box Model describes how every HTML element is structured: **Content** (actual content) → **Padding** (space inside border) → **Border** (the border line) → **Margin** (space outside border).

```html
<div class="box-model">Content Area</div>
<p>
  Margin → Outside Space<br>
  Border → Border Area<br>
  Padding → Inside Space<br>
  Content → Actual Content
</p>
```

```css
.box-model {
  margin: 20px;
  border: 5px solid red;
  padding: 30px;
  background-color: lightyellow;
}
```

---

## 24. Inline CSS

**Definition:** Inline CSS is written directly inside an HTML tag using the `style` attribute. It applies only to that single element and has the highest priority among the three CSS types.

```html
<p style="color:purple; font-weight:bold;">
  This text is styled using Inline CSS.
</p>
```

```css
/* No separate CSS file/block needed —
   styles are written directly in the style="" attribute */
```

---

## 25. Internal CSS

**Definition:** Internal CSS is written inside a `<style>` tag in the `<head>` section of an HTML document. It applies to all matching elements within that single page only.

```html
<head>
  <style>
    .font-weight-demo {
      font-weight: bold;
    }
  </style>
</head>
<body>
  <p class="font-weight-demo">Styled using Internal CSS</p>
</body>
```

```css
/* This entire block, placed inside <head><style>...</style></head>,
   is an example of Internal CSS */
.font-weight-demo {
  font-weight: bold;
}
```

---


#   Full code 

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Complete Notes </title>

    <style>
        body {
            font-family:'Times New Roman', Times, sans-serif;
            margin:20px;
            line-height:1.8;

        }
        section{
            margin-bottom:40px;
        }
        hr {
            margin:40px 0;
        }
        .targent-notes
        {
            font-size: 13px;
            color:#555;
            background: #f2f3f2;
            padding:6px 10px;
            margin-top:8px;
            font-family: monospace;
            border-left: 4px solid #2196F3;


        }
        
        .color-demo{ 
            color:red;
        } 
        .demo-box, .bg-demo
        {
            padding : 15px;
            border: 2px solid #000;
            margin-top:10px;

        }
        .bg-demo{
            background-color: yellow;
        }
        .font-family-demo{
            font-family: Arial;
        }
        .font-size-demo {
            font-size:25px;
        }
        .font-weight-demo {
            font-weight:bold;
        } 
         .font-style-demo {
            font-style:italic;
        } 
        .text-align-c-demo {
            text-align:center;
        }
        .text-align-l-demo {
            text-align:left;
        }
        .text-align-r-demo {
            text-align:right;
        }
        .underline{
            text-decoration: underline;
        }
        .overline{
            text-decoration: overline;
        }
        .line-through{
            text-decoration: line-through;
        }
        .none{
            text-decoration: none;
        }
        .uppercase{
            text-transform: uppercase;
        }
        .lowercase{
            text-transform: lowercase;
        }
        .capitlize{
            text-transform: capitalize;
        }
        .letter-spacing-demo {
            letter-spacing:10px;
        } 
        .word-spacing-demo {
            word-spacing:10px;
        } 
        .line-height-demo {
            line-height:4;
        } 
        .border-solid{
            border: 3px solid;
            margin:5px;
            padding:5px;

        }
        .border-dotted{
            border: 3px dotted maroon;
            margin:5px;
            padding:5px;
            
        }
        .border-dashed{
            border: 3px dashed green;
            margin:5px;
            padding:5px;
        }
        .border-double{
            border: 5px double black;
            margin:5px;
            padding:5px;
        }
        .radius-demo {
            border:2px solid black;
            border-radius:20px;
            padding :20px;
        } 
        .circle{
            width:150px;
            height:150px;
            border-radius: 50%;
            background-color: lightblue;
            text-align: center;
            line-height: 150px;
        }
        .size-demo{
            height:100px;
             width:300px;
        }
        .padding-demo {
            border:2px solid black;
            padding:30px;
        }
        .margin-demo {
            border:2px solid black;
            margin:40px;
        } 
        .shadow-demo {
            padding :20px ;
            box-shadow:0px 0px 15px gray;
        }
        .cursor-demo {
            cursor:pointer;
        } 
        .inline{
            display: inline;
            background-color: yellow;
        }
        .block{
            display:block;
            background-color: lightblue;
        }
        .lnline-block {
            display:inline-block;
            background-color: limegreen;
            width:150px;
        }
        .hover-btn{
            padding:10px 20px;
            border:none;
            background-color: blue;
            color:white;
        }
        .hover-btn:hover {
            background-color: red;
        }
        .box-model{
            margin :20px;
            border:5px solid red;
            padding:30px;
            background-color: lightyellow;
        }
         

        

    </style>
</head>
<body>
    <h1> CSS Complete Notes</h1>
    <hr>
    <section>
        <h2>1. Color Proporty</h2>
        <p>Used to change the color of the text.</p>
        <p class="color-demo">This text is red.</p>
        <div class="targent-notes"> CSS Target: &lt; class="color-demo" &gt; -> .color-demo{ color:red;}  </div>
    </section>
    <hr>
    <section>
        <h2>2. Background Color</h2>
        <div class="demo-box bg-demo"> Bacakground Color Example.</div>
        <div class="targent-notes"> CSS Target: &lt; class="demo-box bg-demo" &gt; -> .bg-demo {background-color: yellow;}  </div>
    </section>
    <hr>
    <section>
        <h2>3. Font Family</h2>
        <div class="font-family-demo"> This text Arial Font Family </div>
        <div class="targent-notes"> CSS Target: &lt; class="font-family-demo" &gt; -> .font-family-demo {font-family:Arial;}  </div>
    </section>
    <hr>
    <section>
        <h2>4. Font Size</h2>
        <div class="font-size-demo"> Font size is 25px </div>
        <div class="targent-notes"> CSS Target: &lt; class="font-size-demo" &gt; -> .font-size-demo {font-size:25px}  </div>
    </section>
    <hr>
    <section>
        <h2>5. Font weight</h2>
        <div class="font-weight-demo"> Bold text Example </div>
        <div class="targent-notes"> CSS Target: &lt; class="font-weight-demo" &gt; -> .font-weight-demo {font-weight:Bold}  </div>
    </section>
    <hr>
    <section>
        <h2>6. Font style</h2>
        <div class="font-style-demo"> Italic text Example </div>
        <div class="targent-notes"> CSS Target: &lt; class="font-style-demo" &gt; -> .font-style-demo {font-style:italic}  </div>
    </section>
    <hr>
    <section>
        <h2>7. Text Align</h2>
        <div class="text-align-c-demo demo-box"> centered Text  </div>
        <div class="text-align-l-demo demo-box"> left Text  </div>
        <div class="text-align-r-demo demo-box"> Right Text  </div>
        <div class="targent-notes"> CSS Target: &lt; class="text-align-c-demo" &gt; -> .text-align-c-demo {text-align:center}  </div>
    </section>
    <hr>
    <section>
        <h2>8. Text Decoration</h2>
        <p class="underline">underline text </p>
        <p class="overline">overline text </p>
        <p class="line-through"> line Through 72000</p>
        <a class="none" href="#"> </a>
        <div class="targent-notes"> CSS Target: &lt; class="underline/overline/line-through" &gt; -> Css {text-decoration:value;}  </div>
    </section>
    <hr>
    <section>
        <h2>9. Text Transformation</h2>
        <p class="uppercase"> hello world </p>
        <p class="lowercase"> HELLO WORLD </p>
        <p class="capitlize">hello world </p>
        <div class="targent-notes"> CSS Target: &lt; class="uppercase/lowercase/capitlize" &gt; -> css {text-transform:value}  </div>
    </section>
    
    <hr>
    <section>
        <h2>10. letter Spacing</h2>
        <p class="letter-spacing-demo"> LETTER SPACING </p>
        
        <div class="targent-notes"> CSS Target: &lt; class="letter-spacing-demo" &gt; -> .letter-spacing-demo {letter-spacing:10px;}  </div>
    </section>
    <hr>
    <section>
        <h2>11. Word Spacing</h2>
        <p class="word-spacing-demo"> Word  Spacing Example </p>
        
        <div class="targent-notes"> CSS Target: &lt; class="word-spacing-demo" &gt; -> .word-spacing-demo {word-spacing:10px;}  </div>
    </section>
    <hr>
    <section>
        <h2>12. line height</h2>
        <p class="line-height-demo">Line 1 <br> Line 2 <br> Line 3</p>
        
        <div class="targent-notes"> CSS Target: &lt; class="line-height-demo" &gt; -> .line-height-demo {line-height:4;}  </div>
    </section>
    <hr>
    <section>
        <h2>13. Border proporty</h2>
        <div class="border-solid"> Solid Border  </div>
        <div class="border-dotted"> Dotted Border  </div>
        <div class="border-dashed"> Dashed Border  </div>
        <div class="border-double"> Double Border  </div>

        <div class="targent-notes"> CSS Target: &lt; class="border-solid/dotted/dashed/double" &gt; -> css {border:value}  </div>
    </section>
    <hr>
    <section>
        <h2>14. border radius</h2>
        <div class="radius-demo"> rounded cornors </div>
        <br>
        <div class="circle"> circle </div>

        <div class="targent-notes"> CSS Target: &lt; class="radius-demo" &gt; -> .radius-demo {border-radius:vlaue;}  </div>
    </section>
    <hr>
    <section>
        <h2>15. height & width</h2>
        <div class="size-demo"> 100 X 300  </div>
        <div class="targent-notes"> CSS Target: &lt; class="size-demo" &gt; -> .size-demo {height:100px; width:300px;}  </div>
    </section>
    <hr>
    <section>
        <h2>16. Padding</h2>
        <div class="padding-demo"> Padding creates the sapce inside the border.   </div>
        <div class="targent-notes"> CSS Target: &lt; class="padding-demo"" &gt; -> .padding-demo {padding:value;}  </div>
    </section>
    <hr>
    <section>
        <h2>17. Margin</h2>
        <div class="margin-demo"> Margin creates space outside the border.  </div>
        <div class="targent-notes"> CSS Target: &lt; class="margin-demo" &gt; -> .margin-demo {margin:value;}  </div>
    </section>
    <hr>
    <section>
        <h2>18. Box Shadow </h2>
        <div class="shadow-demo"> Box Shadow </div>
        <div class="targent-notes"> CSS Target: &lt; class="shadow-demo" &gt; -> .shadow-demo {box-shadow:0px 0px 15px ;}  </div>
    </section>
    <hr>
    <section>
        <h2>19. Cursor proporty </h2>
        <div class="cursor-demo">Hover Mouse Here </div>
        <div class="targent-notes"> CSS Target: &lt; class="cursor-demo" &gt; -> .cursor-demo {cursor:pointer;}  </div>
    </section>
    <hr>
    <section>
        <h2>20. Display proporty </h2>
        <span class="inline">Inline</span> 
        <span class="inline">Inline</span>
        <br> <br>
        <div class="block"> block element </div>
        <br>
        <div class="lnline-block"> block element </div>

        <div class="targent-notes"> CSS Target: &lt; class="inline/block/Lnline-block" &gt; -> css {proporty : value;}  </div>
    </section>
    <hr>
    <section>
        <h2>21. Hover Effect </h2>
        <button class="hover-btn">Hover me </button>
        <div class="targent-notes"> CSS Target: &lt; class="hover-btn" &gt; -> .hover-btn {proporty:value;}  </div>
    </section>
    <hr>
    <section>
        <h2>22. Css Box Model </h2>
        <div class="box-model"> Conet Area </div>
        <p> 
            Margin  -> Ouside Space <br>
            Border  -> Border Area <br>
            Padding -> Inside Space <br>
            content -> Actual contnet 


        </p>
        <div class="targent-notes"> CSS Target: &lt; class="box-model" &gt; -> .box-model {proporty:value;}  </div>
    </section>
    <hr>
    <section>
        <h2>24. Inline CSS </h2>
        <p> inline css is written dirctly inside the HTML tag using style attribute. but it applys to that single emelent only we canot add it multiple blocks.</p>
        <p style="color:purple; font-size: 20px; font-weight: 900; ">This is Inline CSS</p>
        <div class="targent-notes"> CSS Target: &lt; style="color:purple; font-size: 20px; font-weight: 900;" &gt;  </div>
    </section>
     <hr>
    <section>
        <h2>25. Internal CSS </h2>
        <p> Internal CSS is writtten in the &lt; Head tag &gt; using &lt; style tag &gt; section of the html document. it applies to all matcing elemnts on that page </p>
        <button class="hover-btn">Hover me </button>
        <div class="targent-notes"> CSS Target: &lt; class="hover-btn" &gt; -> .hover-btn {proporty:value;}  </div>  
    </section>

    



    
</body>
</html>
```
---

# Assignment 1: Digital Business Card

## Objective

Create a personal digital business card for yourself.

## Requirements

### HTML Content

* Your Name
* Role (Frontend Developer / Student)
* Short Introduction (3–4 lines)
* Skills List
* Contact Information
* Portfolio Link

### CSS Requirements

Use the following:

Background Color
Text Color
Font Family
Font Size
Font Weight
Text Align
Border
Border Radius
Width & Height
Padding
Margin
Box Shadow
Hover Effect on Portfolio Link
Cursor Property

### Expected Output

```
-------------------------------------
|                                   |
|      JOHN DOE                    |
|      Frontend Developer          |
|                                   |
|  Passionate about Web Design     |
|  HTML | CSS | JavaScript         |
|                                   |
|  Email: abc@gmail.com            |
|  Phone: 9999999999               |
|                                   |
|   [ View Portfolio ]             |
|                                   |
-------------------------------------
```

### Challenge

When user hovers on the portfolio button:

* Background color should change.
* Cursor should become pointer.

---

# Assignment 2: Movie Poster Design

## Objective

Create a movie poster using only HTML and CSS.

## Requirements

### HTML Content

* Movie Name
* Tagline
* Release Date
* Main Actor Names
* Watch Now Button

### CSS Requirements

Large Font Sizes
Text Transform (UPPERCASE)
Letter Spacing
Word Spacing
Background Color
Text Color
Border
Border Radius
Text Align
Box Shadow
Hover Effect

### Expected Output

```
****************************************
*                                      *
*          THE LAST WARRIOR            *
*                                      *
*     "A Battle Beyond Imagination"    *
*                                      *
*       RELEASES JULY 2026             *
*                                      *
*     Starring: Actor A, Actor B       *
*                                      *
*          [ WATCH NOW ]               *
*                                      *
****************************************
```

### Challenge

Make the movie title look dramatic using:

* Letter Spacing
* Font Weight
* Text Transform

---

# Assignment 3: Product Advertisement Card

## Objective

Design an advertisement card for any product.

Examples:

* Mobile Phone
* Laptop
* Headphones
* Smart Watch
* Gaming Mouse

## Requirements

### HTML Content

* Product Name
* Product Image
* Price
* Features (unordered list)
* Buy Now Button

### CSS Requirements

Image Width & Height
Background Color
Font Styling
Border
Border Radius
Padding
Margin
Box Shadow
Hover Effect
Text Decoration
Display Property (inline-block)

### Expected Output

```
----------------------------------
|                                |
|       PRODUCT IMAGE            |
|                                |
|      Gaming Headset            |
|                                |
|      ₹2,999                    |
|                                |
|  ✓ Noise Cancellation          |
|  ✓ RGB Lights                  |
|  ✓ Wireless                    |
|                                |
|      [ BUY NOW ]               |
|                                |
----------------------------------
```

### Challenge

* Strike the old price using `text-decoration: line-through`.
* Change button color on hover.
* Use `display: inline-block` for feature badges.

---
#  


## 26. Text Shadow

**Definition:** The `text-shadow` property adds a shadow effect to text. Syntax: `horizontal-offset vertical-offset blur-radius color`.

```html
<h3 class="text-shadow-demo">Shadow Text Example</h3>
```

```css
.text-shadow-demo {
  text-shadow: 2px 2px 5px gray;
}
```

---

## 27. Background Image

**Definition:** The `background-image` property sets an image (or gradient) as the background of an element.

```html
<div class="bg-image-demo">Background Image Area</div>
```

```css
.bg-image-demo {
  height: 150px;
  background-image: linear-gradient(to right, lightblue, lightgreen);
}
```

---

## 28. List Style

**Definition:** The `list-style-type` property defines the marker style (bullet shape) for list items.

```html
<ul class="list-demo">
  <li>HTML</li>
  <li>CSS</li>
</ul>
```

```css
.list-demo {
  list-style-type: square;
}
```

---

## 29. Overflow

**Definition:** The `overflow` property controls what happens when content is too big to fit inside its box. Values: `visible`, `hidden`, `scroll`, `auto`.

```html
<div class="overflow-demo">
  Overflow example Overflow example Overflow example Overflow example
</div>
```

```css
.overflow-demo {
  width: 250px;
  height: 80px;
  overflow: scroll;
  border: 1px solid black;
}
```

---

## 30. Max Width

**Definition:** The `max-width` property sets the maximum width an element can grow to, even if its container is larger.

```html
<div class="max-width-demo">Max Width Example</div>
```

```css
.max-width-demo {
  max-width: 400px;
  background: lightyellow;
  padding: 10px;
}
```

---

## 31. Min Width

**Definition:** The `min-width` property sets the minimum width an element must maintain, even if its content is smaller.

```html
<div class="min-width-demo">Min Width Example</div>
```

```css
.min-width-demo {
  min-width: 300px;
  background: lightblue;
  padding: 10px;
}
```

---

## 32. Max Height

**Definition:** The `max-height` property sets the maximum height an element can grow to. If content exceeds it, `overflow` controls how it's handled.

```html
<div class="max-height-demo">
  Line1<br>Line2<br>Line3<br>Line4<br>Line5
</div>
```

```css
.max-height-demo {
  max-height: 60px;
  overflow: auto;
  border: 1px solid black;
}
```

---

## 33. Min Height

**Definition:** The `min-height` property sets the minimum height an element must maintain.

```html
<div class="min-height-demo">Min Height Example</div>
```

```css
.min-height-demo {
  min-height: 100px;
  background: #eee;
}
```

---

## 34. Visibility

**Definition:** The `visibility` property hides an element, but unlike `display: none`, the element still takes up space in the layout.

```html
<p class="visibility-demo">Hidden Text</p>
<p>Space remains.</p>
```

```css
.visibility-demo {
  visibility: hidden;
}
```

---

## 35. Outline

**Definition:** The `outline` property draws a line around an element, outside the border. It does not affect layout/spacing like border does.

```html
<div class="outline-demo">Outline Example</div>
```

```css
.outline-demo {
  outline: 3px solid red;
  padding: 10px;
}
```

---

## 36. CSS Units

**Definition:** CSS units define measurement values. `rem` is relative to the root element's font size, making it useful for scalable/responsive design.

```html
<p class="units-demo">2rem Example</p>
```

```css
.units-demo {
  font-size: 2rem;
}
```

---

## 37. Cursor Types

**Definition:** The `cursor` property can take many values to change the mouse pointer shape — e.g. `crosshair`, `pointer`, `move`, `not-allowed`.

```html
<div class="cursor-demo">Move mouse here</div>
```

```css
.cursor-demo {
  cursor: crosshair;
}
```

---

## 38. Multiple Classes

**Definition:** An HTML element can have more than one class. CSS rules for all listed classes are applied together (combined).

```html
<p class="red bold">Red and Bold</p>
```

```css
.red {
  color: red;
}
.bold {
  font-weight: bold;
}
```

---

## 39. CSS Comments

**Definition:** Comments in CSS are written between `/* */`. They are ignored by the browser and used to explain code.

```html
<p>Use /* comment */ in CSS</p>
```

```css
/* This is a CSS comment.
   It does not affect the styling. */
p {
  color: black; /* sets text color */
}
```

---

## 40. Universal Selector

**Definition:** The `*` (universal selector) targets **all** elements on the page. Commonly used for resets (e.g. removing default margin/padding).

```html
<p>* selector targets all elements.</p>
```

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```

---

## 41. Group Selector

**Definition:** A group selector applies the same CSS rule to multiple selectors at once, separated by commas.

```html
<h1>Heading 1</h1>
<h2>Heading 2</h2>
<h3>Heading 3</h3>
```

```css
h1, h2, h3 {
  color: blue;
}
```

---

## 42. Attribute Selector

**Definition:** An attribute selector targets elements based on the presence or value of an HTML attribute. Syntax: `element[attribute=value]`.

```html
<input type="text" placeholder="Text Input">
```

```css
input[type="text"] {
  background: #ffffcc;
}
```

---

## 43. Child Selector

**Definition:** The child selector (`>`) targets only the **direct children** of an element, not deeper descendants.

```html
<div class="child-demo">
  <p>Direct Child</p>
</div>
```

```css
.child-demo > p {
  color: red;
}
```

---

## 44. Descendant Selector

**Definition:** The descendant selector (space between selectors) targets **all** elements nested inside another element, at any depth.

```html
<div class="desc-demo">
  <div>
    <p>Descendant Paragraph</p>
  </div>
</div>
```

```css
.desc-demo p {
  font-style: italic;
}
```

---

## 45. Link States

**Definition:** Pseudo-classes like `:hover`, `:visited`, `:active`, `:link` style hyperlinks based on their state.

```html
<a href="#" class="link-demo">Hover Link</a>
```

```css
.link-demo:hover {
  color: red;
}
```

---

## 46. Table Styling

**Definition:** `border-collapse` merges table cell borders into a single border. `th` and `td` can be styled individually for headers and data cells.

```html
<table>
  <tr>
    <th>Name</th>
    <th>Skill</th>
  </tr>
  <tr>
    <td>Mahesh</td>
    <td>CSS</td>
  </tr>
</table>
```

```css
table {
  border-collapse: collapse;
}
th, td {
  border: 1px solid black;
  padding: 8px;
}
th {
  background: lightblue;
}
```

---

## 47. Form Styling

**Definition:** Form elements like `<input>` can be styled using descendant selectors to add padding, margin, borders, etc.

```html
<form class="form-demo">
  <input placeholder="Name">
</form>
```

```css
.form-demo input {
  padding: 8px;
  margin: 5px;
}
```

---

## 48. Image Styling

**Definition:** Images can be styled like any other element — setting `width`, and using `border-radius: 50%` to create a circular image.

```html
<img class="img-demo" src="https://via.placeholder.com/120">
```

```css
.img-demo {
  width: 120px;
  border-radius: 50%;
}
```

---

## 49. Transition

**Definition:** The `transition` property animates changes to CSS property values smoothly over a specified duration, instead of changing instantly.

```html
<button class="transition-btn">Hover Me</button>
```

```css
.transition-btn {
  padding: 10px;
  transition: 0.4s;
}
.transition-btn:hover {
  background: red;
  color: white;
}
```

---

## 50. Transform

**Definition:** The `transform` property applies 2D/3D transformations like `scale()`, `rotate()`, `translate()` to an element.

```html
<div class="transform-box">Hover Scale</div>
```

```css
.transform-box {
  display: inline-block;
  padding: 15px;
  background: lightgreen;
}
.transform-box:hover {
  transform: scale(1.2);
}
```

---

# Full Code 

```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="UTF-8">
    <title>CSS Complete Notes - Topics 1 to 50</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            line-height: 1.8
        }

        section {
            margin-bottom: 40px
        }

        .demo,
        .demo-box {
            padding: 15px;
            border: 1px solid #000;
            margin-top: 10px
        }

        hr {
            margin: 40px 0
        }

        .target-note {
            font-size: 13px;
            color: #555;
            background: #f2f2f2;
            border-left: 4px solid #2196F3;
            padding: 6px 10px;
            margin-top: 8px;
            font-family: monospace
        }

        /* =========================
   1-25: GENERAL STYLING
========================= */

        /* 1. Color Property -> applies to <p class="color-demo"> */
        .color-demo {
            color: red;
        }

        /* 2. Background Color -> applies to <div class="demo-box bg-demo"> */
        .bg-demo {
            background-color: yellow;
        }

        /* 3. Font Family -> applies to <p class="font-family-demo"> */
        .font-family-demo {
            font-family: 'Times New Roman';
        }

        /* 4. Font Size -> applies to <p class="font-size-demo"> */
        .font-size-demo {
            font-size: 30px;
        }

        /* 5. Font Weight -> applies to <p class="font-weight-demo"> */
        .font-weight-demo {
            font-weight: bold;
        }

        /* 6. Font Style -> applies to <p class="font-style-demo"> */
        .font-style-demo {
            font-style: italic;
        }

        /* 7. Text Align -> applies to <div class="text-align-demo"> */
        .text-align-demo {
            text-align: center;
        }

        /* 8. Text Decoration -> applies to <p>/<a> with .none / .underline / .overline / .line-through */
        .none {
            text-decoration: none;
        }

        .underline {
            text-decoration: underline;
        }

        .overline {
            text-decoration: overline;
        }

        .line-through {
            text-decoration: line-through;
        }

        /* 9. Text Transform -> applies to <p> with .uppercase / .lowercase / .capitalize */
        .uppercase {
            text-transform: uppercase;
        }

        .lowercase {
            text-transform: lowercase;
        }

        .capitalize {
            text-transform: capitalize;
        }

        /* 10. Letter Spacing -> applies to <p class="letter-spacing-demo"> */
        .letter-spacing-demo {
            letter-spacing: 5px;
        }

        /* 11. Word Spacing -> applies to <p class="word-spacing-demo"> */
        .word-spacing-demo {
            word-spacing: 15px;
        }

        /* 12. Line Height -> applies to <p class="line-height-demo"> */
        .line-height-demo {
            line-height: 3;
        }

        /* 13. Border Property -> applies to <div> with .border-demo / .dotted / .dashed / .double */
        .border-demo {
            border: 3px solid red;
        }

        .dotted {
            border: 3px dotted blue;
        }

        .dashed {
            border: 3px dashed green;
        }

        .double {
            border: 5px double black;
        }

        /* 14. Border Radius -> applies to <div class="radius-demo"> and <div class="circle"> */
        .radius-demo {
            border: 2px solid black;
            border-radius: 20px;
            padding: 20px;
        }

        .circle {
            width: 150px;
            height: 150px;
            border-radius: 50%;
            background-color: lightblue;
            text-align: center;
            line-height: 150px;
        }

        /* 15. Width and Height -> applies to <div class="size-demo"> */
        .size-demo {
            width: 300px;
            height: 100px;
            background-color: lightgreen;
        }

        /* 16. Padding -> applies to <div class="padding-demo"> */
        .padding-demo {
            border: 2px solid black;
            padding: 30px;
        }

        /* 17. Margin -> applies to <div class="margin-demo"> */
        .margin-demo {
            border: 2px solid red;
            margin: 40px;
        }

        /* 18. Box Shadow -> applies to <div class="shadow-demo"> */
        .shadow-demo {
            padding: 20px;
            box-shadow: 0px 0px 15px gray;
        }

        /* 19. Cursor Property -> applies to <button class="cursor-demo"> */
        .cursor-demo-1 {
            cursor: pointer;
        }

        /* 20. Opacity -> applies to <div class="opacity-demo"> */
        .opacity-demo {
            opacity: 0.5;
        }

        /* 21. Display Property -> applies to <span class="inline">, <div class="block">, <div class="inline-block"> */
        .inline {
            display: inline;
            background: yellow;
        }

        .block {
            display: block;
            background: lightblue;
        }

        .inline-block {
            display: inline-block;
            background: lightgreen;
            width: 150px;
        }

        /* 22. Hover Effect -> applies to <button class="hover-btn"> */
        .hover-btn {
            padding: 10px 20px;
            border: none;
            background-color: blue;
            color: white;
        }

        .hover-btn:hover {
            background-color: red;
        }

        /* 23. CSS Box Model -> applies to <div class="box-model"> */
        .box-model {
            margin: 20px;
            border: 5px solid red;
            padding: 30px;
            background-color: lightyellow;
        }

        /* 24. Inline CSS -> applied directly via style="" attribute on the element (no class needed) */

        /* 25. Internal CSS -> this whole <style> block in <head> is an example of Internal CSS, applies to ALL matching elements in this page */


        /* =========================
   26-50: AS PROVIDED
========================= */

        /* 26. Text Shadow */
        .text-shadow-demo {
            text-shadow: 2px 2px 5px gray;
        }

        /* 27. Background Image */
        .bg-image-demo {
            height: 150px;
            background-image: linear-gradient(to right, lightblue, lightgreen);
        }

        /* 28. List Style */
        .list-demo {
            list-style-type: square;
        }

        /* 29. Overflow */
        .overflow-demo {
            width: 250px;
            height: 80px;
            overflow: scroll;
            border: 1px solid black;
        }

        /* 30. Max Width */
        .max-width-demo {
            max-width: 400px;
            background: lightyellow;
            padding: 10px;
        }

        /* 31. Min Width */
        .min-width-demo {
            min-width: 300px;
            background: lightblue;
            padding: 10px;
        }

        /* 32. Max Height */
        .max-height-demo {
            max-height: 60px;
            overflow: auto;
            border: 1px solid black;
        }

        /* 33. Min Height */
        .min-height-demo {
            min-height: 100px;
            background: #eee;
        }

        /* 34. Visibility */
        .visibility-demo {
            visibility: hidden;
        }

        /* 35. Outline */
        .outline-demo {
            outline: 3px solid red;
            padding: 10px;
        }

        /* 36. CSS Units */
        .units-demo {
            font-size: 2rem;
        }

        /* 37. Cursor Types */
        .cursor-demo {
            cursor: crosshair;
        }

        /* 38. Multiple Classes */
        .red {
            color: red;
        }

        .bold {
            font-weight: bold;
        }

        /* 39. CSS Comments */

        /* 40. Universal Selector example */

        /* 41. Group Selector */

        /* 42. Attribute Selector */
        input[type=text] {
            background: #ffffcc;
        }

        /* 43. Child Selector */
        .child-demo>p {
            color: red;
        }

        /* 44. Descendant Selector */
        .desc-demo p {
            font-style: italic;
        }

        /* 45. Link States */
        .link-demo:hover {
            color: red;
        }

        /* 46. Table Styling */
        table {
            border-collapse: collapse;
        }

        th,
        td {
            border: 1px solid black;
            padding: 8px;
        }

        th {
            background: lightblue;
        }

        /* 47. Form Styling */
        .form-demo input {
            padding: 8px;
            margin: 5px;
        }

        /* 48. Image Styling */
        .img-demo {
            width: 120px;
            border-radius: 50%;
        }

        /* 49. Transition */
        .transition-btn {
            padding: 10px;
        }

        .transition-btn {
            transition: 0.4s;
        }

        .transition-btn:hover {
            background: red;
            color: white;
        }

        /* 50. Transform */
        .transform-box {
            display: inline-block;
            padding: 15px;
            background: lightgreen;
        }

        .transform-box:hover {
            transform: scale(1.2);
        }
    </style>
</head>

<body>

    <h1>CSS Complete Notes - Topics 1 to 50</h1>

    <hr>

    <section>
        <h2>1. Color Property</h2>
        <p>Used to change text color.</p>
        <p class="color-demo">This text is red.</p>
        <div class="target-note">CSS Target: &lt;p class="color-demo"&gt; → .color-demo { color: red; }</div>
    </section>

    <hr>

    <section>
        <h2>2. Background Color</h2>
        <div class="demo-box bg-demo">Background Color Example</div>
        <div class="target-note">CSS Target: &lt;div class="demo-box bg-demo"&gt; → .bg-demo { background-color: yellow;
            }</div>
    </section>

    <hr>

    <section>
        <h2>3. Font Family</h2>
        <p class="font-family-demo">Times New Roman Font</p>
        <div class="target-note">CSS Target: &lt;p class="font-family-demo"&gt; → .font-family-demo { font-family:
            'Times New Roman'; }</div>
    </section>

    <hr>

    <section>
        <h2>4. Font Size</h2>
        <p class="font-size-demo">Font Size 30px</p>
        <div class="target-note">CSS Target: &lt;p class="font-size-demo"&gt; → .font-size-demo { font-size: 30px; }
        </div>
    </section>

    <hr>

    <section>
        <h2>5. Font Weight</h2>
        <p class="font-weight-demo">Bold Text Example</p>
        <div class="target-note">CSS Target: &lt;p class="font-weight-demo"&gt; → .font-weight-demo { font-weight: bold;
            }</div>
    </section>

    <hr>

    <section>
        <h2>6. Font Style</h2>
        <p class="font-style-demo">Italic Text Example</p>
        <div class="target-note">CSS Target: &lt;p class="font-style-demo"&gt; → .font-style-demo { font-style: italic;
            }</div>
    </section>

    <hr>

    <section>
        <h2>7. Text Align</h2>
        <div class="text-align-demo">Centered Text</div>
        <div class="target-note">CSS Target: &lt;div class="text-align-demo"&gt; → .text-align-demo { text-align:
            center; }</div>
    </section>

    <hr>

    <section>
        <h2>8. Text Decoration</h2>
        <p class="underline">Underline</p>
        <p class="overline">Overline</p>
        <p class="line-through">Line Through</p>
        <a href="#" class="none">Link Without Underline</a>
        <div class="target-note">CSS Target: &lt;p class="underline/overline/line-through"&gt; and &lt;a
            class="none"&gt; → text-decoration property</div>
    </section>

    <hr>

    <section>
        <h2>9. Text Transform</h2>
        <p class="uppercase">hello world</p>
        <p class="lowercase">HELLO WORLD</p>
        <p class="capitalize">hello world css</p>
        <div class="target-note">CSS Target: &lt;p class="uppercase/lowercase/capitalize"&gt; → text-transform property
        </div>
    </section>

    <hr>

    <section>
        <h2>10. Letter Spacing</h2>
        <p class="letter-spacing-demo">LETTER SPACING</p>
        <div class="target-note">CSS Target: &lt;p class="letter-spacing-demo"&gt; → .letter-spacing-demo {
            letter-spacing: 5px; }</div>
    </section>

    <hr>

    <section>
        <h2>11. Word Spacing</h2>
        <p class="word-spacing-demo">Word Spacing Example</p>
        <div class="target-note">CSS Target: &lt;p class="word-spacing-demo"&gt; → .word-spacing-demo { word-spacing:
            15px; }</div>
    </section>

    <hr>

    <section>
        <h2>12. Line Height</h2>
        <p class="line-height-demo">Line 1<br>Line 2<br>Line 3</p>
        <div class="target-note">CSS Target: &lt;p class="line-height-demo"&gt; → .line-height-demo { line-height: 3; }
        </div>
    </section>

    <hr>

    <section>
        <h2>13. Border Property</h2>
        <div class="border-demo">Solid Border</div>
        <br>
        <div class="dotted">Dotted Border</div>
        <br>
        <div class="dashed">Dashed Border</div>
        <br>
        <div class="double">Double Border</div>
        <div class="target-note">CSS Target: &lt;div class="border-demo/dotted/dashed/double"&gt; → border property
            variations</div>
    </section>

    <hr>

    <section>
        <h2>14. Border Radius</h2>
        <div class="radius-demo">Rounded Corners</div>
        <br>
        <div class="circle">Circle</div>
        <div class="target-note">CSS Target: &lt;div class="radius-demo"&gt; and &lt;div class="circle"&gt; →
            border-radius property</div>
    </section>

    <hr>

    <section>
        <h2>15. Width and Height</h2>
        <div class="size-demo">300 x 100</div>
        <div class="target-note">CSS Target: &lt;div class="size-demo"&gt; → .size-demo { width: 300px; height: 100px; }
        </div>
    </section>

    <hr>

    <section>
        <h2>16. Padding</h2>
        <div class="padding-demo">Padding Creates Space Inside Border</div>
        <div class="target-note">CSS Target: &lt;div class="padding-demo"&gt; → .padding-demo { padding: 30px; }</div>
    </section>

    <hr>

    <section>
        <h2>17. Margin</h2>
        <div class="margin-demo">Margin Creates Space Outside Border</div>
        <div class="target-note">CSS Target: &lt;div class="margin-demo"&gt; → .margin-demo { margin: 40px; }</div>
    </section>

    <hr>

    <section>
        <h2>18. Box Shadow</h2>
        <div class="shadow-demo">Shadow Effect</div>
        <div class="target-note">CSS Target: &lt;div class="shadow-demo"&gt; → .shadow-demo { box-shadow: 0px 0px 15px
            gray; }</div>
    </section>

    <hr>

    <section>
        <h2>19. Cursor Property</h2>
        <button class="cursor-demo-1">Hover Mouse Here</button>
        <div class="target-note">CSS Target: &lt;button class="cursor-demo-1"&gt; → .cursor-demo-1 { cursor: pointer; }
        </div>
    </section>

    <hr>

    <section>
        <h2>20. Opacity</h2>
        <div class="opacity-demo">Opacity 0.5 Example</div>
        <div class="target-note">CSS Target: &lt;div class="opacity-demo"&gt; → .opacity-demo { opacity: 0.5; }</div>
    </section>

    <hr>

    <section>
        <h2>21. Display Property</h2>
        <span class="inline">Inline</span>
        <span class="inline">Inline</span>
        <br><br>
        <div class="block">Block Element</div>
        <br>
        <div class="inline-block">Inline Block</div>
        <div class="target-note">CSS Target: &lt;span class="inline"&gt;, &lt;div class="block"&gt;, &lt;div
            class="inline-block"&gt; → display property</div>
    </section>

    <hr>

    <section>
        <h2>22. Hover Effect</h2>
        <button class="hover-btn">Hover Me</button>
        <div class="target-note">CSS Target: &lt;button class="hover-btn"&gt; → .hover-btn and .hover-btn:hover</div>
    </section>

    <hr>

    <section>
        <h2>23. CSS Box Model</h2>
        <div class="box-model">Content Area</div>
        <p>
            Margin → Outside Space<br>
            Border → Border Area<br>
            Padding → Inside Space<br>
            Content → Actual Content
        </p>
        <div class="target-note">CSS Target: &lt;div class="box-model"&gt; → .box-model { margin, border, padding,
            background-color }</div>
    </section>

    <hr>

    <section>
        <h2>24. Inline CSS</h2>
        <p>Inline CSS is written directly inside an HTML tag using the style attribute. It applies only to that single
            element.</p>
        <p style="color:purple;font-weight:bold;">This text is styled using Inline CSS.</p>
        <div class="target-note">CSS Target: &lt;p style="color:purple;font-weight:bold;"&gt; → style applied directly
            on the element, no class/selector used</div>
    </section>

    <hr>

    <section>
        <h2>25. Internal CSS</h2>
        <p>Internal CSS is written inside a &lt;style&gt; tag in the &lt;head&gt; section of the HTML document. It
            applies to all matching elements on that page.</p>
        <p class="font-weight-demo">This page itself uses Internal CSS (see the &lt;style&gt; block above).</p>
        <div class="target-note">CSS Target: The &lt;style&gt;...&lt;/style&gt; block inside &lt;head&gt; → applies
            rules to all matching elements across this page</div>
    </section>

    <hr>

    <section>
        <h2>26. Text Shadow</h2>
        <p>Explanation and demo of Text Shadow.</p>
        <h3 class='text-shadow-demo'>Shadow Text Example</h3>
    </section>
    <hr>
    <section>
        <h2>27. Background Image</h2>
        <p>Explanation and demo of Background Image.</p>
        <div class='bg-image-demo demo'>Background Image Area</div>
    </section>
    <hr>
    <section>
        <h2>28. List Style</h2>
        <p>Explanation and demo of List Style.</p>
        <ul class='list-demo'>
            <li>HTML</li>
            <li>CSS</li>
        </ul>
    </section>
    <hr>
    <section>
        <h2>29. Overflow</h2>
        <p>Explanation and demo of Overflow.</p>
        <div class='overflow-demo'>Overflow example Overflow example Overflow example Overflow example Overflow example
            Overflow example</div>
    </section>
    <hr>
    <section>
        <h2>30. Max Width</h2>
        <p>Explanation and demo of Max Width.</p>
        <div class='max-width-demo'>Max Width Example</div>
    </section>
    <hr>
    <section>
        <h2>31. Min Width</h2>
        <p>Explanation and demo of Min Width.</p>
        <div class='min-width-demo'>Min Width Example</div>
    </section>
    <hr>
    <section>
        <h2>32. Max Height</h2>
        <p>Explanation and demo of Max Height.</p>
        <div class='max-height-demo'>Line1<br>Line2<br>Line3<br>Line4<br>Line5</div>
    </section>
    <hr>
    <section>
        <h2>33. Min Height</h2>
        <p>Explanation and demo of Min Height.</p>
        <div class='min-height-demo'>Min Height Example</div>
    </section>
    <hr>
    <section>
        <h2>34. Visibility</h2>
        <p>Explanation and demo of Visibility.</p>
        <p class='visibility-demo'>Hidden Text</p>
        <p>Space remains.</p>
    </section>
    <hr>
    <section>
        <h2>35. Outline</h2>
        <p>Explanation and demo of Outline.</p>
        <div class='outline-demo'>Outline Example</div>
    </section>
    <hr>
    <section>
        <h2>36. CSS Units</h2>
        <p>Explanation and demo of CSS Units.</p>
        <p class='units-demo'>2rem Example</p>
    </section>
    <hr>
    <section>
        <h2>37. Cursor Types</h2>
        <p>Explanation and demo of Cursor Types.</p>
        <div class='cursor-demo'>Move mouse here</div>
    </section>
    <hr>
    <section>
        <h2>38. Multiple Classes</h2>
        <p>Explanation and demo of Multiple Classes.</p>
        <p class='red bold'>Red and Bold</p>
    </section>
    <hr>
    <section>
        <h2>39. CSS Comments</h2>
        <p>Explanation and demo of CSS Comments.</p>
        <p>Use /* comment */ in CSS</p>
    </section>
    <hr>
    <section>
        <h2>40. Universal Selector</h2>
        <p>Explanation and demo of Universal Selector.</p>
        <p>* selector targets all elements.</p>
    </section>
    <hr>
    <section>
        <h2>41. Group Selector</h2>
        <p>Explanation and demo of Group Selector.</p>
        <p>h1,h2,h3{color:blue;}</p>
    </section>
    <hr>
    <section>
        <h2>42. Attribute Selector</h2>
        <p>Explanation and demo of Attribute Selector.</p><input type='text' placeholder='Text Input'>
    </section>
    <hr>
    <section>
        <h2>43. Child Selector</h2>
        <p>Explanation and demo of Child Selector.</p>
        <div class='child-demo'>
            <p>Direct Child</p>
        </div>
    </section>
    <hr>
    <section>
        <h2>44. Descendant Selector</h2>
        <p>Explanation and demo of Descendant Selector.</p>
        <div class='desc-demo'>
            <div>
                <p>Descendant Paragraph</p>
            </div>
        </div>
    </section>
    <hr>
    <section>
        <h2>45. Link States</h2>
        <p>Explanation and demo of Link States.</p><a href='#' class='link-demo'>Hover Link</a>
    </section>
    <hr>
    <section>
        <h2>46. Table Styling</h2>
        <p>Explanation and demo of Table Styling.</p>
        <table>
            <tr>
                <th>Name</th>
                <th>Skill</th>
            </tr>
            <tr>
                <td>Mahesh</td>
                <td>CSS</td>
            </tr>
        </table>
    </section>
    <hr>
    <section>
        <h2>47. Form Styling</h2>
        <p>Explanation and demo of Form Styling.</p>
        <form class='form-demo'><input placeholder='Name'></form>
    </section>
    <hr>
    <section>
        <h2>48. Image Styling</h2>
        <p>Explanation and demo of Image Styling.</p><img class='img-demo' src='https://via.placeholder.com/120'>
    </section>
    <hr>
    <section>
        <h2>49. Transition</h2>
        <p>Explanation and demo of Transition.</p><button class='transition-btn'>Hover Me</button>
    </section>
    <hr>
    <section>
        <h2>50. Transform</h2>
        <p>Explanation and demo of Transform.</p>
        <div class='transform-box'>Hover Scale</div>
    </section>
    <hr>

    <h1>CSS Notes (1 to 50) Completed</h1>

</body>

</html> 

```

---

## Quick Reference Table

| # | Topic | Property/Concept |
|---|-------|-------------------|
| 1 | Color | `color` |
| 2 | Background Color | `background-color` |
| 3 | Font Family | `font-family` |
| 4 | Font Size | `font-size` |
| 5 | Font Weight | `font-weight` |
| 6 | Font Style | `font-style` |
| 7 | Text Align | `text-align` |
| 8 | Text Decoration | `text-decoration` |
| 9 | Text Transform | `text-transform` |
| 10 | Letter Spacing | `letter-spacing` |
| 11 | Word Spacing | `word-spacing` |
| 12 | Line Height | `line-height` |
| 13 | Border | `border` |
| 14 | Border Radius | `border-radius` |
| 15 | Width & Height | `width`, `height` |
| 16 | Padding | `padding` |
| 17 | Margin | `margin` |
| 18 | Box Shadow | `box-shadow` |
| 19 | Cursor | `cursor: pointer` |
| 20 | Opacity | `opacity` |
| 21 | Display | `display: inline/block/inline-block` |
| 22 | Hover Effect | `:hover` |
| 23 | Box Model | margin → border → padding → content |
| 24 | Inline CSS | `style=""` attribute |
| 25 | Internal CSS | `<style>` in `<head>` |
| 26 | Text Shadow | `text-shadow` |
| 27 | Background Image | `background-image` |
| 28 | List Style | `list-style-type` |
| 29 | Overflow | `overflow` |
| 30 | Max Width | `max-width` |
| 31 | Min Width | `min-width` |
| 32 | Max Height | `max-height` |
| 33 | Min Height | `min-height` |
| 34 | Visibility | `visibility` |
| 35 | Outline | `outline` |
| 36 | CSS Units | `rem`, `px`, `%`, etc. |
| 37 | Cursor Types | `cursor: crosshair`, etc. |
| 38 | Multiple Classes | `class="a b"` |
| 39 | CSS Comments | `/* comment */` |
| 40 | Universal Selector | `*` |
| 41 | Group Selector | `h1, h2, h3 { }` |
| 42 | Attribute Selector | `input[type="text"]` |
| 43 | Child Selector | `parent > child` |
| 44 | Descendant Selector | `parent child` |
| 45 | Link States | `:hover`, `:visited`, `:active` |
| 46 | Table Styling | `border-collapse`, `th`, `td` |
| 47 | Form Styling | `.form-demo input` |
| 48 | Image Styling | `width`, `border-radius: 50%` |
| 49 | Transition | `transition` |
| 50 | Transform | `transform: scale()`, `rotate()` |

---


# Responsive Web Design Using Bootstrap 12-Column Grid System

## Introduction

Nowadays users access websites from different devices such as:

* Mobile Phones
* Tablets
* Laptops
* Desktop Computers
* Smart TVs

A website should automatically adjust its layout according to the screen size of the device.

This concept is called:

### Responsive Web Design

### Definition

Responsive Web Design is a technique used to make websites automatically adapt to different screen sizes and resolutions.

---

# Why Responsive Design?

Imagine creating a website on a laptop.

When opened on a mobile phone:

* Text becomes very small
* Images overflow outside the screen
* Horizontal scrolling appears
* Poor user experience

Responsive Design solves these problems by adjusting layouts based on device size.

---

# Viewport Meta Tag

Before creating responsive websites, always include:

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

### Purpose

* Matches website width to device width
* Enables proper responsive behavior
* Essential for mobile devices

---

# Bootstrap and Responsive Design

Bootstrap provides a responsive 12-column grid system.

Instead of writing complex CSS media queries manually, Bootstrap provides ready-made classes.

Examples:

```html
col-6
col-md-4
col-lg-3
```

These classes automatically change layout according to screen size.

---

# Bootstrap Setup

Include Bootstrap CSS inside the head section.

```html
<link rel="stylesheet"
href="https://cdn.jsdelivr.net/npm/bootstrap@4.5.3/dist/css/bootstrap.min.css">
```

Include Bootstrap JavaScript before closing body tag.

```html
<script src="https://cdn.jsdelivr.net/npm/bootstrap@4.5.3/dist/js/bootstrap.bundle.min.js"></script>
```

---

# Bootstrap Grid System

Bootstrap divides every row into 12 equal columns.

Visual Representation:

|1|2|3|4|5|6|7|8|9|10|11|12|

Think of it like a pizza divided into 12 slices.

Every row has a total of 12 columns.

---

# Grid Formula

```text
Total Columns = 12
```

Examples:

```text
6 + 6 = 12
```

```text
4 + 4 + 4 = 12
```

```text
3 + 3 + 3 + 3 = 12
```

```text
5 + 5 + 2 = 12
```

```text
7 + 3 + 2 = 12
```

---

# Bootstrap Structure

Always follow:

```html
Container
   ↓
Row
   ↓
Column
```

Example:

```html
<div class="container">
    <div class="row">
        <div class="col-6">
            Left
        </div>

        <div class="col-6">
            Right
        </div>
    </div>
</div>
```

---

# Understanding Column Widths

```text
col-12 = 100%
col-6  = 50%
col-4  = 33.33%
col-3  = 25%
col-2  = 16.66%
col-1  = 8.33%
```

---

# Example 1: Two Equal Sections

```html
<div class="row container1">

    <div class="col-6 green">
        left
    </div>

    <div class="col-6 red">
        right
    </div>

</div>
```

Calculation:

```text
6 + 6 = 12
```

Output:

```text
Left | Right
```

---

# Example 2: Three Equal Sections

```html
<div class="row container1">

    <div class="col-4 green">
        Container 1
    </div>

    <div class="col-4 red">
        Container 2
    </div>

    <div class="col-4 green">
        Container 3
    </div>

</div>
```

Calculation:

```text
4 + 4 + 4 = 12
```

---

# Example 3: Four Equal Sections

```html
<div class="row container1">

    <div class="col-3 green">
        Container 1
    </div>

    <div class="col-3 red">
        Container 2
    </div>

    <div class="col-3 green">
        Container 3
    </div>

    <div class="col-3 red">
        Container 4
    </div>

</div>
```

Calculation:

```text
3 + 3 + 3 + 3 = 12
```

---

# Example 4

```html
<div class="row container1">

    <div class="col-5 green">
        Container 1
    </div>

    <div class="col-5 red">
        Container 2
    </div>

    <div class="col-2 green">
        Container 3
    </div>

</div>
```

Calculation:

```text
5 + 5 + 2 = 12
```

---

# Example 5

```html
<div class="row container1">

    <div class="col-7 green">
        Container 1
    </div>

    <div class="col-3 red">
        Container 2
    </div>

    <div class="col-2 green">
        Container 3
    </div>

</div>
```

Calculation:

```text
7 + 3 + 2 = 12
```

---

# Bootstrap Breakpoints

Bootstrap provides different breakpoints for different screen sizes.

| Class   | Screen Size | Device             |
| ------- | ----------- | ------------------ |
| col     | All Devices | Mobile             |
| col-sm  | >= 576px    | Tablet             |
| col-md  | >= 768px    | Laptop             |
| col-lg  | >= 992px    | Desktop            |
| col-xl  | >= 1200px   | Large Desktop / TV |
| col-xxl | >= 1400px   | Ultra Wide Screens |

---

# Responsive Grid Example

```html
<div class="row">

    <div class="col-6 col-md-4 red">

    </div>

    <div class="col-6 col-md-4 green">

    </div>

</div>
```

### Mobile

```text
col-6
```

50% width

```text
Red | Green
```

### Laptop and Above

```text
col-md-4
```

Each takes 4 columns.

---

# Another Responsive Example

```html
<div class="row">

    <div class="col-12 col-md-6 red">

    </div>

    <div class="col-12 col-md-6 green">

    </div>

</div>
```

### Mobile

```text
Red
Green
```

### Laptop

```text
Red | Green
```

---

# Complete Responsive Example

```html
<div class="row">

    <div class="col-12 col-sm-6 col-md-5 col-lg-4 col-xl-3 col-xxl-2 red">

    </div>

    <div class="col-12 col-sm-6 col-md-5 col-lg-4 col-xl-3 col-xxl-2 green">

    </div>

</div>
```

---

# Understanding the Above Code

```html
col-12
```

Mobile = Full Width

```text
1 item per row
```

---

```html
col-sm-6
```

Tablet = Half Width

```text
2 items per row
```

---

```html
col-md-5
```

Laptop = 5 Columns

---

```html
col-lg-4
```

Desktop = 4 Columns

```text
3 items per row
```

---

```html
col-xl-3
```

Large Desktop

```text
4 items per row
```

---

```html
col-xxl-2
```

Ultra Wide Screens

```text
6 items per row
```

---

# Most Important Interview Question

## Why Bootstrap Uses 12 Columns?

Because 12 is highly divisible.

```text
12 ÷ 2 = 6
12 ÷ 3 = 4
12 ÷ 4 = 3
12 ÷ 6 = 2
```

This allows flexible layouts.

---


```html
col-12 col-sm-6 col-md-6 col-lg-4 col-xl-3
```

Meaning:

```text
Mobile  = 1 Item

Tablet  = 2 Items

Laptop  = 2 Items

Desktop = 3 Items

TV      = 4 Items
```

---

# CSS Used in Today's Examples

```css
*{
    background-color: beige;
}

.green{
    background-color: green;
    border-radius: 7px;
    border-style: none;
    padding:10px;
}

.red{
    background-color: red;
    border-radius: 7px;
    border-style: none;
    padding:10px;
}

.container1{
   background-color: rgb(202, 234, 245);
   padding-top:10px;
   padding-bottom:10px;
}
```

---

# Key Takeaways

1. Responsive Design makes websites work on all devices.
2. Bootstrap provides a 12-column grid system.
3. One row always contains 12 columns.
4. Use Container → Row → Column structure.
5. Bootstrap breakpoints help create responsive layouts.
6. Different column classes apply at different screen sizes.
7. The most commonly used responsive class combination is:

```html
col-12 col-sm-6 col-md-6 col-lg-4 col-xl-3
```
# Full Code 
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Responsive Design using Bootstrap 12 Grid System</title>

    <!-- Bootstrap CSS -->
    <link rel="stylesheet"
        href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.8/dist/css/bootstrap.min.css">

    <style>
        *{
            background-color: beige;
        }

        .green{
            background-color: green;
            border-radius: 7px;
            border-style: none;
            padding:10px;
            color:white;
            text-align:center;
            min-height:60px;
        }

        .red{
            background-color: red;
            border-radius: 7px;
            border-style: none;
            padding:10px;
            color:white;
            text-align:center;
            min-height:60px;
        }

        .container1{
            background-color: rgb(202, 234, 245);
            padding-top:10px;
            padding-bottom:10px;
        }

        h1,h2,h3,h4,p{
            background:transparent;
        }

        .note{
            background:white;
            padding:20px;
            border-radius:10px;
            margin:20px;
        }
    </style>
</head>

<body>

<div class="container">

    <div class="note">

        <h1>Responsive Design using Bootstrap 12 Grid System</h1>

        <hr>

        <h3>Bootstrap Grid System</h3>

        <p>
            Bootstrap divides every row into 12 equal columns.
        </p>

        <pre>
|1|2|3|4|5|6|7|8|9|10|11|12|
        </pre>

        <hr>

        <h3>Bootstrap Breakpoints</h3>

        <table class="table table-bordered">
            <thead>
                <tr>
                    <th>Class</th>
                    <th>Screen Size</th>
                    <th>Device</th>
                </tr>
            </thead>

            <tbody>
                <tr>
                    <td>col</td>
                    <td>All Devices</td>
                    <td>Mobile</td>
                </tr>

                <tr>
                    <td>col-sm</td>
                    <td>&gt;=576px</td>
                    <td>Tablet</td>
                </tr>

                <tr>
                    <td>col-md</td>
                    <td>&gt;=768px</td>
                    <td>Laptop</td>
                </tr>

                <tr>
                    <td>col-lg</td>
                    <td>&gt;=992px</td>
                    <td>Desktop</td>
                </tr>

                <tr>
                    <td>col-xl</td>
                    <td>&gt;=1200px</td>
                    <td>TV</td>
                </tr>

                <tr>
                    <td>col-xxl</td>
                    <td>&gt;=1400px</td>
                    <td>Large TV</td>
                </tr>
            </tbody>
        </table>

        <hr>

        <h3>Column Widths</h3>

        <pre>
col-12 = 100%
col-6  = 50%
col-4  = 33.33%
col-3  = 25%
col-2  = 16.66%
col-1  = 8.33%
        </pre>

        <hr>

        <h3>Example 1 : col-6 + col-6</h3>

        <div class="row container1">

            <div class="col-6 green">
                Left
            </div>

            <div class="col-6 red">
                Right
            </div>

        </div>

        <p>
            Formula : 6 + 6 = 12
        </p>

        <hr>

        <h3>Example 2 : col-4 + col-4 + col-4</h3>

        <div class="row container1">

            <div class="col-4 green">
                Container 1
            </div>

            <div class="col-4 red">
                Container 2
            </div>

            <div class="col-4 green">
                Container 3
            </div>

        </div>

        <p>
            Formula : 4 + 4 + 4 = 12
        </p>

        <hr>

        <h3>Example 3 : col-3 + col-3 + col-3 + col-3</h3>

        <div class="row container1">

            <div class="col-3 green">
                Container 1
            </div>

            <div class="col-3 red">
                Container 2
            </div>

            <div class="col-3 green">
                Container 3
            </div>

            <div class="col-3 red">
                Container 4
            </div>

        </div>

        <p>
            Formula : 3 + 3 + 3 + 3 = 12
        </p>

        <hr>

        <h3>Example 4 : col-5 + col-5 + col-2</h3>

        <div class="row container1">

            <div class="col-5 green">
                Container 1
            </div>

            <div class="col-5 red">
                Container 2
            </div>

            <div class="col-2 green">
                Container 3
            </div>

        </div>

        <p>
            Formula : 5 + 5 + 2 = 12
        </p>

        <hr>

        <h3>Example 5 : col-7 + col-3 + col-2</h3>

        <div class="row container1">

            <div class="col-7 green">
                Container 1
            </div>

            <div class="col-3 red">
                Container 2
            </div>

            <div class="col-2 green">
                Container 3
            </div>

        </div>

        <p>
            Formula : 7 + 3 + 2 = 12
        </p>

        <hr>

        <h3>Example 6 : 12 Individual Columns</h3>

        <div class="row container1">

            <div class="col-1 green">1</div>
            <div class="col-1 red">2</div>
            <div class="col-1 green">3</div>
            <div class="col-1 red">4</div>
            <div class="col-1 green">5</div>
            <div class="col-1 red">6</div>
            <div class="col-1 green">7</div>
            <div class="col-1 red">8</div>
            <div class="col-1 green">9</div>
            <div class="col-1 red">10</div>
            <div class="col-1 green">11</div>
            <div class="col-1 red">12</div>

        </div>

        <hr>

        <h3>Responsive Example 1</h3>

        <p>
            Mobile = col-6
            <br>
            Laptop = col-md-4
        </p>

        <div class="row">

            <div class="col-6 col-md-4 red">
                Red
            </div>

            <div class="col-6 col-md-4 green">
                Green
            </div>

        </div>

        <hr>

        <h3>Responsive Example 2</h3>

        <p>
            Mobile = Full Width
            <br>
            Laptop = Half Width
        </p>

        <div class="row">

            <div class="col-12 col-md-6 red">
                Red Section
            </div>

            <div class="col-12 col-md-6 green">
                Green Section
            </div>

        </div>

        <hr>

        <h3>Responsive Example 3</h3>

        <div class="row">

            <div class="col-12 col-sm-6 col-md-5 col-lg-4 col-xl-3 col-xxl-2 red">
                Responsive Box
            </div>

            <div class="col-12 col-sm-6 col-md-5 col-lg-4 col-xl-3 col-xxl-2 green">
                Responsive Box
            </div>

        </div>

        <br>

        <pre>
col-12 col-sm-6 col-md-6 col-lg-4 col-xl-3

Mobile   = 1 Item

Tablet   = 2 Items

Laptop   = 2 Items

Desktop  = 3 Items

TV       = 4 Items
        </pre>

        <hr>

        <h3>Important Points</h3>

        <pre>
Container
    ↓
Row
    ↓
Column

One Row = 12 Columns

6 + 6 = 12

4 + 4 + 4 = 12

3 + 3 + 3 + 3 = 12

5 + 5 + 2 = 12

7 + 3 + 2 = 12
        </pre>

    </div>

</div>

<!-- Bootstrap JS -->
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.8/dist/js/bootstrap.bundle.min.js"></script>

</body>
</html>
```
---

# Assignment 1: Responsive Restaurant Website

## Objective

Design a modern restaurant website.

### Sections

#### Navbar

* Logo
* Home
* Menu
* About
* Contact

#### Hero Section

* Restaurant Name
* Tagline
* Order Now Button

#### Popular Dishes

Minimum 6 Food Cards

Each Card Contains:

* Food Image
* Food Name
* Price
* Order Button

#### About Restaurant

* Restaurant Description
* Restaurant Image

#### Contact Section

* Address
* Phone Number
* Email

#### Footer

* Social Media Icons
* Copyright

---

## Responsive Requirement

```html
col-12 col-md-6 col-lg-4
```

### Mobile

```text
Food 1

Food 2

Food 3

Food 4

Food 5

Food 6
```

### Tablet

```text
Food 1     Food 2

Food 3     Food 4

Food 5     Food 6
```

### Desktop

```text
Food 1    Food 2    Food 3

Food 4    Food 5    Food 6
```

---
# Reference Image 
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/920bb120-0e36-4834-9f3f-0b1dc9e263ba" />

---

# Assignment 2: Responsive E-Commerce Product Page

## Objective

Build an Amazon/Flipkart-style product showcase page.

### Sections

#### Navbar

* Logo
* Home
* Products
* Cart
* Contact

#### Banner

* Promotional Banner

#### Product Section

Minimum 8 Products

Each Product Card

* Product Image
* Product Name
* Price
* Buy Now Button

#### Footer

* Quick Links
* Contact Information

---

## Output Structure

### Mobile

```text
----------------
Navbar
----------------

Banner

Product 1

Product 2

Product 3

Product 4

Product 5

Product 6

Product 7

Product 8

Footer
```

---

### Tablet

```text
Product 1   Product 2

Product 3   Product 4

Product 5   Product 6

Product 7   Product 8
```

---

### Desktop

```text
Product1 Product2 Product3 Product4

Product5 Product6 Product7 Product8
```

Use

```html
col-12 col-sm-6 col-lg-3
```

---
# Reference Image 
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/f7d46209-ce22-48f4-bc4e-00f98453f4eb" />

---

# Assignment 3: Responsive College Website

## Objective

Build a professional college landing page.

### Sections

#### Header

* College Logo
* College Name

#### Navbar

* Home
* About
* Courses
* Placements
* Contact

#### Hero Section

* College Banner
* Admission Open Button

#### Courses Section

Minimum 6 Courses

* CSE
* ECE
* EEE
* Civil
* Mechanical
* AI & DS

#### Placement Statistics

Display

* Students Placed
* Highest Package
* Companies Visited

#### Footer

* Address
* Phone
* Email

---

## Output Structure

### Desktop

```text
----------------------------------
Header
----------------------------------

Navbar

----------------------------------
Hero Banner
----------------------------------

Course1  Course2  Course3

Course4  Course5  Course6

----------------------------------
Placement Statistics
----------------------------------

Students   Package   Companies

----------------------------------
Footer
----------------------------------
```

---

### Mobile

```text
Header

Navbar

Hero Banner

Course1

Course2

Course3

Course4

Course5

Course6

Placement Statistics

Footer
```

Use

```html
col-12 col-md-6 col-lg-4
```
---
```html
col-12
col-sm-6
col-md-6
col-lg-4
col-xl-3
```
---
# Reference Image 
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/0a8ec341-e2b8-4f45-9f50-4df9c98232d5" />

---

# JavaScript Introduction

---

# What is JavaScript?

**JavaScript (JS)** is a high-level, interpreted, lightweight, object-oriented, and dynamically typed programming language used to make web pages interactive and dynamic.

HTML provides the **structure** of a webpage.

CSS provides the **style** of a webpage.

JavaScript provides the **behavior and functionality** of a webpage.

Without JavaScript, a website is mostly static. JavaScript allows users to interact with web pages.

Examples include:

* Login Forms
* Registration Forms
* Image Sliders
* Dark Mode
* Pop-up Messages
* Online Calculators
* Games
* Real-time Chat Applications
* Shopping Cart
* Dynamic Content Updates

---

# Real World Example

Think of a Car.

* Engine → JavaScript
* Body → HTML
* Paint → CSS

The car body gives the structure.

The paint makes it attractive.

The engine makes it move.

Similarly,

HTML builds the webpage.

CSS designs the webpage.

JavaScript makes it interactive.

---

# Features of JavaScript

* Easy to Learn
* Lightweight Language
* Object-Oriented
* Cross Platform
* Event Driven
* Dynamic Typing
* Client Side Scripting
* Server Side Development using Node.js
* Supports Asynchronous Programming
* Large Community Support

---

# Why Learn JavaScript?

JavaScript is one of the most popular programming languages in the world.

It is used in:

* Frontend Development
* Backend Development
* Mobile App Development
* Desktop Applications
* Game Development
* Artificial Intelligence
* APIs
* Cloud Applications

---

# Applications of JavaScript

## Frontend

Examples

* Interactive Websites
* Animations
* Forms
* Dashboard

Frameworks

* React
* Angular
* Vue

---

## Backend

Using

Node.js

Examples

* REST APIs
* Authentication
* Database Operations

---

## Mobile Apps

Using

* React Native

---

## Desktop Applications

Using

* Electron

Applications

* VS Code
* Discord
* Slack

---

# Advantages of JavaScript

* Fast Execution
* Easy Syntax
* Huge Community
* Runs in Browser
* No Compilation Required
* Free to Use
* Platform Independent

---

# JavaScript Versions

| Version | Features                             |
| ------- | ------------------------------------ |
| ES5     | Basic JavaScript                     |
| ES6     | let, const, Arrow Functions, Classes |
| ES7     | Async Features                       |
| ES8     | Async Await                          |
| ES2020+ | Modern Features                      |

Today we mostly use **ES6+ JavaScript**.

---

# How JavaScript Works

```
User Clicks Button
        │
        ▼
Browser Receives Event
        │
        ▼
JavaScript Executes
        │
        ▼
HTML Updated
        │
        ▼
User Sees Result
```

---

# Ways to Add JavaScript

## 1. Inline JavaScript

```html
<button onclick="alert('Welcome')">
Click
</button>
```

Not recommended for large applications.

---

## 2. Internal JavaScript

```html
<script>

console.log("Hello JavaScript");

</script>
```

---

## 3. External JavaScript

HTML

```html
<script src="script.js"></script>
```

script.js

```javascript
console.log("External JavaScript");
```

Best Practice.

---

# First JavaScript Program

```javascript
console.log("Hello World");
```

Output

```
Hello World
```

---

# Printing Multiple Lines

```javascript
console.log("Welcome");
console.log("JavaScript");
console.log("Course");
```

Output

```
Welcome
JavaScript
Course
```

---

# Comments

Comments are ignored by JavaScript.

Used to explain code.

---

## Single Line Comment

```javascript
// This is comment
```

---

## Multi Line Comment

```javascript
/*
This
is
comment
*/
```

---

# VARIABLES

---

# What is a Variable?

A variable is a container used to store data.

Variables help us store information that can be used later.

Real-world Example

Think of a Water Bottle.

Bottle = Variable

Water = Data

You can fill different liquids in the same bottle.

Similarly,

Variables store different values.

---

# Why Variables?

Without Variables

```javascript
console.log("Rahul");
console.log("Rahul");
console.log("Rahul");
```

With Variables

```javascript
let name = "Rahul";

console.log(name);
console.log(name);
console.log(name);
```

Much easier to manage.

---

# Syntax

```javascript
keyword variableName = value;
```

Example

```javascript
let age = 20;
```

---

# Types of Variables

JavaScript has three keywords.

```
var

let

const
```

---

# var

Old way of declaring variables.

```javascript
var name = "Rahul";
```

---

Properties

* Can Redeclare
* Can Reassign
* Function Scoped

Example

```javascript
var a = 10;

var a = 20;

a = 30;

console.log(a);
```

Output

```
30
```

---

# let

Modern way.

Most commonly used.

```javascript
let age = 22;
```

Properties

* Cannot Redeclare
* Can Reassign
* Block Scoped

Example

```javascript
let marks = 90;

marks = 95;

console.log(marks);
```

Output

```
95
```

---

Redeclaration Error

```javascript
let age = 20;

let age = 30;
```

Output

```
Error
```

---

# const

Constant Variable.

Cannot change value.

```javascript
const PI = 3.14;
```

Properties

* Cannot Redeclare
* Cannot Reassign
* Block Scoped

Example

```javascript
const country = "India";

console.log(country);
```

Output

```
India
```

---

Trying to Change

```javascript
const country = "India";

country = "USA";
```

Output

```
Error
```

---

# Comparison

| Feature   | var      | let   | const |
| --------- | -------- | ----- | ----- |
| Redeclare | Yes      | No    | No    |
| Reassign  | Yes      | Yes   | No    |
| Scope     | Function | Block | Block |
| Modern    | No       | Yes   | Yes   |

---

# Variable Naming Rules

Allowed

```javascript
let name;

let studentName;

let student_name;

let student1;

let $price;

let _total;
```

---

Not Allowed

```javascript
let 1name;

let first-name;

let class;

let let;
```

---

# Best Practices

Good

```javascript
let firstName;

let studentAge;

let totalAmount;
```

Bad

```javascript
let a;

let b;

let x1;

let abc123;
```

Always use meaningful names.

---

# Multiple Variables

```javascript
let name = "John";

let age = 25;

let city = "Hyderabad";
```

---

Or

```javascript
let a = 10,
    b = 20,
    c = 30;
```

---

# Variable Example

```javascript
let student = "Ravi";

let age = 21;

console.log(student);

console.log(age);
```

Output

```
Ravi

21
```

---

# Swapping Variables

```javascript
let a = 10;

let b = 20;

let temp = a;

a = b;

b = temp;

console.log(a);

console.log(b);
```

Output

```
20

10
```

---

# DATA TYPES

---

# What is Data Type?

A Data Type specifies what type of value a variable stores.

Example

Age

```
20
```

Name

```
Rahul
```

Married

```
true
```

Different values have different data types.

---

# JavaScript Data Types

Two Categories

```
Primitive

Non Primitive
```

---

# Primitive Data Types

1 Number

2 String

3 Boolean

4 Undefined

5 Null

6 BigInt

7 Symbol

---

# Non Primitive

Objects

Arrays

Functions

Dates

Maps

Sets

---

# Number

Stores

* Integer
* Decimal

Example

```javascript
let age = 20;

let price = 99.99;
```

Output

```
20

99.99
```

---

Arithmetic

```javascript
let a = 10;

let b = 5;

console.log(a+b);

console.log(a-b);

console.log(a*b);

console.log(a/b);
```

Output

```
15

5

50

2
```

---

# String

Stores Text.

Can use

```
" "

' '

` `
```

Example

```javascript
let name = "Rahul";

console.log(name);
```

Output

```
Rahul
```

---

Concatenation

```javascript
let first = "Java";

let second = "Script";

console.log(first + second);
```

Output

```
JavaScript
```

---

Template Literal

```javascript
let name = "Rahul";

let age = 20;

console.log(`My name is ${name} and age is ${age}`);
```

Output

```
My name is Rahul and age is 20
```

---

# Boolean

Stores

```
true

false
```

Example

```javascript
let isStudent = true;

console.log(isStudent);
```

Output

```
true
```

---

# Undefined

Variable declared but not assigned.

```javascript
let city;

console.log(city);
```

Output

```
undefined
```

---

# Null

Represents empty value.

```javascript
let phone = null;

console.log(phone);
```

Output

```
null
```

---

# BigInt

Used for very large integers.

```javascript
let big = 123456789012345678901234567890n;

console.log(big);
```

---

# Symbol

Unique identifier.

```javascript
let id = Symbol("id");
```

Mostly used in advanced JavaScript.

---

# Object

Stores data in key-value pairs.

```javascript
let student = {

name : "Rahul",

age : 20,

city : "Hyderabad"

};

console.log(student);
```

Output

```
{name:"Rahul",age:20,city:"Hyderabad"}
```

---

# Array

Stores multiple values.

```javascript
let colors = [

"Red",

"Blue",

"Green"

];

console.log(colors);
```

Output

```
["Red","Blue","Green"]
```

---

# Function

Stores reusable code.

```javascript
function greet(){

console.log("Hello");

}

greet();
```

Output

```
Hello
```

---

# typeof Operator

Used to identify data type.

Syntax

```javascript
typeof variable
```

Example

```javascript
console.log(typeof 10);

console.log(typeof "Java");

console.log(typeof true);

console.log(typeof undefined);

console.log(typeof null);
```

Output

```
number

string

boolean

undefined

object
```

**Note:** `typeof null` returns `"object"` due to a historical bug in JavaScript.

---

# Type Conversion

## Automatic Conversion (Implicit)

```javascript
console.log("10" + 5);
```

Output

```
105
```

Because number `5` is converted into a string.

---

```javascript
console.log("10" - 5);
```

Output

```
5
```

Here JavaScript converts `"10"` into a number automatically.

---

## Manual Conversion (Explicit)

Convert String to Number

```javascript
let age = "25";

let numAge = Number(age);

console.log(numAge);

console.log(typeof numAge);
```

Output

```
25

number
```

---

Convert Number to String

```javascript
let price = 500;

let text = String(price);

console.log(text);

console.log(typeof text);
```

Output

```
500

string
```

---

Convert String to Boolean

```javascript
console.log(Boolean("Hello"));

console.log(Boolean(""));
```

Output

```
true

false
```

---

# Primitive vs Non-Primitive

| Primitive                | Non-Primitive           |
| ------------------------ | ----------------------- |
| Stores single value      | Stores multiple values  |
| Immutable                | Mutable                 |
| Compared by value        | Compared by reference   |
| Examples: Number, String | Object, Array, Function |

---

# Memory Tip

```
Primitive
↓

Simple Values

Number

String

Boolean

Undefined

Null

BigInt

Symbol
```

```
Non Primitive
↓

Complex Values

Object

Array

Function
```

---

# Common Beginner Mistakes

 Using `var` everywhere.

 Prefer `let` and `const`.

---

 Variable names like

```javascript
let a;
let x;
let abc;
```

 Use meaningful names.

```javascript
let studentName;
let totalMarks;
let employeeSalary;
```

---

 Forgetting quotes for strings.

Wrong

```javascript
let name = Rahul;
```

Correct

```javascript
let name = "Rahul";
```

---

 Confusing `=` and `==`

`=` → Assignment

`==` → Comparison (covered later)

---

# Interview Questions

# JavaScript Interview Questions & Answers

---

## 1. What is JavaScript?

**Answer:**

JavaScript is a high-level, interpreted programming language used to make web pages interactive and dynamic. It allows developers to create features like form validation, animations, popups, API calls, games, and much more.

**Example:**
```javascript
console.log("Hello, JavaScript!");
```

---

## 2. Difference between HTML, CSS, and JavaScript?

| HTML | CSS | JavaScript |
|------|-----|------------|
| Creates the structure of a webpage | Styles the webpage | Adds functionality and interactivity |
| Skeleton | Design | Brain |
| Uses tags | Uses selectors | Uses programming logic |

**Example:**

```html
<h1>Hello</h1>
```

```css
h1{
    color: blue;
}
```

```javascript
document.querySelector("h1").innerText = "Welcome";
```

---

## 3. What are Variables?

**Answer:**

Variables are containers used to store data in memory so it can be used later in the program.

**Example:**

```javascript
let name = "John";
let age = 25;

console.log(name);
console.log(age);
```

---

## 4. Difference between `var`, `let`, and `const`?

| var | let | const |
|------|------|--------|
| Function scoped | Block scoped | Block scoped |
| Can be redeclared | Cannot be redeclared | Cannot be redeclared |
| Can be reassigned | Can be reassigned | Cannot be reassigned |
| Hoisted with `undefined` | Hoisted but in TDZ | Hoisted but in TDZ |

**Example:**

```javascript
var a = 10;
var a = 20; // Allowed

let b = 30;
// let b = 40; // Error

const c = 50;
// c = 60; // Error
```

---

## 5. What is Block Scope?

**Answer:**

A block scope means a variable declared inside `{}` can only be accessed within that block.

`let` and `const` are block-scoped.

**Example:**

```javascript
{
    let x = 10;
    console.log(x);
}

// console.log(x); // Error
```

---

## 6. What are Primitive Data Types?

**Answer:**

Primitive data types store a single value.

There are **7 primitive data types**:

- String
- Number
- Boolean
- Undefined
- Null
- BigInt
- Symbol

**Example:**

```javascript
let name = "John";
let age = 22;
let isStudent = true;
let salary;
let value = null;
let big = 12345678901234567890n;
let id = Symbol("id");
```

---

## 7. What is `undefined`?

**Answer:**

`undefined` means a variable has been declared but has not been assigned any value.

**Example:**

```javascript
let x;

console.log(x);
```

**Output**

```
undefined
```

---

## 8. Difference between `undefined` and `null`?

| undefined | null |
|------------|------|
| Default value assigned by JavaScript | Assigned intentionally by the programmer |
| Means value is not assigned | Means empty value |
| Type is `"undefined"` | Type is `"object"` (historical bug) |

**Example:**

```javascript
let a;
let b = null;

console.log(a);
console.log(b);
```

---

## 9. What is `typeof`?

**Answer:**

`typeof` is an operator used to determine the data type of a variable or value.

**Example:**

```javascript
console.log(typeof "Hello");
console.log(typeof 100);
console.log(typeof true);
console.log(typeof undefined);
```

**Output**

```
string
number
boolean
undefined
```

---

## 10. Why does `typeof null` return `"object"`?

**Answer:**

This is a historical bug in JavaScript.

When JavaScript was first created, values were stored internally in a way that caused `null` to be identified as an object. This mistake has been preserved to maintain backward compatibility with older code.

**Example:**

```javascript
console.log(typeof null);
```

**Output**

```
object
```

> **Interview Tip:**  
> Although `typeof null` returns `"object"`, **`null` is not actually an object**.

---

## 11. What is a Template Literal?

**Answer:**

Template literals allow you to create strings using backticks (`` ` ``). They support multi-line strings and variable interpolation using `${}`.

**Example:**

```javascript
let name = "John";
let age = 25;

console.log(`My name is ${name} and I am ${age} years old.`);
```

**Output**

```
My name is John and I am 25 years old.
```

---

## 12. What is Type Conversion?

**Answer:**

Type conversion is the process of converting one data type into another.

There are two types:

- Implicit Conversion
- Explicit Conversion

---

## 13. Difference between Implicit and Explicit Conversion?

| Implicit Conversion | Explicit Conversion |
|---------------------|--------------------|
| Done automatically by JavaScript | Done manually by the programmer |
| Also called Type Coercion | Uses conversion functions |

### Implicit Example

```javascript
console.log("5" + 2);
```

**Output**

```
52
```

---

### Explicit Example

```javascript
let num = Number("5");

console.log(num + 2);
```

**Output**

```
7
```

---

## 14. What is BigInt?

**Answer:**

BigInt is a primitive data type used to store very large integers that exceed the safe limit of the `Number` type.

A BigInt is created by adding `n` at the end of an integer.

**Example:**

```javascript
let bigNumber = 123456789012345678901234567890n;

console.log(bigNumber);
```

**Why use BigInt?**

The `Number` type can safely store integers only up to:

```javascript
9007199254740991
```

For larger integers, use `BigInt`.

---

## 15. What are Non-Primitive Data Types?

**Answer:**

Non-primitive data types can store multiple values and are mutable (their contents can be changed).

Common non-primitive data types include:

- Object
- Array
- Function
- Date
- Map
- Set

### Object Example

```javascript
let student = {
    name: "Rahul",
    age: 22
};
```

### Array Example

```javascript
let colors = ["Red", "Green", "Blue"];
```

### Function Example

```javascript
function greet() {
    console.log("Hello");
}
```

---

# Quick Revision

| Question | Short Answer |
|-----------|--------------|
| What is JavaScript? | Programming language for web interactivity |
| HTML | Structure |
| CSS | Styling |
| JavaScript | Functionality |
| Variables | Store data |
| var | Function scoped |
| let | Block scoped, reassignable |
| const | Block scoped, cannot reassign |
| Primitive Types | String, Number, Boolean, Undefined, Null, BigInt, Symbol |
| Undefined | Variable declared but no value assigned |
| Null | Intentional empty value |
| typeof | Returns the data type |
| typeof null | `"object"` (historical bug) |
| Template Literal | String using backticks and `${}` |
| Type Conversion | Changing one data type to another |
| Implicit Conversion | Automatic conversion |
| Explicit Conversion | Manual conversion |
| BigInt | Stores very large integers |
| Non-Primitive Types | Object, Array, Function, Date, Map, Set |

---

# Practice Programs

### Program 1

```javascript
let name = "Apex";

console.log(name);
```

---

### Program 2

```javascript
let age = 22;

console.log(age);
```

---

### Program 3

```javascript
let first = "Hello";

let second = "World";

console.log(first + " " + second);
```

---

### Program 4

```javascript
const PI = 3.14159;

console.log(PI);
```

---

### Program 5

```javascript
let student = {
    name: "Rahul",
    age: 20,
    course: "Java Full Stack"
};

console.log(student);
```

---

### Program 6

```javascript
let fruits = ["Apple", "Mango", "Orange"];

console.log(fruits);
```

---

### Program 7

```javascript
let salary = "50000";

console.log(Number(salary));
```

---

# Operators

---

# What is an Operator?

An **Operator** is a special symbol that performs an operation on one or more values (operands).

In simple words,

> Operators tell JavaScript what operation should be performed.

Example

```javascript
let a = 10;
let b = 5;

console.log(a + b);
```

Output

```
15
```

Here,

* `+` is the operator.
* `10` and `5` are operands.

---

# Real World Example

Imagine you are using a calculator.

```
10 + 5
```

The `+` button tells the calculator to add two numbers.

Similarly,

JavaScript operators perform operations like:

* Addition
* Subtraction
* Comparison
* Assignment
* Logical Operations
* Increment
* Decrement

---

# Types of Operators

JavaScript provides several types of operators.

1. Arithmetic Operators
2. Assignment Operators
3. Comparison Operators
4. Logical Operators
5. Increment & Decrement Operators
6. Ternary Operator

---

# 1. Arithmetic Operators

Arithmetic operators are used to perform mathematical calculations.

| Operator | Meaning             |
| -------- | ------------------- |
| +        | Addition            |
| -        | Subtraction         |
| *        | Multiplication      |
| /        | Division            |
| %        | Modulus (Remainder) |
| **       | Exponent (Power)    |

---

## Addition (+)

Adds two numbers.

Syntax

```javascript
value1 + value2
```

Example

```javascript
let a = 20;
let b = 10;

console.log(a + b);
```

Output

```
30
```

---

## Subtraction (-)

Subtracts one value from another.

```javascript
let a = 20;
let b = 10;

console.log(a - b);
```

Output

```
10
```

---

## Multiplication (*)

```javascript
let a = 5;
let b = 6;

console.log(a * b);
```

Output

```
30
```

---

## Division (/)

```javascript
let a = 20;
let b = 5;

console.log(a / b);
```

Output

```
4
```

---

## Modulus (%)

Returns the remainder after division.

Example

```javascript
console.log(10 % 3);
```

Output

```
1
```

Explanation

```
10 ÷ 3 = 3

3 × 3 = 9

10 - 9 = 1
```

So,

```
Remainder = 1
```

---

## Exponent (**)

Calculates the power of a number.

```javascript
console.log(2 ** 3);
```

Output

```
8
```

Meaning

```
2 × 2 × 2
```

---

# Arithmetic Example

```javascript
let a = 15;
let b = 4;

console.log(a + b);
console.log(a - b);
console.log(a * b);
console.log(a / b);
console.log(a % b);
```

Output

```
19
11
60
3.75
3
```

---

# 2. Assignment Operators

Assignment operators assign values to variables.

| Operator | Meaning             |
| -------- | ------------------- |
| =        | Assign              |
| +=       | Add and Assign      |
| -=       | Subtract and Assign |
| *=       | Multiply and Assign |
| /=       | Divide and Assign   |
| %=       | Modulus and Assign  |

---

## =

```javascript
let age = 20;
```

---

## +=

```javascript
let marks = 50;

marks += 10;

console.log(marks);
```

Output

```
60
```

Equivalent to

```javascript
marks = marks + 10;
```

---

## -=

```javascript
let marks = 80;

marks -= 20;

console.log(marks);
```

Output

```
60
```

---

## *=

```javascript
let value = 5;

value *= 4;

console.log(value);
```

Output

```
20
```

---

## /=

```javascript
let value = 40;

value /= 5;

console.log(value);
```

Output

```
8
```

---

## %=

```javascript
let value = 25;

value %= 7;

console.log(value);
```

Output

```
4
```

---

# 3. Comparison Operators

Comparison operators compare two values.

The result is always

```
true

or

false
```

| Operator | Meaning               |
| -------- | --------------------- |
| ==       | Equal                 |
| ===      | Strict Equal          |
| !=       | Not Equal             |
| !==      | Strict Not Equal      |
| >        | Greater Than          |
| <        | Less Than             |
| >=       | Greater Than or Equal |
| <=       | Less Than or Equal    |

---

## == (Loose Equality)

Checks only values.

```javascript
console.log(10 == "10");
```

Output

```
true
```

Because JavaScript converts the string into a number.

---

## === (Strict Equality)

Checks both value and data type.

```javascript
console.log(10 === "10");
```

Output

```
false
```

Number is different from String.

---

## !=

```javascript
console.log(10 != 5);
```

Output

```
true
```

---

## !==

```javascript
console.log(10 !== "10");
```

Output

```
true
```

---

## Greater Than

```javascript
console.log(20 > 10);
```

Output

```
true
```

---

## Less Than

```javascript
console.log(20 < 10);
```

Output

```
false
```

---

## Greater Than or Equal

```javascript
console.log(50 >= 50);
```

Output

```
true
```

---

## Less Than or Equal

```javascript
console.log(20 <= 30);
```

Output

```
true
```

---

# Difference Between == and ===

| ==                         | ===                   |
| -------------------------- | --------------------- |
| Checks only value          | Checks value and type |
| Performs type conversion   | No type conversion    |
| Less strict                | More strict           |
| Avoid in modern JavaScript | Recommended           |

Example

```javascript
console.log(5 == "5");
```

Output

```
true
```

```javascript
console.log(5 === "5");
```

Output

```
false
```

**Best Practice:** Always prefer `===` and `!==` to avoid unexpected type conversion.

---

# 4. Logical Operators

Logical operators combine multiple conditions.

| Operator | Meaning |
| -------- | ------- |
| &&       | AND     |
| ||       | OR      |
| !        | NOT     |

---

## AND (&&)

Returns `true` only if **all conditions are true**.

Truth Table

| A     | B     | Result |
| ----- | ----- | ------ |
| true  | true  | true   |
| true  | false | false  |
| false | true  | false  |
| false | false | false  |

Example

```javascript
let age = 22;
let hasLicense = true;

console.log(age >= 18 && hasLicense);
```

Output

```
true
```

---

## OR (||)

Returns `true` if **at least one condition is true**.

Truth Table

| A     | B     | Result |
| ----- | ----- | ------ |
| true  | true  | true   |
| true  | false | true   |
| false | true  | true   |
| false | false | false  |

Example

```javascript
let isHoliday = false;
let isSunday = true;

console.log(isHoliday || isSunday);
```

Output

```
true
```

---

## NOT (!)

Reverses a boolean value.

```javascript
console.log(!true);
console.log(!false);
```

Output

```
false
true
```

---

# Operator Precedence

JavaScript follows the **BODMAS** rule.

Priority

1. `()`
2. `**`
3. `* / %`
4. `+ -`
5. Comparison Operators
6. Logical Operators

Example

```javascript
console.log(10 + 5 * 2);
```

Output

```
20
```

Explanation

```
5 × 2 = 10

10 + 10 = 20
```

---

# Increment Operator (++)

Increases the value by **1**.

```javascript
let count = 5;

count++;

console.log(count);
```

Output

```
6
```

---

## Pre Increment

```javascript
let a = 5;

console.log(++a);
```

Output

```
6
```

---

## Post Increment

```javascript
let a = 5;

console.log(a++);
console.log(a);
```

Output

```
5
6
```

---

# Decrement Operator (--)

Decreases the value by **1**.

```javascript
let count = 10;

count--;

console.log(count);
```

Output

```
9
```

---

## Pre Decrement

```javascript
let a = 10;

console.log(--a);
```

Output

```
9
```

---

## Post Decrement

```javascript
let a = 10;

console.log(a--);
console.log(a);
```

Output

```
10
9
```

---

# Ternary Operator

The ternary operator is a **short form of the `if...else` statement**. It evaluates a condition and returns one value if the condition is `true`, otherwise it returns another value.

### Syntax

```javascript
condition ? valueIfTrue : valueIfFalse;
```

---

### Example

```javascript
let age = 20;

let result = age >= 18 ? "Eligible to Vote" : "Not Eligible";

console.log(result);
```

Output

```
Eligible to Vote
```

---

### Another Example

```javascript
let marks = 45;

let result = marks >= 35 ? "Pass" : "Fail";

console.log(result);
```

Output

```
Pass
```

---

# Common Beginner Mistakes

 Using `=` instead of `==` or `===`.

Wrong

```javascript
if (age = 18)
```

Correct

```javascript
if (age === 18)
```

---

 Using `==` when strict comparison is needed.

```javascript
5 == "5"
```

Better

```javascript
5 === "5"
```

---

 Forgetting operator precedence.

Wrong assumption

```javascript
10 + 5 * 2 = 30
```

Correct

```
10 + (5 × 2) = 20
```

---

 Confusing pre-increment and post-increment.

```javascript
let a = 5;

console.log(a++);
```

Output

```
5
```

Many beginners expect `6`, but `a++` returns the current value first and increments afterward.

---

# Memory Tips

### Arithmetic

```
+  Add

-  Subtract

*  Multiply

/  Divide

%  Remainder

** Power
```

---

### Comparison

```
==   Value

===  Value + Type

!=   Not Equal

!==  Strict Not Equal
```

---

### Logical

```
&&

Both True

||

Any One True

!

Reverse Boolean
```

---

# Interview Questions

1. What is an operator in JavaScript?
2. What are operands?
3. Explain arithmetic operators.
4. What is the difference between `%` and `/`?
5. What is the purpose of assignment operators?
6. Explain the difference between `==` and `===`.
7. Why is `===` recommended over `==`?
8. What are logical operators?
9. Explain the truth table of `&&` and `||`.
10. What is the difference between pre-increment and post-increment?
11. What is operator precedence?
12. What is the ternary operator?
13. When should you use the ternary operator?
14. What does `!true` return?
15. What is the output of `10 + 5 * 2` and why?

---

# Practice Programs

### Program 1 - Arithmetic Operations

```javascript
let a = 12;
let b = 5;

console.log("Addition:", a + b);
console.log("Subtraction:", a - b);
console.log("Multiplication:", a * b);
console.log("Division:", a / b);
console.log("Remainder:", a % b);
```

---

### Program 2 - Assignment Operators

```javascript
let marks = 50;

marks += 20;
marks -= 5;
marks *= 2;
marks /= 5;

console.log(marks);
```

---

### Program 3 - Comparison Operators

```javascript
let x = 25;
let y = "25";

console.log(x == y);
console.log(x === y);
console.log(x != y);
console.log(x !== y);
```

---

### Program 4 - Logical Operators

```javascript
let age = 22;
let hasLicense = true;

console.log(age >= 18 && hasLicense);
console.log(age >= 18 || hasLicense);
console.log(!hasLicense);
```

---

### Program 5 - Increment & Decrement

```javascript
let count = 10;

console.log(count++);
console.log(count);

console.log(++count);

console.log(count--);
console.log(count);

console.log(--count);
```

---

### Program 6 - Ternary Operator

```javascript
let temperature = 32;

let weather = temperature > 30 ? "Hot Day" : "Pleasant Day";

console.log(weather);
```

---

### Program 7 - Mixed Operators

```javascript
let num1 = 15;
let num2 = 4;

let result = (num1 + num2) * 2 > 30 && num1 % num2 !== 0;

console.log(result);
```

---

# Summary

* Operators are symbols used to perform operations on values.
* Arithmetic operators perform mathematical calculations.
* Assignment operators assign and update values.
* Comparison operators return `true` or `false`.
* Use `===` and `!==` for strict comparisons.
* Logical operators combine multiple conditions.
* Increment (`++`) and decrement (`--`) modify values by one.
* Understand the difference between pre and post increment/decrement.
* The ternary operator is a concise alternative to `if...else`.
* Always remember operator precedence (BODMAS) to avoid unexpected results.

---

#  

# Conditional Statements

---

# What are Conditional Statements?

A **Conditional Statement** is used to make decisions in a program.

It allows JavaScript to execute different blocks of code depending on whether a condition is **true** or **false**.

In simple words,

> Conditional statements help the program decide **what to do next**.

---

# Real World Example

Imagine you are logging into a website.

```text
Enter Username
        │
        ▼
Enter Password
        │
        ▼
Password Correct?
      /      \
    Yes       No
    │          │
    ▼          ▼
 Login     Show Error
```

The decision is based on a **condition**.

---

# Why do we need Conditional Statements?

Without Conditions

```javascript
console.log("You can vote.");
```

The message is printed for everyone.

With Conditions

```javascript
let age = 20;

if(age >= 18){
    console.log("You can vote.");
}
```

Now the message is displayed only when the condition is true.

---

# Types of Conditional Statements

JavaScript provides the following conditional statements.

* if
* if...else
* else if
* Nested if
* switch
* Ternary Operator (Already Learned)

---

# if Statement

The **if** statement executes a block of code only when the condition is **true**.

---

## Syntax

```javascript
if(condition){
    // Code
}
```

---

## Flow

```text
Condition
   │
 ┌─┴─────┐
 │ True  │
 ▼        │
Execute   │
 Code     │
 │         │
 └─────────┘
```

---

## Example

```javascript
let age = 20;

if(age >= 18){
    console.log("Eligible to Vote");
}
```

Output

```text
Eligible to Vote
```

---

## Example 2

```javascript
let marks = 80;

if(marks >= 35){
    console.log("Pass");
}
```

Output

```text
Pass
```

---

# if...else Statement

If the condition is true,

execute one block.

Otherwise,

execute another block.

---

## Syntax

```javascript
if(condition){

}

else{

}
```

---

## Flow

```text
Condition
    │
 ┌──┴─────┐
 │ True   │ False
 ▼         ▼
Block 1  Block 2
```

---

## Example

```javascript
let age = 15;

if(age >= 18){
    console.log("Eligible");
}
else{
    console.log("Not Eligible");
}
```

Output

```text
Not Eligible
```

---

## Example

```javascript
let number = 10;

if(number % 2 == 0){
    console.log("Even Number");
}
else{
    console.log("Odd Number");
}
```

Output

```text
Even Number
```

---

# else if Statement

Used when there are **multiple conditions**.

---

## Syntax

```javascript
if(condition1){

}
else if(condition2){

}
else{

}
```

---

## Example

```javascript
let marks = 82;

if(marks >= 90){
    console.log("Grade A+");
}
else if(marks >= 75){
    console.log("Grade A");
}
else if(marks >= 60){
    console.log("Grade B");
}
else if(marks >= 35){
    console.log("Grade C");
}
else{
    console.log("Fail");
}
```

Output

```text
Grade A
```

---

# Real World Example

ATM Machine

```text
Balance > ₹5000
        │
      Yes
        │
Premium Customer

Otherwise

Regular Customer
```

---

# Nested if Statement

An **if statement inside another if statement** is called a Nested if.

---

## Syntax

```javascript
if(condition1){

    if(condition2){

    }

}
```

---

## Example

```javascript
let age = 20;
let hasLicense = true;

if(age >= 18){

    if(hasLicense){
        console.log("You Can Drive");
    }

}
```

Output

```text
You Can Drive
```

---

## Example 2

```javascript
let username = "admin";
let password = "12345";

if(username == "admin"){

    if(password == "12345"){
        console.log("Login Success");
    }
    else{
        console.log("Wrong Password");
    }

}
else{
    console.log("Invalid User");
}
```

Output

```text
Login Success
```

---

# switch Statement

The **switch statement** is used when there are multiple possible values for one variable.

It is cleaner than writing many `else if` statements.

---

## Syntax

```javascript
switch(expression){

case value:

    code;

    break;

default:

    code;

}
```

---

## Flow

```text
Expression
     │
 ┌───┼──────────────┐
 │   │              │
Case1 Case2      Default
```

---

## Example

```javascript
let day = 3;

switch(day){

case 1:
console.log("Monday");
break;

case 2:
console.log("Tuesday");
break;

case 3:
console.log("Wednesday");
break;

default:
console.log("Invalid");
}
```

Output

```text
Wednesday
```

---

## Example

```javascript
let color = "Red";

switch(color){

case "Blue":
console.log("Blue Color");
break;

case "Green":
console.log("Green Color");
break;

case "Red":
console.log("Red Color");
break;

default:
console.log("Unknown");
}
```

Output

```text
Red Color
```

---

# Importance of break

Without `break`, JavaScript continues executing the remaining cases.

Example

```javascript
let day = 2;

switch(day){

case 1:
console.log("Monday");

case 2:
console.log("Tuesday");

case 3:
console.log("Wednesday");

}
```

Output

```text
Tuesday
Wednesday
```

---

Correct Version

```javascript
let day = 2;

switch(day){

case 1:
console.log("Monday");
break;

case 2:
console.log("Tuesday");
break;

case 3:
console.log("Wednesday");
break;

}
```

Output

```text
Tuesday
```

---

# if vs switch

| if                    | switch                  |
| --------------------- | ----------------------- |
| Works with conditions | Works with values       |
| More flexible         | Cleaner for many values |
| Used for ranges       | Used for exact matches  |

---

# LOOPS

---

# What is a Loop?

A **Loop** is used to execute the same block of code multiple times.

Instead of writing the same code repeatedly,

we use loops.

---

# Real World Example

Suppose you need to print

```text
Welcome
```

100 times.

Without Loop

```javascript
console.log("Welcome");
console.log("Welcome");
console.log("Welcome");
```

100 lines...

With Loop

```javascript
for(let i=1;i<=100;i++){

console.log("Welcome");

}
```

---

# Types of Loops

* for
* while
* do...while
* Nested Loop

---

# for Loop

The **for loop** is used when we know how many times the loop should execute.

---

## Syntax

```javascript
for(initialization; condition; increment){

}
```

---

## Parts of for Loop

```text
Initialization

↓

Condition

↓

Code Executes

↓

Increment

↓

Condition Again
```

---

## Flow Diagram

```text
Start
  │
Initialization
  │
Condition
  │
True
  │
Code
  │
Increment
  │
Condition Again
  │
False
  ▼
Stop
```

---

## Example

```javascript
for(let i=1;i<=5;i++){

console.log(i);

}
```

Output

```text
1
2
3
4
5
```

---

## Print Even Numbers

```javascript
for(let i=2;i<=20;i+=2){

console.log(i);

}
```

Output

```text
2
4
6
8
10
12
14
16
18
20
```

---

## Print Odd Numbers

```javascript
for(let i=1;i<=19;i+=2){

console.log(i);

}
```

---

# while Loop

The **while loop** executes as long as the condition remains true.

---

## Syntax

```javascript
while(condition){

}
```

---

## Example

```javascript
let i=1;

while(i<=5){

console.log(i);

i++;

}
```

Output

```text
1
2
3
4
5
```

---

# do...while Loop

The **do...while** loop executes the block **at least once**, even if the condition is false.

---

## Syntax

```javascript
do{

}
while(condition);
```

---

## Example

```javascript
let i=1;

do{

console.log(i);

i++;

}
while(i<=5);
```

Output

```text
1
2
3
4
5
```

---

## Difference

```javascript
let i=10;

while(i<=5){

console.log(i);

}
```

Output

```text
Nothing Printed
```

---

```javascript
let i=10;

do{

console.log(i);

}
while(i<=5);
```

Output

```text
10
```

---

# break Statement

Used to stop a loop immediately.

---

## Example

```javascript
for(let i=1;i<=10;i++){

if(i==6){

break;

}

console.log(i);

}
```

Output

```text
1
2
3
4
5
```

---

# continue Statement

Skips the current iteration.

---

## Example

```javascript
for(let i=1;i<=5;i++){

if(i==3){

continue;

}

console.log(i);

}
```

Output

```text
1
2
4
5
```

---

# Nested Loop

A loop inside another loop.

---

## Example

```javascript
for(let i=1;i<=3;i++){

for(let j=1;j<=3;j++){

console.log(i,j);

}

}
```

Output

```text
1 1
1 2
1 3
2 1
2 2
2 3
3 1
3 2
3 3
```

---

# Multiplication Table

```javascript
let number=5;

for(let i=1;i<=10;i++){

console.log(number+" x "+i+" = "+number*i);

}
```

Output

```text
5 x 1 = 5
5 x 2 = 10
5 x 3 = 15
...
5 x 10 = 50
```

---

# Sum of Numbers

```javascript
let sum=0;

for(let i=1;i<=10;i++){

sum+=i;

}

console.log(sum);
```

Output

```text
55
```

---

# Factorial Program

```javascript
let fact=1;

for(let i=1;i<=5;i++){

fact*=i;

}

console.log(fact);
```

Output

```text
120
```

---

# Common Beginner Mistakes

 Forgetting braces `{}`

```javascript
if(age>=18)
console.log("Eligible");
```

Although valid for a single statement, always use braces for better readability.

---

 Using `=` instead of `===`

Wrong

```javascript
if(age=18)
```

Correct

```javascript
if(age===18)
```

---

 Infinite Loop

```javascript
let i=1;

while(i<=5){

console.log(i);

}
```

`i` is never incremented, so the loop runs forever.

Correct

```javascript
let i=1;

while(i<=5){

console.log(i);

i++;

}
```

---

 Forgetting `break` in `switch`

Without `break`, execution falls through to the next case.

---

# Memory Tips

### Conditional Statements

```text
if
↓

One Condition

if...else
↓

Two Choices

else if
↓

Many Conditions

switch
↓

Many Values
```

---

### Loops

```text
for

Know Number of Iterations

while

Condition First

do...while

Runs At Least Once
```

---

### Loop Control Statements

```text
break

↓

Stop Loop

continue

↓

Skip Current Iteration
```

---

# Interview Questions

1. What is a conditional statement?
2. What is the difference between `if` and `if...else`?
3. When should you use `else if`?
4. What is a nested `if`?
5. What is a `switch` statement?
6. Why is `break` important in a `switch` statement?
7. Difference between `if` and `switch`?
8. What is a loop?
9. Difference between `for`, `while`, and `do...while`?
10. What is an infinite loop?
11. What is the difference between `break` and `continue`?
12. What is a nested loop?
13. How do you print a multiplication table using a loop?
14. How do you calculate the sum of numbers using a loop?
15. How do you calculate the factorial of a number?

---

# Practice Programs

### Program 1 - Check Positive or Negative

```javascript
let number = -10;

if(number >= 0){
    console.log("Positive");
}
else{
    console.log("Negative");
}
```

---

### Program 2 - Grade Calculator

```javascript
let marks = 88;

if(marks >= 90){
    console.log("A+");
}
else if(marks >= 75){
    console.log("A");
}
else if(marks >= 60){
    console.log("B");
}
else if(marks >= 35){
    console.log("C");
}
else{
    console.log("Fail");
}
```

---

### Program 3 - Day Using Switch

```javascript
let day = 5;

switch(day){
    case 1: console.log("Monday"); break;
    case 2: console.log("Tuesday"); break;
    case 3: console.log("Wednesday"); break;
    case 4: console.log("Thursday"); break;
    case 5: console.log("Friday"); break;
    case 6: console.log("Saturday"); break;
    case 7: console.log("Sunday"); break;
    default: console.log("Invalid Day");
}
```

---

### Program 4 - Print Numbers 1 to 20

```javascript
for(let i = 1; i <= 20; i++){
    console.log(i);
}
```

---

### Program 5 - Print Even Numbers

```javascript
for(let i = 2; i <= 20; i += 2){
    console.log(i);
}
```

---

### Program 6 - Multiplication Table

```javascript
let number = 7;

for(let i = 1; i <= 10; i++){
    console.log(`${number} x ${i} = ${number * i}`);
}
```

---

### Program 7 - Sum of First 100 Numbers

```javascript
let sum = 0;

for(let i = 1; i <= 100; i++){
    sum += i;
}

console.log(sum);
```

---

### Program 8 - Factorial

```javascript
let fact = 1;

for(let i = 1; i <= 6; i++){
    fact *= i;
}

console.log(fact);
```

---

### Program 9 - Break Example

```javascript
for(let i = 1; i <= 10; i++){

    if(i === 7){
        break;
    }

    console.log(i);
}
```

---

### Program 10 - Continue Example

```javascript
for(let i = 1; i <= 10; i++){

    if(i === 5){
        continue;
    }

    console.log(i);
}
```
---

# Functions

---

# What is a Function?

A **Function** is a reusable block of code designed to perform a specific task.

Instead of writing the same code again and again, we can place it inside a function and call it whenever needed.

In simple words,

> A function is like a machine that takes some input, performs a task, and gives an output.

---

# Real World Example

Imagine a **Coffee Machine**.

```text
Coffee Machine
      │
      ▼
Insert Money
      │
      ▼
Select Coffee
      │
      ▼
Machine Prepares Coffee
      │
      ▼
Coffee Ready 
```

Every time you want coffee, you don't build the machine again.

You simply press the button.

Similarly,

A function is written **once** but can be called **many times**.

---

# Why Do We Need Functions?

Without Functions

```javascript
console.log("Welcome to JavaScript");
console.log("Learn Functions");
console.log("Happy Coding");

console.log("Welcome to JavaScript");
console.log("Learn Functions");
console.log("Happy Coding");

console.log("Welcome to JavaScript");
console.log("Learn Functions");
console.log("Happy Coding");
```

Notice that the same code is repeated multiple times.

---

With Functions

```javascript
function welcome(){

    console.log("Welcome to JavaScript");
    console.log("Learn Functions");
    console.log("Happy Coding");

}

welcome();
welcome();
welcome();
```

Output

```text
Welcome to JavaScript
Learn Functions
Happy Coding

Welcome to JavaScript
Learn Functions
Happy Coding

Welcome to JavaScript
Learn Functions
Happy Coding
```

The code becomes shorter, cleaner, and easier to maintain.

---

# Advantages of Functions

Functions provide many benefits.

* Code Reusability
* Easy Maintenance
* Better Readability
* Less Code Duplication
* Easier Debugging
* Modular Programming
* Faster Development

---

# Function Syntax

```javascript
function functionName(){

    // Code

}
```

---

# Understanding the Syntax

```javascript
function greet(){

    console.log("Hello");

}
```

Here,

```text
function
```

Keyword used to create a function.

```text
greet
```

Function Name.

```text
()
```

Parentheses.

Used to receive input (Parameters).

```text
{}
```

Function Body.

Contains the code.

---

# Function Flow

```text
Function Created
        │
        ▼
Stored in Memory
        │
        ▼
Function Called
        │
        ▼
Code Executes
        │
        ▼
Output
```

---

# Creating Your First Function

```javascript
function greet(){

    console.log("Hello Students");

}
```

Nothing happens yet.

Because the function is only created.

---

# Calling a Function

```javascript
function greet(){

    console.log("Hello Students");

}

greet();
```

Output

```text
Hello Students
```

---

# Calling Multiple Times

```javascript
function greet(){

    console.log("Welcome");

}

greet();

greet();

greet();
```

Output

```text
Welcome
Welcome
Welcome
```

---

# Function Naming Rules

Good Names

```javascript
calculateTotal()

printInvoice()

findMaximum()

displayStudent()

showProfile()
```

Bad Names

```javascript
a()

abc()

x1()

test123()
```

Always use meaningful names.

---

# Function Parameters

A **Parameter** is a variable declared inside the function definition.

Parameters receive values from the function call.

---

# Syntax

```javascript
function functionName(parameter){

}
```

---

# Example

```javascript
function greet(name){

    console.log("Hello " + name);

}

greet("Rahul");
```

Output

```text
Hello Rahul
```

---

# Multiple Parameters

```javascript
function student(name, age){

    console.log(name);

    console.log(age);

}

student("Ravi",21);
```

Output

```text
Ravi

21
```

---

# Parameters Flow

```text
Function Call

student("Ravi",21)

        │

        ▼

name = Ravi

age = 21

        │

        ▼

Code Executes
```

---

# Function Arguments

The actual values passed while calling a function are called **Arguments**.

Example

```javascript
function greet(name){

    console.log(name);

}

greet("Apex");
```

Here,

Parameter

```text
name
```

Argument

```text
"Apex"
```

---

# Parameters vs Arguments

| Parameters            | Arguments     |
| --------------------- | ------------- |
| Variables in Function | Actual Values |
| Declared              | Passed        |
| Receive Data          | Send Data     |

---

# Example

```javascript
function add(a,b){

    console.log(a+b);

}

add(20,30);
```

Output

```text
50
```

---

# Default Parameters

Sometimes users don't provide arguments.

We can assign default values.

Syntax

```javascript
function greet(name="Guest"){

}
```

---

Example

```javascript
function greet(name="Guest"){

    console.log("Hello " + name);

}

greet();
```

Output

```text
Hello Guest
```

---

Calling with Value

```javascript
function greet(name="Guest"){

    console.log("Hello " + name);

}

greet("Rahul");
```

Output

```text
Hello Rahul
```

---

# Return Statement

The **return** statement sends a value back to the place where the function was called.

---

# Why Return?

Without Return

```javascript
function add(a,b){

console.log(a+b);

}

let result = add(10,20);

console.log(result);
```

Output

```text
30

undefined
```

Because nothing was returned.

---

Correct Way

```javascript
function add(a,b){

return a+b;

}

let result = add(10,20);

console.log(result);
```

Output

```text
30
```

---

# Return Flow

```text
Call Function

↓

Execute Code

↓

Return Value

↓

Store Result
```

---

# Returning String

```javascript
function fullName(first,last){

return first+" "+last;

}

console.log(fullName("Rahul","Sharma"));
```

Output

```text
Rahul Sharma
```

---

# Returning Boolean

```javascript
function isAdult(age){

return age>=18;

}

console.log(isAdult(20));
```

Output

```text
true
```

---

# Returning Object

```javascript
function student(){

return{

name:"Rahul",

age:20

};

}

console.log(student());
```

Output

```text
{name:"Rahul",age:20}
```

---

# Function Expression

Functions can also be stored inside variables.

Syntax

```javascript
let variable=function(){

};
```

---

Example

```javascript
let greet=function(){

console.log("Hello");

};

greet();
```

Output

```text
Hello
```

---

# Function Declaration vs Function Expression

| Function Declaration         | Function Expression       |
| ---------------------------- | ------------------------- |
| Starts with function keyword | Stored inside variable    |
| Hoisted                      | Not Fully Hoisted         |
| Most Common                  | Used in Modern JavaScript |

---

Declaration

```javascript
function greet(){

console.log("Hello");

}
```

---

Expression

```javascript
let greet=function(){

console.log("Hello");

};
```

---

# Anonymous Function

A function without a name is called an **Anonymous Function**.

Example

```javascript
let message=function(){

console.log("Anonymous Function");

};

message();
```

Output

```text
Anonymous Function
```

---

# Immediately Invoked Function Expression (IIFE)

An IIFE executes immediately after it is defined.

Syntax

```javascript
(function(){

})();
```

---

Example

```javascript
(function(){

console.log("Executed Immediately");

})();
```

Output

```text
Executed Immediately
```

---

# Callback Function

A **Callback Function** is a function passed as an argument to another function.

---

Real World Example

Imagine ordering food online.

```text
Place Order
      │
      ▼
Restaurant Prepares Food
      │
      ▼
Delivery Partner Calls You
```

The call happens **after** the order is ready.

Similarly,

Callbacks execute after another function completes.

---

Example

```javascript
function greet(name){

console.log("Hello "+name);

}

function process(callback){

callback("Rahul");

}

process(greet);
```

Output

```text
Hello Rahul
```

---

# Types of Functions Learned

* Function Declaration
* Function Expression
* Anonymous Function
* Callback Function
* IIFE

---

# Common Beginner Mistakes

  Forgetting Parentheses

Wrong

```javascript
greet;
```

Correct

```javascript
greet();
```

---

  Forgetting return

Wrong

```javascript
function add(a,b){

a+b;

}
```

Correct

```javascript
function add(a,b){

return a+b;

}
```

---

  Passing Wrong Number of Arguments

```javascript
function add(a,b){

return a+b;

}

add(10);
```

Result

```text
NaN
```

Because

```text
b = undefined
```

---

  Confusing Parameters and Arguments

```text
Parameters

↓

Variables

Arguments

↓

Actual Values
```

---

# Memory Tips

### Function

```text
Write Once

↓

Call Many Times
```

---

### Parameter

```text
Receives Data
```

---

### Argument

```text
Sends Data
```

---

### Return

```text
Function

↓

Returns Value

↓

Caller Receives Value
```

---

# Interview Questions

1. What is a function in JavaScript?
2. Why do we use functions?
3. What are the advantages of functions?
4. What is the syntax of a function?
5. What is the difference between parameters and arguments?
6. What is a return statement?
7. What happens if a function does not return anything?
8. What is a function expression?
9. What is an anonymous function?
10. What is an IIFE?
11. What is a callback function?
12. Difference between function declaration and function expression?
13. What are default parameters?
14. Can a function return an object?
15. Can a function return another function? (Advanced concept)

---

# Practice Programs

### Program 1 - Simple Function

```javascript
function welcome(){

    console.log("Welcome to JavaScript");

}

welcome();
```

---

### Program 2 - Addition Function

```javascript
function add(a,b){

    return a+b;

}

console.log(add(15,25));
```

---

### Program 3 - Area of Rectangle

```javascript
function area(length,width){

    return length*width;

}

console.log(area(10,5));
```

---

### Program 4 - Check Even Number

```javascript
function isEven(number){

    return number%2===0;

}

console.log(isEven(18));
```

---

### Program 5 - Greeting Function

```javascript
function greet(name="Guest"){

    console.log("Hello "+name);

}

greet();

greet("Rahul");
```

---

### Program 6 - Function Expression

```javascript
let square=function(number){

    return number*number;

};

console.log(square(8));
```

---

### Program 7 - Anonymous Function

```javascript
let message=function(){

    console.log("Learning JavaScript Functions");

};

message();
```

---

### Program 8 - Callback Function

```javascript
function display(name){

    console.log("Welcome "+name);

}

function process(callback){

    callback("Apex");

}

process(display);
```

---

### Program 9 - Student Details

```javascript
function student(name,age,course){

    console.log("Name :",name);
    console.log("Age :",age);
    console.log("Course :",course);

}

student("Rahul",21,"Java Full Stack");
```

---

### Program 10 - Calculator

```javascript
function calculator(a,b){

    console.log("Addition :",a+b);
    console.log("Subtraction :",a-b);
    console.log("Multiplication :",a*b);
    console.log("Division :",a/b);

}

calculator(20,5);
```

---


---

# Arrow Functions

---

# What is an Arrow Function?

An **Arrow Function** is a shorter and modern way of writing functions in JavaScript.

Arrow Functions were introduced in **ES6 (ECMAScript 2015)**.

They make the code shorter, cleaner, and easier to read.

In simple words,

> An Arrow Function is a simplified version of a traditional function.

---

# Real World Example

Imagine writing an address.

Traditional Way

```text
House No: 101
Street: MG Road
City: Hyderabad
State: Telangana
Country: India
```

Short Way

```text
101, MG Road,
Hyderabad, Telangana
```

Both represent the same address.

Similarly,

Traditional Functions and Arrow Functions perform the same task, but Arrow Functions use less code.

---

# Why Were Arrow Functions Introduced?

Before ES6, JavaScript developers had to write many lines of code even for simple functions.

Example

```javascript
function add(a, b){

    return a + b;

}
```

After ES6

```javascript
const add = (a, b) => a + b;
```

Both produce the same result.

Arrow Functions reduce unnecessary code.

---

# Traditional Function Syntax

```javascript
function functionName(parameters){

    // Code

}
```

Example

```javascript
function greet(){

    console.log("Hello Students");

}
```

---

# Arrow Function Syntax

```javascript
const functionName = (parameters) => {

    // Code

};
```

Example

```javascript
const greet = () => {

    console.log("Hello Students");

};
```

---

# Understanding the Syntax

```javascript
const add = (a, b) => {

    return a + b;

};
```

Explanation

```text
const

↓

Stores Function

add

↓

Function Name

(a, b)

↓

Parameters

=>

↓

Arrow Operator

{}

↓

Function Body
```

---

# First Arrow Function

```javascript
const welcome = () => {

    console.log("Welcome to JavaScript");

};

welcome();
```

Output

```text
Welcome to JavaScript
```

---

# Arrow Function with Parameters

```javascript
const greet = (name) => {

    console.log("Hello " + name);

};

greet("Rahul");
```

Output

```text
Hello Rahul
```

---

# Arrow Function with Multiple Parameters

```javascript
const student = (name, age) => {

    console.log(name);

    console.log(age);

};

student("Ravi", 21);
```

Output

```text
Ravi
21
```

---

# Arrow Function Returning a Value

```javascript
const add = (a, b) => {

    return a + b;

};

console.log(add(10, 20));
```

Output

```text
30
```

---

# Explicit Return

When we use the `return` keyword inside the function body, it is called an **Explicit Return**.

Syntax

```javascript
const functionName = () => {

    return value;

};
```

Example

```javascript
const square = (number) => {

    return number * number;

};

console.log(square(5));
```

Output

```text
25
```

---

# Implicit Return

If the function contains only **one expression**, JavaScript automatically returns the value.

No need to write `return`.

Syntax

```javascript
const functionName = () => expression;
```

Example

```javascript
const square = number => number * number;

console.log(square(6));
```

Output

```text
36
```

---

# Explicit vs Implicit Return

| Explicit Return        | Implicit Return       |
| ---------------------- | --------------------- |
| Uses `return`          | No `return`           |
| Uses `{}`              | No `{}` required      |
| Multiple Statements    | Single Expression     |
| Easy for Complex Logic | Best for Simple Logic |

---

Example

Explicit

```javascript
const multiply = (a, b) => {

    return a * b;

};

console.log(multiply(5, 4));
```

Output

```text
20
```

---

Implicit

```javascript
const multiply = (a, b) => a * b;

console.log(multiply(5, 4));
```

Output

```text
20
```

---

# Arrow Function with No Parameters

```javascript
const message = () => {

    console.log("Learning Arrow Functions");

};

message();
```

Output

```text
Learning Arrow Functions
```

---

# Arrow Function with One Parameter

If there is only **one parameter**, parentheses are optional.

Both are correct.

```javascript
const greet = (name) => {

    console.log(name);

};
```

or

```javascript
const greet = name => {

    console.log(name);

};
```

Example

```javascript
const cube = number => number * number * number;

console.log(cube(3));
```

Output

```text
27
```

---

# Arrow Function with Multiple Parameters

If there are two or more parameters, parentheses are required.

```javascript
const add = (a, b) => a + b;

console.log(add(20, 15));
```

Output

```text
35
```

---

# Returning an Object

When returning an object using an implicit return, wrap it inside parentheses.

Wrong

```javascript
const student = () => {
    name: "Rahul"
};
```

Correct

```javascript
const student = () => ({
    name: "Rahul",
    age: 20
});

console.log(student());
```

Output

```text
{ name: 'Rahul', age: 20 }
```

---

# Traditional Function vs Arrow Function

| Traditional Function    | Arrow Function                       |
| ----------------------- | ------------------------------------ |
| Uses `function` keyword | Uses `=>`                            |
| Longer Syntax           | Shorter Syntax                       |
| Has its own `this`      | Does not have its own `this`         |
| Best for Object Methods | Best for Callbacks & Short Functions |
| Available before ES6    | Introduced in ES6                    |

---

Example

Traditional

```javascript
function add(a, b){

    return a + b;

}
```

Arrow

```javascript
const add = (a, b) => a + b;
```

---

# Arrow Functions and `this`

One of the biggest differences is how `this` behaves.

Traditional Function

```javascript
const person = {

    name: "Rahul",

    greet: function(){

        console.log(this.name);

    }

};

person.greet();
```

Output

```text
Rahul
```

Arrow Function

```javascript
const person = {

    name: "Rahul",

    greet: () => {

        console.log(this.name);

    }

};

person.greet();
```

Output

```text
undefined
```

### Why?

Arrow Functions **do not create their own `this`**.

They inherit `this` from the surrounding scope.

**Note:** We'll study `this` in detail later.

---

# Where Should We Use Arrow Functions?

Arrow Functions are commonly used in:

* Callback Functions
* Array Methods
* Event Handlers (with care)
* Simple Utility Functions
* Promise Functions
* API Calls

---

# Real World Example

Suppose you want to calculate the GST amount.

Traditional Function

```javascript
function calculateGST(amount){

    return amount * 0.18;

}

console.log(calculateGST(1000));
```

Output

```text
180
```

Arrow Function

```javascript
const calculateGST = amount => amount * 0.18;

console.log(calculateGST(1000));
```

Output

```text
180
```

---

# Nested Arrow Function

```javascript
const outer = () => {

    const inner = () => {

        console.log("Inner Function");

    };

    inner();

};

outer();
```

Output

```text
Inner Function
```

---

# Callback Using Arrow Function

Traditional Callback

```javascript
function process(callback){

    callback();

}

process(function(){

    console.log("Processing...");

});
```

Output

```text
Processing...
```

---

Arrow Callback

```javascript
function process(callback){

    callback();

}

process(() => {

    console.log("Processing...");

});
```

Output

```text
Processing...
```

---

# Common Beginner Mistakes

  Forgetting Parentheses for Multiple Parameters

Wrong

```javascript
const add = a, b => a + b;
```

Correct

```javascript
const add = (a, b) => a + b;
```

---

  Forgetting `return` with Braces

Wrong

```javascript
const square = number => {

    number * number;

};
```

Output

```text
undefined
```

Correct

```javascript
const square = number => {

    return number * number;

};
```

---

  Returning Object Incorrectly

Wrong

```javascript
const student = () => {

    name: "Rahul";

};
```

Correct

```javascript
const student = () => ({

    name: "Rahul"

});
```

---

  Using Arrow Functions for Object Methods

Avoid

```javascript
const person = {

    name: "Rahul",

    greet: () => {

        console.log(this.name);

    }

};
```

Prefer

```javascript
const person = {

    name: "Rahul",

    greet(){

        console.log(this.name);

    }

};
```

---

# Memory Tips

### Arrow Function

```text
Traditional Function

↓

Long Syntax

Arrow Function

↓

Short Syntax
```

---

### Parameters

```text
0 Parameters

↓

()

1 Parameter

↓

parameter

2+ Parameters

↓

(parameter1, parameter2)
```

---

### Return

```text
{}

↓

Need return

No {}

↓

Automatic Return
```

---

### `this`

```text
Traditional Function

↓

Own this

Arrow Function

↓

Uses Parent this
```

---

# Interview Questions

1. What is an Arrow Function?
2. When were Arrow Functions introduced?
3. What are the advantages of Arrow Functions?
4. What is the syntax of an Arrow Function?
5. What is the difference between a Traditional Function and an Arrow Function?
6. What is an Implicit Return?
7. What is an Explicit Return?
8. Can Arrow Functions have multiple parameters?
9. How do you return an object from an Arrow Function?
10. Does an Arrow Function have its own `this`?
11. Why are Arrow Functions popular in callbacks?
12. When should you avoid using Arrow Functions?
13. Can Arrow Functions be anonymous?
14. What is the difference between `() => {}` and `() => expression`?
15. Are Arrow Functions hoisted like function declarations?

---

# Practice Programs

### Program 1 - Simple Arrow Function

```javascript
const welcome = () => {

    console.log("Welcome to JavaScript");

};

welcome();
```

---

### Program 2 - Addition

```javascript
const add = (a, b) => a + b;

console.log(add(25, 15));
```

---

### Program 3 - Square

```javascript
const square = number => number * number;

console.log(square(8));
```

---

### Program 4 - Greeting

```javascript
const greet = name => {

    console.log("Hello " + name);

};

greet("Apex");
```

---

### Program 5 - Area of Circle

```javascript
const area = radius => 3.14 * radius * radius;

console.log(area(5));
```

---

### Program 6 - Even or Odd

```javascript
const isEven = number => number % 2 === 0;

console.log(isEven(18));
console.log(isEven(15));
```

---

### Program 7 - Maximum Number

```javascript
const maximum = (a, b) => a > b ? a : b;

console.log(maximum(45, 60));
```

---

### Program 8 - Returning Object

```javascript
const employee = () => ({

    id: 101,

    name: "Rahul",

    department: "IT"

});

console.log(employee());
```

---

### Program 9 - Callback Function

```javascript
function execute(callback){

    callback();

}

execute(() => {

    console.log("Callback Executed");

});
```

---

### Program 10 - Calculator

```javascript
const calculator = (a, b) => {

    console.log("Addition :", a + b);
    console.log("Subtraction :", a - b);
    console.log("Multiplication :", a * b);
    console.log("Division :", a / b);

};

calculator(20, 5);
```

---




---
# Scope in JavaScript

---

# What is Scope?

**Scope** is the area or region of a program where a variable can be accessed.

In simple words,

> Scope determines **where a variable is available** and **where it cannot be used**.

If a variable is created inside one scope, it may not be accessible outside that scope.

Understanding scope is one of the most important concepts in JavaScript because it helps us avoid errors and write secure, organized code.

---

# Real World Example

Imagine a school.

```text
School
│
├── Principal Room
│
├── Staff Room
│
├── Classroom 1
│
└── Classroom 2
```

A student from Classroom 1 cannot enter the Principal's room without permission.

Similarly,

Variables belong to certain areas of a program.

Some variables are available everywhere.

Some variables are available only inside a specific block.

---

# Why Do We Need Scope?

Suppose every variable in a program was accessible from anywhere.

Problems:

* Variables may accidentally change.
* Different developers may use the same variable names.
* Bugs become difficult to find.
* Large projects become difficult to maintain.

Scope solves these problems by limiting where variables can be used.

---

# Types of Scope

JavaScript mainly has four types of scope.

* Global Scope
* Local Scope
* Function Scope
* Block Scope

Later, we'll learn:

* Lexical Scope
* Scope Chain
* Closures

---

# Global Scope

---

## What is Global Scope?

A variable declared **outside every function and block** belongs to the **Global Scope**.

Global variables can be accessed from anywhere in the program.

---

## Syntax

```javascript
let variableName = value;
```

Declared outside all functions.

---

## Example

```javascript
let company = "ApexSwaram";

console.log(company);
```

Output

```text
ApexSwaram
```

---

## Accessing Global Variable Inside Function

```javascript
let company = "ApexSwaram";

function display(){

    console.log(company);

}

display();
```

Output

```text
ApexSwaram
```

Why?

Because global variables are accessible everywhere.

---

## Example

```javascript
let course = "JavaScript";

function student1(){

    console.log(course);

}

function student2(){

    console.log(course);

}

student1();

student2();
```

Output

```text
JavaScript

JavaScript
```

Both functions can access the same variable.

---

# Global Scope Diagram

```text
Global Scope

course

company

price

age

↓

Accessible Everywhere
```

---

# Advantages of Global Variables

* Can be accessed from any function.
* Easy to share data.
* Useful for constants.
* Good for application-wide settings.

---

# Disadvantages of Global Variables

* Any function can change them.
* Difficult to debug.
* Memory remains occupied throughout the program.
* May create naming conflicts.

---

# Example of Problem

```javascript
let total = 100;

function increase(){

    total = total + 50;

}

function decrease(){

    total = total - 20;

}

increase();

decrease();

console.log(total);
```

Output

```text
130
```

Since everyone can modify the same variable, unexpected changes may occur.

---

# Local Scope

---

## What is Local Scope?

Variables declared **inside a function** or **inside a block** are called Local Variables.

They are available only within that particular area.

---

## Example

```javascript
function student(){

    let name = "Rahul";

    console.log(name);

}

student();
```

Output

```text
Rahul
```

---

Trying to Access Outside

```javascript
function student(){

    let name = "Rahul";

}

console.log(name);
```

Output

```text
ReferenceError
```

Because

```text
name
```

exists only inside the function.

---

# Local Scope Diagram

```text
Function

↓

name

age

marks

↓

Available Only Here
```

---

# Global vs Local

```javascript
let city = "Hyderabad";

function display(){

    let name = "Rahul";

    console.log(name);

    console.log(city);

}

display();

console.log(city);
```

Output

```text
Rahul

Hyderabad

Hyderabad
```

Notice

Global variable

```text
city
```

works everywhere.

Local variable

```text
name
```

works only inside the function.

---

# Function Scope

---

## What is Function Scope?

Variables declared using

```text
var

let

const
```

inside a function belong only to that function.

---

## Example

```javascript
function addition(){

    let a = 20;

    let b = 30;

    console.log(a + b);

}

addition();
```

Output

```text
50
```

---

Trying Outside

```javascript
function addition(){

    let a = 20;

}

console.log(a);
```

Output

```text
ReferenceError
```

---

# Another Example

```javascript
function employee(){

    let salary = 50000;

    console.log(salary);

}

employee();
```

Output

```text
50000
```

---

# Memory Representation

```text
Global Memory

↓

employee()

↓

salary

↓

Destroyed After Function Ends
```

Local variables are removed from memory after the function finishes execution.

---

# Block Scope

---

## What is Block Scope?

A block is any code written inside

```text
{

}
```

Variables declared using

```text
let

const
```

are available only inside that block.

---

## Example

```javascript
{

let message = "Hello";

console.log(message);

}
```

Output

```text
Hello
```

---

Outside

```javascript
{

let message = "Hello";

}

console.log(message);
```

Output

```text
ReferenceError
```

---

# Example with if

```javascript
if(true){

let marks = 90;

console.log(marks);

}
```

Output

```text
90
```

Outside

```javascript
if(true){

let marks = 90;

}

console.log(marks);
```

Output

```text
ReferenceError
```

---

# Example with for Loop

```javascript
for(let i=1;i<=3;i++){

console.log(i);

}
```

Output

```text
1

2

3
```

Outside

```javascript
for(let i=1;i<=3;i++){

}

console.log(i);
```

Output

```text
ReferenceError
```

---

# Block Scope Diagram

```text
{

let a

const b

}

↓

Available Only Here
```

---

# Important Difference

```javascript
{

var x = 10;

}

console.log(x);
```

Output

```text
10
```

Because

```text
var
```

does **NOT** follow block scope.

---

Using let

```javascript
{

let x = 10;

}

console.log(x);
```

Output

```text
ReferenceError
```

---

Using const

```javascript
{

const x = 10;

}

console.log(x);
```

Output

```text
ReferenceError
```

---

# Function Scope vs Block Scope

| Function Scope               | Block Scope                          |
| ---------------------------- | ------------------------------------ |
| Exists inside function       | Exists inside `{}`                   |
| `var` follows function scope | `let` and `const` follow block scope |
| Ends when function ends      | Ends when block ends                 |

---

# Scope Hierarchy

```text
Global Scope

↓

Function Scope

↓

Block Scope
```

Inner scopes can access outer scopes.

Outer scopes cannot access inner scopes.

---

# Scope Flow

```text
Global Variable

↓

Accessible Inside Function

↓

Accessible Inside Block
```

But

```text
Block Variable

↓

Cannot Access Outside Block
```

---

# Real World Example

Imagine a company.

```text
Company

↓

Department

↓

Employee
```

Company Rules

Accessible to everyone.

Department Rules

Accessible only to that department.

Employee Personal File

Accessible only to that employee.

Similarly,

Global Variables

↓

Available everywhere.

Local Variables

↓

Available only in their own area.

---

# Best Practices

  Prefer

```javascript
let
```

for changing values.

---

  Prefer

```javascript
const
```

for fixed values.

---

  Avoid

```javascript
var
```

in modern JavaScript unless necessary.

---

Keep variables inside the smallest possible scope.

This makes programs safer and easier to maintain.

---

# Common Beginner Mistakes

### Mistake 1

Trying to access local variables outside.

Wrong

```javascript
function test(){

let age = 20;

}

console.log(age);
```

---

### Mistake 2

Using too many global variables.

```javascript
let a=10;

let b=20;

let c=30;

let d=40;
```

Avoid unnecessary globals.

---

### Mistake 3

Thinking

```text
var
```

is block scoped.

Wrong

```javascript
if(true){

var x=100;

}

console.log(x);
```

Output

```text
100
```

---

### Mistake 4

Using the same variable name everywhere.

Instead

```javascript
let studentName;
```

Use meaningful names.

---

# Memory Tips

## Global Scope

```text
Outside Everything

↓

Accessible Everywhere
```

---

## Function Scope

```text
Inside Function

↓

Only Inside Function
```

---

## Block Scope

```text
Inside {}

↓

Only Inside Block
```

---

## Remember

```text
var

↓

Function Scope

let

↓

Block Scope

const

↓

Block Scope
```

---

# Interview Questions

1. What is Scope?
2. Why is Scope important?
3. What is Global Scope?
4. What is Local Scope?
5. What is Function Scope?
6. What is Block Scope?
7. Difference between Global and Local Variables?
8. Why is `let` block scoped?
9. Why is `var` not block scoped?
10. Which is better: `var`, `let`, or `const`?
11. Can a function access a global variable?
12. Can global code access a local variable?
13. What happens to local variables after a function finishes?
14. Why should we avoid too many global variables?
15. What is the difference between Function Scope and Block Scope?

---

# Practice Programs

## Program 1 - Global Variable

```javascript
let company = "ApexSwaram";

function showCompany(){

    console.log(company);

}

showCompany();

console.log(company);
```

---

## Program 2 - Local Variable

```javascript
function student(){

    let name = "Rahul";

    console.log(name);

}

student();
```

---

## Program 3 - Function Scope

```javascript
function add(){

    let a = 10;

    let b = 20;

    console.log(a + b);

}

add();
```

---

## Program 4 - Block Scope

```javascript
if(true){

    let marks = 95;

    console.log(marks);

}
```

---

## Program 5 - var Example

```javascript
if(true){

    var x = 100;

}

console.log(x);
```

---

## Program 6 - let Example

```javascript
if(true){

    let x = 100;

    console.log(x);

}
```

---

## Program 7 - const Example

```javascript
{

    const PI = 3.14;

    console.log(PI);

}
```

---

## Program 8 - Global and Local Together

```javascript
let college = "ABC College";

function details(){

    let student = "Rahul";

    console.log(student);

    console.log(college);

}

details();

console.log(college);
```

---

## Program 9 - Multiple Functions

```javascript
let language = "JavaScript";

function first(){

    console.log(language);

}

function second(){

    console.log(language);

}

first();

second();
```

---

## Program 10 - Block Inside Function

```javascript
function demo(){

    let name = "Apex";

    if(true){

        let course = "JavaScript";

        console.log(name);

        console.log(course);

    }

}

demo();
```

---


# Arrays

---

# What is an Array?

An **Array** is a special data structure in JavaScript that is used to store **multiple values in a single variable**.

Instead of creating many variables to store similar data, we can store all the values inside one array.

In simple words,

> **An Array is a collection of multiple values stored under a single variable name.**

---

# Real World Example

Imagine a classroom.

Without an Array

```javascript
let student1 = "Rahul";
let student2 = "Ravi";
let student3 = "Kiran";
let student4 = "Akhil";
```

Creating separate variables for every student becomes difficult.

Using an Array

```javascript
let students = ["Rahul", "Ravi", "Kiran", "Akhil"];
```

Now all student names are stored inside one variable.

---

# Why Do We Need Arrays?

Without Arrays

```javascript
let mark1 = 90;
let mark2 = 85;
let mark3 = 76;
let mark4 = 95;
```

With Arrays

```javascript
let marks = [90, 85, 76, 95];
```

Arrays make programs

* Easier to write
* Easier to maintain
* Easy to search
* Easy to update
* Easy to loop through data

---

# Characteristics of Arrays

* Stores multiple values.
* Can store different data types.
* Starts with index **0**.
* Dynamic in size.
* Ordered collection.

Example

```javascript
let data = [
    "Rahul",
    22,
    true,
    85.5
];
```

---

# Array Syntax

```javascript
let arrayName = [value1, value2, value3];
```

Example

```javascript
let colors = ["Red", "Green", "Blue"];
```

---

# Creating Arrays

## Method 1 (Recommended)

```javascript
let fruits = ["Apple", "Banana", "Mango"];
```

---

## Method 2

```javascript
let numbers = new Array(10, 20, 30);
```

Both create arrays.

---

# Array Structure

```text
Index      0        1        2

Value   Apple    Banana    Mango
```

---

# Accessing Elements

Syntax

```javascript
arrayName[index];
```

Example

```javascript
let fruits = ["Apple", "Banana", "Mango"];

console.log(fruits[0]);
console.log(fruits[1]);
console.log(fruits[2]);
```

Output

```text
Apple
Banana
Mango
```

---

# Why Index Starts from 0?

JavaScript stores the first element at position **0**.

```text
Index

0  1  2  3

↓

First Element = 0
```

---

# Updating Array Elements

```javascript
let fruits = ["Apple", "Banana", "Mango"];

fruits[1] = "Orange";

console.log(fruits);
```

Output

```text
["Apple","Orange","Mango"]
```

---

# Array Length

The `length` property returns the total number of elements.

```javascript
let fruits = ["Apple", "Banana", "Mango"];

console.log(fruits.length);
```

Output

```text
3
```

---

# Traversing an Array

Traversing means visiting every element one by one.

---

## Using for Loop

```javascript
let fruits = ["Apple", "Banana", "Mango"];

for(let i = 0; i < fruits.length; i++){

    console.log(fruits[i]);

}
```

Output

```text
Apple
Banana
Mango
```

---

## Using for...of Loop

```javascript
let fruits = ["Apple", "Banana", "Mango"];

for(let fruit of fruits){

    console.log(fruit);

}
```

Output

```text
Apple
Banana
Mango
```

---

# Array Methods

---

# push()

Adds an element at the **end**.

Syntax

```javascript
array.push(value);
```

Example

```javascript
let colors = ["Red", "Blue"];

colors.push("Green");

console.log(colors);
```

Output

```text
["Red","Blue","Green"]
```

---

# pop()

Removes the **last** element.

```javascript
let colors = ["Red", "Blue", "Green"];

colors.pop();

console.log(colors);
```

Output

```text
["Red","Blue"]
```

---

# shift()

Removes the **first** element.

```javascript
let colors = ["Red", "Blue", "Green"];

colors.shift();

console.log(colors);
```

Output

```text
["Blue","Green"]
```

---

# unshift()

Adds an element at the **beginning**.

```javascript
let colors = ["Blue", "Green"];

colors.unshift("Red");

console.log(colors);
```

Output

```text
["Red","Blue","Green"]
```

---

# includes()

Checks whether an element exists.

```javascript
let fruits = ["Apple", "Banana", "Mango"];

console.log(fruits.includes("Banana"));
```

Output

```text
true
```

---

# indexOf()

Returns the index of an element.

```javascript
let fruits = ["Apple", "Banana", "Mango"];

console.log(fruits.indexOf("Mango"));
```

Output

```text
2
```

If not found

```text
-1
```

---

# slice()

Returns a portion of an array.

Original array remains unchanged.

```javascript
let numbers = [10,20,30,40,50];

console.log(numbers.slice(1,4));
```

Output

```text
[20,30,40]
```

---

# splice()

Adds or removes elements.

```javascript
let numbers = [10,20,30,40];

numbers.splice(2,1);

console.log(numbers);
```

Output

```text
[10,20,40]
```

---

# concat()

Joins two arrays.

```javascript
let a = [1,2];

let b = [3,4];

console.log(a.concat(b));
```

Output

```text
[1,2,3,4]
```

---

# join()

Converts an array into a string.

```javascript
let fruits = ["Apple","Banana","Mango"];

console.log(fruits.join("-"));
```

Output

```text
Apple-Banana-Mango
```

---

# Real World Example

Store student marks.

```javascript
let marks = [95,88,76,90,85];

console.log(marks);
```

Store employee names.

```javascript
let employees = [

"Rahul",

"Ravi",

"Kiran",

"Akhil"

];

console.log(employees);
```

---

# Common Beginner Mistakes

### Mistake 1

Using an invalid index.

```javascript
let fruits = ["Apple"];

console.log(fruits[5]);
```

Output

```text
undefined
```

---

### Mistake 2

Using parentheses instead of brackets.

Wrong

```javascript
let numbers = (10,20,30);
```

Correct

```javascript
let numbers = [10,20,30];
```

---

### Mistake 3

Forgetting the array length in loops.

Wrong

```javascript
for(let i=0;i<=fruits.length;i++)
```

Correct

```javascript
for(let i=0;i<fruits.length;i++)
```

---

# Memory Tips

```text
push()

↓

Add Last

pop()

↓

Remove Last

shift()

↓

Remove First

unshift()

↓

Add First
```

---

# Interview Questions

1. What is an Array?
2. Why do we use Arrays?
3. Why does array indexing start from 0?
4. How do you access array elements?
5. Difference between `push()` and `pop()`?
6. Difference between `shift()` and `unshift()`?
7. Difference between `slice()` and `splice()`?
8. What does `includes()` do?
9. What does `indexOf()` return if an element is not found?
10. What is the purpose of the `length` property?

---

# Practice Programs

### Program 1 - Print Array

```javascript
let fruits = ["Apple","Banana","Mango"];

console.log(fruits);
```

---

### Program 2 - Print Each Element

```javascript
let numbers = [10,20,30,40];

for(let i=0;i<numbers.length;i++){

    console.log(numbers[i]);

}
```

---

### Program 3 - Add an Element

```javascript
let colors = ["Red","Blue"];

colors.push("Green");

console.log(colors);
```

---

### Program 4 - Remove Last Element

```javascript
let colors = ["Red","Blue","Green"];

colors.pop();

console.log(colors);
```

---

### Program 5 - Find an Element

```javascript
let students = ["Rahul","Ravi","Kiran"];

console.log(students.includes("Ravi"));
```

---

### Program 6 - Merge Arrays

```javascript
let first = [1,2,3];

let second = [4,5,6];

console.log(first.concat(second));
```

---

### Program 7 - Convert Array to String

```javascript
let cities = ["Hyderabad","Delhi","Mumbai"];

console.log(cities.join(", "));
```

---

### Program 8 - Update an Element

```javascript
let fruits = ["Apple","Banana","Mango"];

fruits[1] = "Orange";

console.log(fruits);
```

---
Excellent. We'll build this like a professional textbook.

# JavaScript DOM 

## Introduction to JavaScript DOM

# 1. Introduction to JavaScript

## What is JavaScript?

JavaScript is a **high-level, lightweight, interpreted programming language** used to make web pages interactive and dynamic.

HTML is responsible for creating the structure of a webpage.

CSS is responsible for designing the webpage.

JavaScript is responsible for adding intelligence and interactivity to the webpage.

Without JavaScript, webpages are static. JavaScript allows users to interact with webpages by clicking buttons, submitting forms, changing images, validating user input, displaying animations, communicating with servers, and much more.

---

## Role of HTML, CSS and JavaScript

| Technology | Purpose                              |
| ---------- | ------------------------------------ |
| HTML       | Creates the structure of the webpage |
| CSS        | Styles and designs the webpage       |
| JavaScript | Adds functionality and interactivity |

### Example

Think of a human body.

* HTML → Skeleton
* CSS → Clothes and Appearance
* JavaScript → Brain and Muscles

Without JavaScript, a webpage cannot respond to user actions.

---

## Example

```html
<!DOCTYPE html>
<html>
<body>

<h1>Welcome Students</h1>

<button>Click Me</button>

</body>
</html>
```

Nothing happens when the button is clicked.

Now add JavaScript.

```html
<!DOCTYPE html>
<html>
<body>

<h1 id="title">Welcome Students</h1>

<button onclick="changeText()">Click Me</button>

<script>

function changeText(){

document.getElementById("title").innerHTML="Welcome Java Full Stack Students";

}

</script>

</body>
</html>
```

Now clicking the button changes the heading.

This is the power of JavaScript.

---

# 2. What is DOM?

## Definition

DOM stands for

> **Document Object Model**

DOM is a programming interface provided by the browser that represents an HTML document as a collection of objects.

It allows JavaScript to access, modify, create, update, and delete HTML elements dynamically.

In simple words,

DOM acts as a bridge between HTML and JavaScript.

Without DOM, JavaScript cannot access HTML elements.

---

## Full Form

```
D → Document

O → Object

M → Model
```

---

## Meaning of Each Word

### Document

The webpage itself is called a document.

Example

```html
index.html
```

The entire HTML page is considered one document.

---

### Object

Every HTML element becomes an object.

Example

```html
<h1>Hello</h1>

<p>Welcome</p>

<button>Click</button>
```

Each of these elements becomes an object.

JavaScript can control these objects.

---

### Model

Model means the browser arranges all HTML elements in a tree-like structure.

This structure is called the DOM Tree.

---

# 3. Why DOM is Required?

Imagine a webpage without DOM.

```html
<h1>Hello Students</h1>

<button>Click</button>
```

Suppose you want

* Change the heading
* Hide the heading
* Change color
* Change font size
* Add another heading

Can HTML do this?

No.

Can CSS do this?

No.

Only JavaScript can perform these operations.

But JavaScript needs a way to find the HTML elements.

DOM provides that way.

---

## Why do we use DOM?

DOM allows JavaScript to

* Read HTML
* Change HTML
* Change CSS
* Add new elements
* Remove elements
* Replace elements
* Read form values
* Validate forms
* Handle mouse events
* Handle keyboard events
* Create animations

Without DOM, JavaScript cannot manipulate a webpage.

---

# 4. How Browser Works?

Whenever a user opens a webpage,

the browser performs the following steps.

```
User Opens Website

↓

Browser Reads HTML File

↓

Browser Parses HTML

↓

Browser Creates DOM Tree

↓

Browser Displays Webpage

↓

JavaScript Accesses DOM

↓

User Interacts With Page
```

---

## Example

Suppose this HTML is loaded.

```html
<body>

<h1>Java</h1>

<p>Welcome</p>

<button>Click</button>

</body>
```

The browser converts it into objects.

---

# 5. How Browser Creates DOM?

Suppose we have

```html
<html>

<body>

<h1>Hello</h1>

<p>Welcome</p>

<button>Click</button>

</body>

</html>
```

The browser converts this into

```
Document
    │
   HTML
    │
   BODY
 ┌──┼──────────┐
 │  │          │
H1  P      BUTTON
```

Each box is called a **Node**.

Every HTML element becomes one node.

---

## Types of Nodes

* Document Node
* Element Node
* Text Node
* Attribute Node
* Comment Node

Example

```html
<h1>Hello</h1>
```

```
Element Node

↓

H1

↓

Text Node

↓

Hello
```

---

# 6. DOM Tree Structure

DOM is organized in the form of a tree.

```
Document
│
HTML
│
├── HEAD
│      ├── TITLE
│      └── META
│
└── BODY
       ├── H1
       ├── P
       ├── IMG
       ├── INPUT
       └── BUTTON
```

Because of this structure,

JavaScript can easily move between parent, child, and sibling elements.

---

## Parent Node

```html
<body>

<h1>Hello</h1>

</body>
```

BODY is the parent.

H1 is the child.

---

## Child Node

```html
<div>

<p>Hello</p>

</div>
```

P is the child of DIV.

---

## Sibling Nodes

```html
<h1>Java</h1>

<p>Python</p>

<button>Click</button>
```

All three are siblings because they share the same parent.

---

# 7. Window Object

Whenever a webpage loads,

the browser automatically creates a **Window Object**.

It is the top-most object in JavaScript.

Everything belongs to the Window object.

```
Window

↓

Document

↓

HTML Elements
```

---

## Examples

```javascript
alert("Hello");
```

Actually,

```javascript
window.alert("Hello");
```

---

```javascript
console.log("Java");
```

Actually,

```javascript
window.console.log("Java");
```

---

```javascript
setTimeout(fun,1000);
```

Actually,

```javascript
window.setTimeout(fun,1000);
```

The `window` keyword is optional because JavaScript assumes it automatically.

---

# 8. Document Object

Inside the Window object is the **Document Object**.

The document object represents the complete HTML page.

Whenever we write

```javascript
document.getElementById("heading");
```

JavaScript first enters the document object.

Then it searches for the HTML element.

Without the document object, JavaScript cannot access HTML elements.

---

## Example

```javascript
document.getElementById("title");
```

Meaning

```
Document

↓

Find the element

↓

ID = title

↓

Return the element
```

---

# Window Object vs Document Object

| Window Object                    | Document Object              |
| -------------------------------- | ---------------------------- |
| Top-level browser object         | Represents the HTML document |
| Created automatically            | Created inside Window        |
| Contains Browser APIs            | Contains HTML Elements       |
| Used for alerts, timers, history | Used for DOM manipulation    |

Relationship

```
Window

↓

Document

↓

HTML

↓

BODY

↓

Elements
```

---

# 9. HTML Document vs DOM

| HTML Document        | DOM                      |
| -------------------- | ------------------------ |
| Written by Developer | Created by Browser       |
| Static               | Dynamic                  |
| Contains Tags        | Contains Objects         |
| Cannot change itself | JavaScript can modify it |

---

# 10. Advantages of DOM

* Makes webpages interactive.
* Changes content without reloading the page.
* Dynamically updates HTML and CSS.
* Creates responsive user interfaces.
* Simplifies form validation.
* Supports animations and dynamic effects.
* Enables event handling.
* Allows creation and deletion of HTML elements at runtime.

---

# 11. Real World Applications of DOM

DOM is used in almost every modern website.

Examples include:

* Login Forms
* Registration Forms
* Shopping Carts
* Online Banking
* Facebook Likes
* Instagram Comments
* YouTube Video Controls
* Amazon Product Filters
* Flipkart Search
* Gmail Compose Window
* Live Notifications
* Dark Mode
* Online Exams
* Image Sliders
* To-Do Lists
* Weather Applications

Whenever you see a webpage changing without refreshing, JavaScript is using the DOM.

---

# 12. Summary

* JavaScript makes webpages interactive.
* DOM stands for Document Object Model.
* The browser converts HTML into a DOM Tree.
* Every HTML element becomes an object.
* JavaScript uses the Document object to access HTML elements.
* The Window object is the top-level browser object.
* DOM allows reading, modifying, creating, and deleting HTML elements dynamically.

---

# Interview Questions

1. What is DOM?
2. What is the full form of DOM?
3. Why is DOM required?
4. What is the difference between HTML and DOM?
5. What is a DOM Tree?
6. What is a Node?
7. What is the Window Object?
8. What is the Document Object?
9. Which object is the parent: Window or Document?
10. Can JavaScript manipulate HTML without the DOM? Why or why not?

---

# Assignment

### Assignment 1

Draw the DOM Tree for the following HTML:

```html
<html>
<body>
<h1>Welcome</h1>
<p>JavaScript</p>
<button>Click Me</button>
</body>
</html>
```

### Assignment 2

Explain the difference between the **Window Object** and the **Document Object** with examples.

### Assignment 3

Write five real-world applications where the DOM is used.

---


# getElementById()

## Definition

The `getElementById()` method is used to select an HTML element using its **id** attribute.

Since an **id** must be unique in an HTML document, this method always returns **only one element**.

It is one of the most commonly used DOM methods because it allows JavaScript to directly access and manipulate a specific HTML element.

---

## Why do we use getElementById()?

Suppose we have a heading on a webpage.

```html
<h1 id="title">Welcome Students</h1>
```

When a user clicks a button, we want to change the heading to another text.

JavaScript first finds the element using its ID and then performs the required action.

---

## Syntax

```javascript
document.getElementById("idName");
```

### Parameter

| Parameter | Description |
|-----------|-------------|
| idName | The ID of the HTML element |

### Return Value

Returns the HTML element with the specified ID.

If no matching element is found, it returns **null**.

---

## Complete Example 1 - Change Text

```html
<!DOCTYPE html>
<html>
<head>
    <title>getElementById()</title>
</head>
<body>

<h1 id="title">Welcome Students</h1>

<button onclick="changeText()">Change Text</button>

<script>

function changeText(){

    document.getElementById("title").innerHTML =
    "Welcome Java Full Stack Students";

}

</script>

</body>
</html>
```

### Output

Before clicking the button

```
Welcome Students
```

After clicking the button

```
Welcome Java Full Stack Students
```

---

## Complete Example 2 - Change Color

```html
<!DOCTYPE html>
<html>
<head>
    <title>Change Color</title>
</head>
<body>

<h1 id="heading">JavaScript DOM</h1>

<button onclick="changeColor()">Change Color</button>

<script>

function changeColor(){

    document.getElementById("heading").style.color="red";

}

</script>

</body>
</html>
```

---

## Complete Example 3 - Hide Element

```html
<!DOCTYPE html>
<html>
<head>
    <title>Hide Element</title>
</head>
<body>

<h1 id="text">Hello Students</h1>

<button onclick="hideText()">Hide</button>

<script>

function hideText(){

    document.getElementById("text").style.display="none";

}

</script>

</body>
</html>
```

---

## Complete Example 4 - Change Image

```html
<!DOCTYPE html>
<html>
<head>
<title>Change Image</title>
</head>
<body>

<img id="photo"
src="https://via.placeholder.com/200">

<br><br>

<button onclick="changeImage()">Change Image</button>

<script>

function changeImage(){

document.getElementById("photo").src="https://picsum.photos/200";

}

</script>

</body>
</html>
```

---

## How getElementById() Works

```
document

↓

Search HTML Document

↓

Find Matching ID

↓

Return HTML Element

↓

JavaScript Manipulates It
```

---

## Important Points

- ID must be unique.
- Returns only one element.
- Faster than most selector methods.
- Returns `null` if the ID is not found.
- IDs are case-sensitive.

---

## Common Mistakes

### Wrong ID

```javascript
document.getElementById("Heading");
```

```html
<h1 id="heading">
```

These are different because IDs are case-sensitive.

---

### Duplicate IDs

 Wrong

```html
<h1 id="title">Java</h1>

<h1 id="title">Python</h1>
```

 Correct

```html
<h1 id="java">Java</h1>

<h1 id="python">Python</h1>
```

---

## Interview Questions

1. What is `getElementById()`?
2. Why should an ID be unique?
3. What happens if the ID is not found?
4. Does `getElementById()` return one element or multiple elements?
5. Is `getElementById()` case-sensitive?

---

## Assignment

Create a webpage where clicking a button changes the heading color, font size, and text using `getElementById()`.

---

# getElementsByClassName()

## Definition

The `getElementsByClassName()` method is used to select **all HTML elements** having the same class name.

Unlike `getElementById()`, this method returns a **collection of elements**, not a single element.

---

## Why do we use getElementsByClassName()?

Sometimes multiple elements share the same class.

Example

```html
<p class="msg">Java</p>

<p class="msg">Python</p>

<p class="msg">JavaScript</p>
```

Instead of changing one element, we can change all of them together.

---

## Syntax

```javascript
document.getElementsByClassName("className");
```

### Parameter

| Parameter | Description |
|-----------|-------------|
| className | Name of the class |

### Return Value

Returns an **HTMLCollection**.

---

## Complete Example 1 - Change First Element

```html
<!DOCTYPE html>
<html>
<head>
<title>Class Example</title>
</head>
<body>

<p class="msg">Java</p>
<p class="msg">Python</p>
<p class="msg">JavaScript</p>

<button onclick="changeFirst()">Click</button>

<script>

function changeFirst(){

document.getElementsByClassName("msg")[0].style.color="red";

}

</script>

</body>
</html>
```

---

## Complete Example 2 - Change All Elements

```html
<!DOCTYPE html>
<html>
<head>
<title>Loop Example</title>
</head>
<body>

<p class="msg">Java</p>
<p class="msg">Python</p>
<p class="msg">JavaScript</p>

<button onclick="changeAll()">Click</button>

<script>

function changeAll(){

let x=document.getElementsByClassName("msg");

for(let i=0;i<x.length;i++){

x[i].style.color="blue";

}

}

</script>

</body>
</html>
```

---

## How getElementsByClassName() Works

```
document

↓

Search Class Name

↓

Find All Matching Elements

↓

Return HTMLCollection

↓

Access Using Index
```

---

## Important Points

- Returns multiple elements.
- Uses index numbers.
- Starts from index 0.
- Returns an HTMLCollection.
- Use loops to modify all elements.

---

## Common Mistakes

Wrong

```javascript
document.getElementsByClassName("msg").style.color="red";
```

Correct

```javascript
document.getElementsByClassName("msg")[0].style.color="red";
```

---

## Interview Questions

1. What does `getElementsByClassName()` return?
2. Can it return one element?
3. Why do we use indexes?
4. Which loop is commonly used with HTMLCollection?

---

## Assignment

Create four paragraphs with the same class.

When clicking a button, all paragraphs should become green.

---

# getElementsByTagName()

## Definition

The `getElementsByTagName()` method selects **all HTML elements having the same tag name**.

It returns an HTMLCollection.

---

## Why do we use getElementsByTagName()?

Suppose a webpage has many paragraphs.

```html
<p>Java</p>

<p>Python</p>

<p>JavaScript</p>
```

Instead of giving every paragraph an ID or class, JavaScript can directly select all `<p>` tags.

---

## Syntax

```javascript
document.getElementsByTagName("tagName");
```

### Parameter

| Parameter | Description |
|-----------|-------------|
| tagName | HTML Tag Name |

---

## Complete Example 1

```html
<!DOCTYPE html>
<html>
<head>
<title>Tag Example</title>
</head>
<body>

<p>Java</p>

<p>Python</p>

<p>JavaScript</p>

<button onclick="changeColor()">Change Color</button>

<script>

function changeColor(){

let p=document.getElementsByTagName("p");

for(let i=0;i<p.length;i++){

p[i].style.color="red";

}

}

</script>

</body>
</html>
```

---

## Complete Example 2

```html
<!DOCTYPE html>
<html>
<head>
<title>Font Size</title>
</head>
<body>

<h2>Java</h2>

<h2>Python</h2>

<h2>JavaScript</h2>

<button onclick="increaseFont()">Increase Font</button>

<script>

function increaseFont(){

let h=document.getElementsByTagName("h2");

for(let i=0;i<h.length;i++){

h[i].style.fontSize="40px";

}

}

</script>

</body>
</html>
```

---

## How getElementsByTagName() Works

```
document

↓

Search Tag Name

↓

Find All Matching Tags

↓

Return HTMLCollection

↓

Access Using Index
```

---

## Important Points

- Returns multiple elements.
- Uses tag names like `p`, `h1`, `img`, `button`.
- Returns an HTMLCollection.
- Uses index numbers.
- Usually used with loops.

---

## Common Mistakes

Wrong

```javascript
document.getElementsByTagName("p").style.color="red";
```

Correct

```javascript
document.getElementsByTagName("p")[0].style.color="red";
```

or

```javascript
let p=document.getElementsByTagName("p");

for(let i=0;i<p.length;i++){

p[i].style.color="red";

}
```

---

## Interview Questions

1. What is `getElementsByTagName()`?
2. What does it return?
3. Can it select multiple elements?
4. Why do we use loops with it?
5. What is the difference between `getElementsByTagName()` and `getElementsByClassName()`?

---

## Assignment

Create five `<h3>` headings.

When clicking a button:

- Change all heading colors to blue.
- Increase the font size.
- Make all headings bold using JavaScript.
  
---
# querySelector()

## Definition

The `querySelector()` method is used to select the **first HTML element** that matches a specified CSS selector.

Unlike `getElementById()`, `querySelector()` can select elements using:

- ID (`#`)
- Class (`.`)
- Tag Name
- Attribute
- CSS Selectors

If multiple elements match the selector, it returns **only the first matching element**.

---

## Why do we use querySelector()?

Suppose we have three paragraphs.

```html
<p class="msg">Java</p>
<p class="msg">Python</p>
<p class="msg">JavaScript</p>
```

If we want to change **only the first paragraph**, we can use `querySelector()`.

---

## Syntax

```javascript
document.querySelector("CSS Selector");
```

### Parameter

| Parameter | Description |
|-----------|-------------|
| CSS Selector | ID, Class, Tag Name or any valid CSS Selector |

### Return Value

Returns the **first matching HTML element**.

If no matching element exists, it returns **null**.

---

## Example 1 - Select by ID

```html
<!DOCTYPE html>
<html>
<head>
<title>querySelector()</title>
</head>
<body>

<h1 id="title">Welcome Students</h1>

<button onclick="changeText()">Click</button>

<script>

function changeText(){

document.querySelector("#title").innerHTML="Welcome Java Full Stack";

}

</script>

</body>
</html>
```

---

## Example 2 - Select by Class

```html
<!DOCTYPE html>
<html>
<head>
<title>querySelector()</title>
</head>
<body>

<p class="msg">Java</p>
<p class="msg">Python</p>
<p class="msg">JavaScript</p>

<button onclick="changeColor()">Click</button>

<script>

function changeColor(){

document.querySelector(".msg").style.color="red";

}

</script>

</body>
</html>
```

Only the first paragraph changes.

---

## Example 3 - Select by Tag Name

```html
<!DOCTYPE html>
<html>
<head>
<title>querySelector()</title>
</head>
<body>

<h2>Java</h2>

<h2>Python</h2>

<h2>JavaScript</h2>

<button onclick="changeFont()">Click</button>

<script>

function changeFont(){

document.querySelector("h2").style.fontSize="45px";

}

</script>

</body>
</html>
```

Only the first `<h2>` changes.

---

## Example 4 - Change Background

```html
<!DOCTYPE html>
<html>
<head>
<title>querySelector()</title>
</head>
<body>

<div class="box">

Welcome Students

</div>

<br>

<button onclick="changeBG()">Click</button>

<script>

function changeBG(){

let box=document.querySelector(".box");

box.style.backgroundColor="yellow";
box.style.padding="20px";

}

</script>

</body>
</html>
```

---

## How querySelector() Works

```
document

↓

Search CSS Selector

↓

Find Matching Elements

↓

Return First Element

↓

JavaScript Manipulates It
```

---

## Important Points

- Returns only one element.
- Returns the first matching element.
- Accepts CSS selectors.
- Returns `null` if no element exists.

---

## Common Mistakes

Wrong

```javascript
document.querySelector("title");
```

Correct

```javascript
document.querySelector("#title");
```

---

## Difference Between getElementById() and querySelector()

| getElementById() | querySelector() |
|-----------------|-----------------|
| Uses ID only | Uses any CSS Selector |
| Faster | Slightly slower |
| Returns one element | Returns first matching element |

---

## Interview Questions

1. What is querySelector()?
2. What does it return?
3. Can querySelector() select by class?
4. Can querySelector() select by ID?
5. What happens if multiple elements match?

---

## Assignment

Create three headings having the same class.

When clicking a button, change only the first heading color to blue.

---

# querySelectorAll()

## Definition

The `querySelectorAll()` method selects **all HTML elements** that match a specified CSS selector.

It returns a **NodeList**.

Unlike `querySelector()`, it returns **every matching element**.

---

## Why do we use querySelectorAll()?

Suppose we have

```html
<p class="msg">Java</p>

<p class="msg">Python</p>

<p class="msg">JavaScript</p>
```

We want to change all paragraphs together.

Instead of selecting one by one, `querySelectorAll()` selects all at once.

---

## Syntax

```javascript
document.querySelectorAll("CSS Selector");
```

### Return Value

Returns a **NodeList**.

---

## Example 1 - Change Color

```html
<!DOCTYPE html>
<html>
<head>
<title>querySelectorAll()</title>
</head>
<body>

<p class="msg">Java</p>
<p class="msg">Python</p>
<p class="msg">JavaScript</p>

<button onclick="changeColor()">Click</button>

<script>

function changeColor(){

let x=document.querySelectorAll(".msg");

x.forEach(function(item){

item.style.color="red";

});

}

</script>

</body>
</html>
```

---

## Example 2 - Increase Font Size

```html
<!DOCTYPE html>
<html>
<head>
<title>querySelectorAll()</title>
</head>
<body>

<h2>Java</h2>

<h2>Python</h2>

<h2>JavaScript</h2>

<button onclick="increaseFont()">Increase</button>

<script>

function increaseFont(){

let h=document.querySelectorAll("h2");

h.forEach(function(item){

item.style.fontSize="40px";

});

}

</script>

</body>
</html>
```

---

## Example 3 - Using for Loop

```html
<!DOCTYPE html>
<html>
<head>
<title>querySelectorAll()</title>
</head>
<body>

<p>Java</p>
<p>Python</p>
<p>JavaScript</p>

<button onclick="change()">Click</button>

<script>

function change(){

let p=document.querySelectorAll("p");

for(let i=0;i<p.length;i++){

p[i].style.color="green";

}

}

</script>

</body>
</html>
```

---

## How querySelectorAll() Works

```
document

↓

Search CSS Selector

↓

Find All Matching Elements

↓

Return NodeList

↓

Loop Through Elements

↓

JavaScript Manipulates Them
```

---

## Important Points

- Returns all matching elements.
- Returns a NodeList.
- Supports `forEach()`.
- Supports `for` loop.
- Accepts CSS selectors.

---

## Difference Between querySelector() and querySelectorAll()

| querySelector() | querySelectorAll() |
|----------------|--------------------|
| Returns first element | Returns all elements |
| Single Element | NodeList |
| No loop needed | Usually uses loop |

---

## Interview Questions

1. What is querySelectorAll()?
2. What does it return?
3. What is NodeList?
4. Can we use forEach() with querySelectorAll()?
5. Difference between querySelector() and querySelectorAll()?

---

## Assignment

Create five paragraphs having the same class.

When clicking a button,

- Change all paragraph colors to blue.
- Increase font size.
- Make text bold.

---

# innerHTML

## Definition

`innerHTML` is used to **read or change the HTML content** inside an HTML element.

It can display plain text as well as HTML tags.

---

## Why do we use innerHTML?

Suppose we have

```html
<h1>Welcome</h1>
```

When the user clicks a button, we want to change it into

```html
<h2>Hello Students</h2>
```

`innerHTML` allows us to do this.

---

## Syntax

```javascript
element.innerHTML="Content";
```

---

## Example 1 - Change Text

```html
<!DOCTYPE html>
<html>
<head>
<title>innerHTML</title>
</head>
<body>

<h1 id="title">Welcome</h1>

<button onclick="changeText()">Click</button>

<script>

function changeText(){

document.getElementById("title").innerHTML="Hello Students";

}

</script>

</body>
</html>
```

---

## Example 2 - Add HTML Tags

```html
<!DOCTYPE html>
<html>
<head>
<title>innerHTML</title>
</head>
<body>

<div id="box"></div>

<button onclick="show()">Show</button>

<script>

function show(){

document.getElementById("box").innerHTML="<h2 style='color:red;'>JavaScript DOM</h2>";

}

</script>

</body>
</html>
```

---

## Example 3 - Add Image

```html
<!DOCTYPE html>
<html>
<head>
<title>innerHTML</title>
</head>
<body>

<div id="image"></div>

<button onclick="showImage()">Show Image</button>

<script>

function showImage(){

document.getElementById("image").innerHTML="<img src='https://picsum.photos/200'>";

}

</script>

</body>
</html>
```

---

## Important Points

- Can read HTML.
- Can write HTML.
- Supports HTML tags.
- Can create dynamic webpages.

---

## Interview Questions

1. What is innerHTML?
2. Can innerHTML insert HTML tags?
3. Can innerHTML replace existing content?

---

## Assignment

Create a button that displays an image and a heading using `innerHTML`.

---

# innerText

## Definition

`innerText` is used to **read or change only the text** inside an HTML element.

It does **not** interpret HTML tags.

---

## Why do we use innerText?

Use `innerText` when you only want to display or change text without rendering HTML.

---

## Syntax

```javascript
element.innerText="New Text";
```

---

## Example 1 - Change Text

```html
<!DOCTYPE html>
<html>
<head>
<title>innerText</title>
</head>
<body>

<h1 id="title">Welcome</h1>

<button onclick="change()">Change</button>

<script>

function change(){

document.getElementById("title").innerText="Hello Java Full Stack";

}

</script>

</body>
</html>
```

---

## Example 2 - Read Text

```html
<!DOCTYPE html>
<html>
<head>
<title>innerText</title>
</head>
<body>

<h1 id="title">JavaScript DOM</h1>

<button onclick="show()">Show</button>

<script>

function show(){

alert(document.getElementById("title").innerText);

}

</script>

</body>
</html>
```

---

## Difference Between innerHTML and innerText

| innerHTML | innerText |
|-----------|-----------|
| Reads HTML | Reads only text |
| Supports HTML tags | Ignores HTML tags |
| Can insert images, buttons, headings | Can insert only plain text |

---

## Important Points

- Used for text only.
- Does not render HTML tags.
- Safer when displaying user input.

---

## Interview Questions

1. What is innerText?
2. Difference between innerHTML and innerText?
3. Which one is used to insert HTML code?

---

## Assignment

Create a webpage with a heading and a button.

When clicking the button, change the heading text using `innerText`.

---
# style Property

## Definition

The `style` property is used to **change the CSS styles of an HTML element** using JavaScript.

It allows us to dynamically change the appearance of an element without modifying the CSS file.

Using the `style` property, we can change:

- Text Color
- Background Color
- Font Size
- Width
- Height
- Border
- Margin
- Padding
- Display
- Visibility
- Opacity
- Border Radius
- Text Alignment
- and many more CSS properties.

---

## Why do we use style Property?

Suppose a webpage contains a heading.

```html
<h1>Welcome Students</h1>
```

When the user clicks a button, we may want to

- Change the text color
- Increase font size
- Change the background color

Instead of writing CSS again, JavaScript can modify the CSS using the `style` property.

---

## Syntax

```javascript
element.style.property = "value";
```

---

## Example 1 - Change Text Color

```html
<!DOCTYPE html>
<html>
<head>
<title>style Property</title>
</head>
<body>

<h1 id="heading">JavaScript DOM</h1>

<button onclick="changeColor()">Change Color</button>

<script>

function changeColor(){

document.getElementById("heading").style.color="red";

}

</script>

</body>
</html>
```

---

## Example 2 - Change Background Color

```html
<!DOCTYPE html>
<html>
<head>
<title>Background Color</title>
</head>
<body>

<h1 id="heading">Welcome Students</h1>

<button onclick="changeBG()">Background</button>

<script>

function changeBG(){

document.getElementById("heading").style.backgroundColor="yellow";

}

</script>

</body>
</html>
```

---

## Example 3 - Change Font Size

```html
<!DOCTYPE html>
<html>
<head>
<title>Font Size</title>
</head>
<body>

<h1 id="heading">JavaScript</h1>

<button onclick="increaseFont()">Increase</button>

<script>

function increaseFont(){

document.getElementById("heading").style.fontSize="50px";

}

</script>

</body>
</html>
```

---

## Example 4 - Change Multiple Styles

```html
<!DOCTYPE html>
<html>
<head>
<title>Multiple Styles</title>
</head>
<body>

<h1 id="heading">JavaScript DOM</h1>

<button onclick="changeStyle()">Click</button>

<script>

function changeStyle(){

let h=document.getElementById("heading");

h.style.color="white";
h.style.backgroundColor="blue";
h.style.padding="20px";
h.style.borderRadius="10px";
h.style.textAlign="center";

}

</script>

</body>
</html>
```

---

## Common Style Properties

| Property | Example |
|----------|---------|
| color | red |
| backgroundColor | yellow |
| fontSize | 40px |
| width | 300px |
| height | 200px |
| border | 2px solid black |
| borderRadius | 20px |
| padding | 15px |
| margin | 20px |
| textAlign | center |
| display | none |
| visibility | hidden |
| opacity | 0.5 |

---

## Important Points

- CSS property names use **camelCase**.
- `background-color` becomes `backgroundColor`.
- `font-size` becomes `fontSize`.
- Values should be written inside quotes.

---

## Interview Questions

1. What is the style property?
2. Why do we use camelCase?
3. How do you change the background color using JavaScript?
4. How do you increase the font size?

---

## Assignment

Create a button that changes

- Text Color
- Background Color
- Font Size
- Border
- Border Radius

of a heading.

---

# value Property

## Definition

The `value` property is used to **get or set the value of form elements** such as:

- Text Box
- Password Box
- Text Area
- Drop-down List
- Radio Button
- Checkbox

It is one of the most commonly used properties in form validation.

---

## Why do we use value?

Suppose a user enters

```
Mahesh
```

inside a textbox.

JavaScript uses `.value` to read the entered text.

---

## Syntax

```javascript
element.value;
```

---

## Example 1 - Read Textbox Value

```html
<!DOCTYPE html>
<html>
<head>
<title>value Property</title>
</head>
<body>

<input type="text" id="name">

<button onclick="show()">Show</button>

<script>

function show(){

let username=document.getElementById("name").value;

alert(username);

}

</script>

</body>
</html>
```

---

## Example 2 - Display Input

```html
<!DOCTYPE html>
<html>
<head>
<title>Input Example</title>
</head>
<body>

<input type="text" id="name">

<button onclick="display()">Display</button>

<h2 id="result"></h2>

<script>

function display(){

let user=document.getElementById("name").value;

document.getElementById("result").innerHTML=user;

}

</script>

</body>
</html>
```

---

## Example 3 - Set Value

```html
<!DOCTYPE html>
<html>
<head>
<title>Set Value</title>
</head>
<body>

<input type="text" id="name">

<button onclick="setValue()">Set Value</button>

<script>

function setValue(){

document.getElementById("name").value="Java Full Stack";

}

</script>

</body>
</html>
```

---

## Important Points

- Used only for form elements.
- Can read user input.
- Can also change input values.

---

## Interview Questions

1. What is the value property?
2. Which HTML elements use value?
3. Can value set data as well as read data?

---

## Assignment

Create a textbox.

When clicking a button,

display the entered text inside a heading.

---

# setAttribute()

## Definition

The `setAttribute()` method is used to **add a new attribute or change the value of an existing attribute** of an HTML element.

---

## Why do we use setAttribute()?

We can dynamically change

- Image Source
- Link
- Width
- Height
- Placeholder
- Class
- ID
- Title

without editing the HTML.

---

## Syntax

```javascript
element.setAttribute("attribute","value");
```

---

## Example 1 - Change Image

```html
<!DOCTYPE html>
<html>
<head>
<title>setAttribute()</title>
</head>
<body>

<img id="photo"
src="https://picsum.photos/200">

<br><br>

<button onclick="changeImage()">Change</button>

<script>

function changeImage(){

document.getElementById("photo")
.setAttribute("src","https://picsum.photos/300");

}

</script>

</body>
</html>
```

---

## Example 2 - Add Placeholder

```html
<!DOCTYPE html>
<html>
<head>
<title>Placeholder</title>
</head>
<body>

<input type="text" id="name">

<button onclick="addPlaceholder()">Click</button>

<script>

function addPlaceholder(){

document.getElementById("name")
.setAttribute("placeholder","Enter Your Name");

}

</script>

</body>
</html>
```

---

## Important Points

- Adds a new attribute.
- Updates an existing attribute.
- Works with almost every HTML element.

---

## Interview Questions

1. What is setAttribute()?
2. Can it modify an existing attribute?
3. Give two examples of attributes changed using setAttribute().

---

## Assignment

Create an image and a button.

When clicking the button,

change the image using `setAttribute()`.

---

# getAttribute()

## Definition

The `getAttribute()` method is used to **read the value of an HTML attribute**.

---

## Why do we use getAttribute()?

Suppose an image contains

```html
<img src="image.jpg">
```

JavaScript can read the value of the `src` attribute.

---

## Syntax

```javascript
element.getAttribute("attribute");
```

---

## Example 1 - Read Image Source

```html
<!DOCTYPE html>
<html>
<head>
<title>getAttribute()</title>
</head>
<body>

<img id="photo"
src="https://picsum.photos/200">

<br><br>

<button onclick="show()">Show Source</button>

<script>

function show(){

let image=document.getElementById("photo")
.getAttribute("src");

alert(image);

}

</script>

</body>
</html>
```

---

## Example 2 - Read Placeholder

```html
<!DOCTYPE html>
<html>
<head>
<title>Placeholder</title>
</head>
<body>

<input
id="name"
placeholder="Enter Name">

<button onclick="readPlaceholder()">Click</button>

<script>

function readPlaceholder(){

let text=document.getElementById("name")
.getAttribute("placeholder");

alert(text);

}

</script>

</body>
</html>
```

---

## Important Points

- Reads attribute values.
- Does not change attributes.
- Returns the attribute value as a string.

---

## Difference Between setAttribute() and getAttribute()

| setAttribute() | getAttribute() |
|---------------|----------------|
| Adds or updates an attribute | Reads an attribute |
| Requires attribute and value | Requires only attribute name |
| Modifies HTML | Reads HTML |

---

## Interview Questions

1. What is getAttribute()?
2. What does it return?
3. Difference between setAttribute() and getAttribute()?
4. Can getAttribute() modify an attribute?

---

## Assignment

Create an image.

Display its `src` value in an alert box using `getAttribute()`.

---

# removeAttribute()

## Definition

The `removeAttribute()` method is used to **remove an attribute** from an HTML element.

After removing the attribute, the element behaves as if that attribute never existed.

---

## Why do we use removeAttribute()?

Suppose we have a textbox.

```html
<input type="text" disabled>
```

Since it is disabled, the user cannot type.

Using JavaScript, we can remove the **disabled** attribute and allow the user to enter data.

---

## Syntax

```javascript
element.removeAttribute("attributeName");
```

### Parameter

| Parameter | Description |
|-----------|-------------|
| attributeName | Name of the attribute to remove |

---

## Example 1 - Remove Disabled Attribute

```html
<!DOCTYPE html>
<html>
<head>
<title>removeAttribute()</title>
</head>
<body>

<input
type="text"
id="name"
placeholder="Enter Name"
disabled>

<br><br>

<button onclick="enableTextbox()">Enable</button>

<script>

function enableTextbox(){

document.getElementById("name")
.removeAttribute("disabled");

}

</script>

</body>
</html>
```

---

## Example 2 - Remove Placeholder

```html
<!DOCTYPE html>
<html>
<head>
<title>removeAttribute()</title>
</head>
<body>

<input
type="text"
id="name"
placeholder="Enter Your Name">

<br><br>

<button onclick="removePlaceholder()">Remove Placeholder</button>

<script>

function removePlaceholder(){

document.getElementById("name")
.removeAttribute("placeholder");

}

</script>

</body>
</html>
```

---

## Example 3 - Remove Width Attribute

```html
<!DOCTYPE html>
<html>
<head>
<title>removeAttribute()</title>
</head>
<body>

<img
id="photo"
src="https://picsum.photos/200"
width="300">

<br><br>

<button onclick="removeWidth()">Remove Width</button>

<script>

function removeWidth(){

document.getElementById("photo")
.removeAttribute("width");

}

</script>

</body>
</html>
```

---

## Important Points

- Removes only one attribute at a time.
- Does not remove the HTML element.
- Removes attributes like:
  - disabled
  - placeholder
  - width
  - height
  - title
  - style
  - class

---

## Interview Questions

1. What is removeAttribute()?
2. Can removeAttribute() delete an HTML element?
3. Which attributes can be removed?

---

## Assignment

Create a disabled button.

When clicking another button,

enable it using `removeAttribute()`.

---

# classList.add()

## Definition

The `classList.add()` method is used to **add one or more CSS classes** to an HTML element.

It applies the CSS styles defined in that class.

---

## Why do we use classList.add()?

Instead of writing multiple style properties using JavaScript,

we can create a CSS class once and apply it whenever required.

---

## Syntax

```javascript
element.classList.add("className");
```

---

## Example 1 - Add CSS Class

```html
<!DOCTYPE html>
<html>
<head>

<title>classList.add()</title>

<style>

.box{

background-color:blue;
color:white;
padding:20px;
font-size:35px;
text-align:center;
border-radius:10px;

}

</style>

</head>
<body>

<h1 id="heading">

Welcome Students

</h1>

<button onclick="addClass()">

Add Class

</button>

<script>

function addClass(){

document.getElementById("heading")
.classList.add("box");

}

</script>

</body>
</html>
```

---

## Example 2 - Add Multiple Classes

```html
<!DOCTYPE html>
<html>
<head>

<style>

.red{

color:red;

}

.big{

font-size:40px;

}

</style>

</head>
<body>

<h1 id="title">

JavaScript

</h1>

<button onclick="styleText()">

Click

</button>

<script>

function styleText(){

let h=document.getElementById("title");

h.classList.add("red");

h.classList.add("big");

}

</script>

</body>
</html>
```

---

## Important Points

- Adds one or more CSS classes.
- Existing classes are not removed.
- Same class is not added twice.

---

## Interview Questions

1. What is classList.add()?
2. Why is classList.add() better than changing multiple style properties?
3. Can we add multiple classes?

---

## Assignment

Create a CSS class named **success**.

When clicking a button,

apply the class to a paragraph.

---

# classList.remove()

## Definition

The `classList.remove()` method is used to **remove a CSS class** from an HTML element.

After removing the class, all styles belonging to that class disappear.

---

## Syntax

```javascript
element.classList.remove("className");
```

---

## Example 1

```html
<!DOCTYPE html>
<html>
<head>

<style>

.box{

background:green;
color:white;
padding:20px;
font-size:35px;

}

</style>

</head>
<body>

<h1
id="heading"
class="box">

JavaScript DOM

</h1>

<button onclick="removeClass()">

Remove Class

</button>

<script>

function removeClass(){

document.getElementById("heading")
.classList.remove("box");

}

</script>

</body>
</html>
```

---

## Example 2

```html
<!DOCTYPE html>
<html>
<head>

<style>

.red{

color:red;

}

</style>

</head>
<body>

<p
id="text"
class="red">

Hello Students

</p>

<button onclick="removeColor()">

Remove Color

</button>

<script>

function removeColor(){

document.getElementById("text")
.classList.remove("red");

}

</script>

</body>
</html>
```

---

## Important Points

- Removes only the specified class.
- Does not remove other classes.
- The HTML element remains on the page.

---

## Interview Questions

1. What is classList.remove()?
2. Does it remove the HTML element?
3. Can it remove multiple classes?

---

## Assignment

Create a heading with a CSS class.

Remove the class when clicking a button.

---

# classList.toggle()

## Definition

The `classList.toggle()` method is used to **add a class if it does not exist and remove it if it already exists**.

It acts like an ON/OFF switch.

---

## Why do we use classList.toggle()?

It is commonly used for:

- Dark Mode
- Navigation Menu
- Sidebar
- Show/Hide Password
- Responsive Menu
- Popup Windows

---

## Syntax

```javascript
element.classList.toggle("className");
```

---

## Example 1 - Dark Mode

```html
<!DOCTYPE html>
<html>
<head>

<style>

.dark{

background:black;
color:white;

}

</style>

</head>
<body id="body">

<h1>

JavaScript DOM

</h1>

<button onclick="darkMode()">

Dark Mode

</button>

<script>

function darkMode(){

document.getElementById("body")
.classList.toggle("dark");

}

</script>

</body>
</html>
```

---

## Example 2 - Show Border

```html
<!DOCTYPE html>
<html>
<head>

<style>

.border{

border:5px solid red;
padding:20px;

}

</style>

</head>
<body>

<div id="box">

Hello Students

</div>

<br>

<button onclick="toggleBorder()">

Toggle Border

</button>

<script>

function toggleBorder(){

document.getElementById("box")
.classList.toggle("border");

}

</script>

</body>
</html>
```

---

## Example 3 - Highlight Text

```html
<!DOCTYPE html>
<html>
<head>

<style>

.highlight{

background:yellow;
font-size:35px;

}

</style>

</head>
<body>

<p id="text">

Java Full Stack

</p>

<button onclick="highlightText()">

Highlight

</button>

<script>

function highlightText(){

document.getElementById("text")
.classList.toggle("highlight");

}

</script>

</body>
</html>
```

---

## How classList.toggle() Works

```
Click Button

↓

Class Exists?

↓

Yes

↓

Remove Class

OR

No

↓

Add Class
```

---

## Difference Between add(), remove() and toggle()

| Method | Purpose |
|---------|----------|
| classList.add() | Adds a class |
| classList.remove() | Removes a class |
| classList.toggle() | Adds or removes a class automatically |

---

## Important Points

- Used for ON/OFF functionality.
- Very useful for Dark Mode.
- Eliminates the need for writing if-else conditions in many cases.

---

## Interview Questions

1. What is classList.toggle()?
2. Why is toggle() used in Dark Mode?
3. Difference between add(), remove(), and toggle()?
4. What happens if the class already exists?

---

## Assignment

Create a webpage with:

- One heading
- One button

When clicking the button,

- First click → Change background to black and text to white.
- Second click → Restore the original colors using `classList.toggle()`.

---
# createElement()

## Definition

The `createElement()` method is used to **create a new HTML element dynamically** using JavaScript.

The created element is **not visible** on the webpage until it is added to the HTML document.

---

## Why do we use createElement()?

Suppose we want to add a new paragraph, heading, button, or image after the webpage has already loaded.

Instead of writing HTML manually, JavaScript can create new elements dynamically.

---

## Syntax

```javascript
document.createElement("tagName");
```

### Parameter

| Parameter | Description |
|-----------|-------------|
| tagName | Name of the HTML element to create |

---

## Example 1 - Create Heading

```html
<!DOCTYPE html>
<html>
<head>
<title>createElement()</title>
</head>
<body>

<button onclick="createHeading()">

Create Heading

</button>

<script>

function createHeading(){

let h1=document.createElement("h1");

h1.innerHTML="Welcome Java Full Stack";

document.body.appendChild(h1);

}

</script>

</body>
</html>
```

---

## Example 2 - Create Paragraph

```html
<!DOCTYPE html>
<html>
<head>
<title>Create Paragraph</title>
</head>
<body>

<button onclick="createParagraph()">

Create Paragraph

</button>

<script>

function createParagraph(){

let p=document.createElement("p");

p.innerHTML="JavaScript is awesome!";

document.body.appendChild(p);

}

</script>

</body>
</html>
```

---

## Example 3 - Create Button

```html
<!DOCTYPE html>
<html>
<head>
<title>Create Button</title>
</head>
<body>

<button onclick="createButton()">

Create New Button

</button>

<script>

function createButton(){

let btn=document.createElement("button");

btn.innerHTML="New Button";

document.body.appendChild(btn);

}

</script>

</body>
</html>
```

---

## Important Points

- Creates only the element.
- The element is not displayed until it is added to the webpage.
- Works with any HTML tag.

---

## Interview Questions

1. What is createElement()?
2. Does createElement() display the element automatically?
3. Which method is used to display the created element?

---

## Assignment

Create a webpage where clicking a button creates a new `<h2>` element.

---

# appendChild()

## Definition

The `appendChild()` method is used to **add a newly created element as the last child** of another HTML element.

It is commonly used together with `createElement()`.

---

## Why do we use appendChild()?

After creating an element using `createElement()`, it exists only in memory.

To display it on the webpage, we must append it to an existing element.

---

## Syntax

```javascript
parentElement.appendChild(childElement);
```

---

## Example 1 - Add List Item

```html
<!DOCTYPE html>
<html>
<head>
<title>appendChild()</title>
</head>
<body>

<ul id="list">

<li>Java</li>

<li>Python</li>

</ul>

<button onclick="addItem()">

Add JavaScript

</button>

<script>

function addItem(){

let li=document.createElement("li");

li.innerHTML="JavaScript";

document.getElementById("list").appendChild(li);

}

</script>

</body>
</html>
```

---

## Example 2 - Add Paragraph

```html
<!DOCTYPE html>
<html>
<head>
<title>appendChild()</title>
</head>
<body>

<div id="box">

</div>

<button onclick="addParagraph()">

Add Paragraph

</button>

<script>

function addParagraph(){

let p=document.createElement("p");

p.innerHTML="Welcome Students";

document.getElementById("box").appendChild(p);

}

</script>

</body>
</html>
```

---

## Important Points

- Adds an element to the end.
- Requires a parent element.
- Usually used with `createElement()`.

---

## Interview Questions

1. What is appendChild()?
2. Why is appendChild() used with createElement()?
3. Where does appendChild() add the new element?

---

## Assignment

Create a button that adds a new `<li>` item to an unordered list.

---

# remove()

## Definition

The `remove()` method is used to **delete an HTML element** from the webpage.

Once removed, the element disappears completely.

---

## Syntax

```javascript
element.remove();
```

---

## Example 1 - Remove Heading

```html
<!DOCTYPE html>
<html>
<head>
<title>remove()</title>
</head>
<body>

<h1 id="heading">

JavaScript DOM

</h1>

<button onclick="removeHeading()">

Remove Heading

</button>

<script>

function removeHeading(){

document.getElementById("heading").remove();

}

</script>

</body>
</html>
```

---

## Example 2 - Remove Paragraph

```html
<!DOCTYPE html>
<html>
<head>
<title>Remove Paragraph</title>
</head>
<body>

<p id="text">

Hello Students

</p>

<button onclick="removeText()">

Remove Paragraph

</button>

<script>

function removeText(){

document.getElementById("text").remove();

}

</script>

</body>
</html>
```

---

## Important Points

- Deletes the selected HTML element.
- Permanently removes it from the webpage.
- Does not remove only the text; it removes the entire element.

---

## Interview Questions

1. What is remove()?
2. Can remove() delete multiple elements at once?
3. What happens after an element is removed?

---

## Assignment

Create two paragraphs.

Remove the second paragraph when clicking a button.

---

# replaceChild()

## Definition

The `replaceChild()` method is used to **replace an existing child element with a new child element**.

---

## Why do we use replaceChild()?

Sometimes we don't want to remove an element completely.

Instead, we replace it with another element.

---

## Syntax

```javascript
parentElement.replaceChild(newElement, oldElement);
```

---

## Example 1 - Replace Heading

```html
<!DOCTYPE html>
<html>
<head>
<title>replaceChild()</title>
</head>
<body>

<div id="container">

<h2 id="oldHeading">

Old Heading

</h2>

</div>

<button onclick="replaceHeading()">

Replace Heading

</button>

<script>

function replaceHeading(){

let newHeading=document.createElement("h2");

newHeading.innerHTML="New Heading";

let oldHeading=document.getElementById("oldHeading");

let parent=document.getElementById("container");

parent.replaceChild(newHeading,oldHeading);

}

</script>

</body>
</html>
```

---

## Example 2 - Replace Paragraph

```html
<!DOCTYPE html>
<html>
<head>
<title>Replace Paragraph</title>
</head>
<body>

<div id="box">

<p id="oldText">

Old Paragraph

</p>

</div>

<button onclick="replaceText()">

Replace

</button>

<script>

function replaceText(){

let p=document.createElement("p");

p.innerHTML="New Paragraph";

let old=document.getElementById("oldText");

document.getElementById("box").replaceChild(p,old);

}

</script>

</body>
</html>
```

---

## Important Points

- Requires a parent element.
- Replaces only child elements.
- The old element is removed automatically.

---

## Difference Between appendChild() and replaceChild()

| appendChild() | replaceChild() |
|--------------|----------------|
| Adds a new element | Replaces an existing element |
| Old element remains | Old element is removed |
| Inserts at the end | Replaces at the same position |

---

## Interview Questions

1. What is replaceChild()?
2. Why do we need the parent element?
3. Difference between appendChild() and replaceChild()?
4. What happens to the old element after replacement?

---

## Assignment

Create a webpage with:

- One `<h1>` heading
- One button

When clicking the button,

replace the existing heading with a new heading saying **"JavaScript DOM Completed"**.

---
# addEventListener()

## Definition

The `addEventListener()` method is used to **attach an event to an HTML element**.

Unlike `onclick`, it separates JavaScript from HTML, making the code cleaner and easier to maintain.

It is the most commonly used method for handling events in modern JavaScript.

---

## Why do we use addEventListener()?

Suppose we have a button.

When the user clicks the button, we want to perform an action.

Instead of writing

```html
<button onclick="show()">
```

we can write

```javascript
button.addEventListener("click", show);
```

This keeps HTML and JavaScript separate.

---

## Syntax

```javascript
element.addEventListener("eventName", functionName);
```

or

```javascript
element.addEventListener("eventName", function(){

// code

});
```

### Parameters

| Parameter | Description |
|-----------|-------------|
| eventName | Name of the event |
| function | Function that executes when the event occurs |

---

## Example 1 - Button Click

```html
<!DOCTYPE html>
<html>
<head>
<title>addEventListener()</title>
</head>
<body>

<h1 id="heading">

Welcome Students

</h1>

<button id="btn">

Click Me

</button>

<script>

document.getElementById("btn")
.addEventListener("click",changeText);

function changeText(){

document.getElementById("heading").innerHTML="JavaScript DOM";

}

</script>

</body>
</html>
```

---

## Example 2 - Change Background

```html
<!DOCTYPE html>
<html>
<head>
<title>Background</title>
</head>
<body>

<button id="btn">

Background Color

</button>

<script>

document.getElementById("btn")
.addEventListener("click",function(){

document.body.style.backgroundColor="yellow";

});

</script>

</body>
</html>
```

---

## Important Points

- Modern way of handling events.
- Keeps HTML clean.
- Multiple events can be attached to the same element.

---

## Difference Between onclick and addEventListener()

| onclick | addEventListener() |
|----------|--------------------|
| Old Method | Modern Method |
| One event at a time | Multiple events can be attached |
| Written inside HTML | Written inside JavaScript |

---

## Interview Questions

1. What is addEventListener()?
2. Why is it preferred over onclick?
3. Can we attach multiple events?

---

## Assignment

Create a button.

When clicking it,

change the heading text using `addEventListener()`.

---

# Mouse Events

## Definition

Mouse Events are triggered when the user interacts with the mouse.

Examples include:

- click
- dblclick
- mouseover
- mouseout
- mousedown
- mouseup
- mousemove

---

## Common Mouse Events

| Event | Description |
|--------|-------------|
| click | Single mouse click |
| dblclick | Double click |
| mouseover | Mouse enters an element |
| mouseout | Mouse leaves an element |
| mousedown | Mouse button is pressed |
| mouseup | Mouse button is released |
| mousemove | Mouse moves over an element |

---

# click Event

## Example

```html
<!DOCTYPE html>
<html>
<head>
<title>Click Event</title>
</head>
<body>

<button id="btn">

Click Me

</button>

<script>

document.getElementById("btn")
.addEventListener("click",function(){

alert("Button Clicked");

});

</script>

</body>
</html>
```

---

# dblclick Event

## Example

```html
<!DOCTYPE html>
<html>
<head>
<title>Double Click</title>
</head>
<body>

<button id="btn">

Double Click

</button>

<script>

document.getElementById("btn")
.addEventListener("dblclick",function(){

alert("Double Click Detected");

});

</script>

</body>
</html>
```

---

# mouseover Event

## Example

```html
<!DOCTYPE html>
<html>
<head>
<title>Mouse Over</title>
</head>
<body>

<h1 id="heading">

Move Mouse Here

</h1>

<script>

document.getElementById("heading")
.addEventListener("mouseover",function(){

this.style.color="red";

});

</script>

</body>
</html>
```

---

# mouseout Event

## Example

```html
<!DOCTYPE html>
<html>
<head>
<title>Mouse Out</title>
</head>
<body>

<h1 id="heading">

Move Mouse Here

</h1>

<script>

let h=document.getElementById("heading");

h.addEventListener("mouseover",function(){

h.style.color="red";

});

h.addEventListener("mouseout",function(){

h.style.color="black";

});

</script>

</body>
</html>
```

---

## Assignment

Create a paragraph.

- Mouse Over → Text becomes blue.
- Mouse Out → Text becomes black.

---

# Keyboard Events

## Definition

Keyboard Events occur when the user presses or releases a key on the keyboard.

They are mainly used for:

- Shortcuts
- Games
- Search Boxes
- Form Validation
- Keyboard Controls

---

## Common Keyboard Events

| Event | Description |
|--------|-------------|
| keydown | Fires when a key is pressed |
| keyup | Fires when a key is released |
| keypress | Fires while typing (deprecated) |

---

# keydown Event

## Example

```html
<!DOCTYPE html>
<html>
<head>
<title>Key Down</title>
</head>
<body>

<script>

document.addEventListener("keydown",function(){

alert("Key Pressed");

});

</script>

</body>
</html>
```

---

# event.key

The `event.key` property returns the key pressed by the user.

---

## Example - Detect A and B

```html
<!DOCTYPE html>
<html>
<head>
<title>Keyboard Event</title>
</head>
<body>

<h1 id="result">

Press A or B

</h1>

<script>

document.addEventListener("keydown",function(event){

if(event.key=="a" || event.key=="A"){

result.innerHTML="You Pressed A";

}

else if(event.key=="b" || event.key=="B"){

result.innerHTML="You Pressed B";

}

});

</script>

</body>
</html>
```

---

## Example - Ctrl + N

```html
<!DOCTYPE html>
<html>
<head>
<title>Ctrl + N</title>
</head>
<body>

<h1>

Press Ctrl + N

</h1>

<script>

document.addEventListener("keydown",function(event){

if(event.ctrlKey && event.key=="n"){

event.preventDefault();

alert("Ctrl + N Pressed");

}

});

</script>

</body>
</html>
```

---

## Example - Arrow Keys

```html
<!DOCTYPE html>
<html>
<head>
<title>Arrow Keys</title>
</head>
<body>

<h1 id="text">

Press Arrow Keys

</h1>

<script>

document.addEventListener("keydown",function(event){

if(event.key=="ArrowUp"){

text.innerHTML="⬆ UP";

}

else if(event.key=="ArrowDown"){

text.innerHTML="⬇ DOWN";

}

else if(event.key=="ArrowLeft"){

text.innerHTML="⬅ LEFT";

}

else if(event.key=="ArrowRight"){

text.innerHTML="➡ RIGHT";

}

});

</script>

</body>
</html>
```

---

## Assignment

Create a webpage where:

- Press **R** → Background becomes Red.
- Press **G** → Background becomes Green.
- Press **B** → Background becomes Blue.

---

# Form Events

## Definition

Form Events occur when the user interacts with form elements like:

- Text Box
- Password
- Text Area
- Select Box

---

## Common Form Events

| Event | Description |
|--------|-------------|
| focus | Fires when an element gets focus |
| blur | Fires when an element loses focus |
| change | Fires when the value changes |
| submit | Fires when the form is submitted |

---

# focus Event

## Example

```html
<!DOCTYPE html>
<html>
<head>
<title>Focus</title>
</head>
<body>

<input type="text" id="name">

<script>

document.getElementById("name")
.addEventListener("focus",function(){

this.style.backgroundColor="yellow";

});

</script>

</body>
</html>
```

---

# blur Event

## Example

```html
<!DOCTYPE html>
<html>
<head>
<title>Blur</title>
</head>
<body>

<input type="text" id="name">

<script>

let input=document.getElementById("name");

input.addEventListener("focus",function(){

input.style.backgroundColor="yellow";

});

input.addEventListener("blur",function(){

input.style.backgroundColor="white";

});

</script>

</body>
</html>
```

---

# change Event

## Example

```html
<!DOCTYPE html>
<html>
<head>
<title>Change Event</title>
</head>
<body>

<select id="course">

<option>Java</option>
<option>Python</option>
<option>JavaScript</option>

</select>

<h2 id="result"></h2>

<script>

document.getElementById("course")
.addEventListener("change",function(){

result.innerHTML=this.value;

});

</script>

</body>
</html>
```

---

# submit Event

## Example

```html
<!DOCTYPE html>
<html>
<head>
<title>Submit Event</title>
</head>
<body>

<form id="myForm">

<input
type="text"
placeholder="Enter Name">

<br><br>

<button>

Submit

</button>

</form>

<script>

document.getElementById("myForm")
.addEventListener("submit",function(event){

event.preventDefault();

alert("Form Submitted");

});

</script>

</body>
</html>
```

---

## Important Points

- `focus` → Cursor enters an input.
- `blur` → Cursor leaves an input.
- `change` → Value changes.
- `submit` → Form submission.

---

## Interview Questions

1. What are Form Events?
2. Difference between focus and blur?
3. Why do we use preventDefault() in submit?
4. Difference between keydown and keyup?
5. Difference between click and dblclick?

---

## Assignment

Create a Registration Form.

- Focus → Yellow Background.
- Blur → White Background.
- Submit → Show "Registration Successful" using `alert()`.

---
# textContent

## Definition

The `textContent` property is used to **get or set the text content** of an HTML element.

Unlike `innerHTML`, it treats everything as plain text and does not render HTML tags.

---

## Why do we use textContent?

Suppose you want to display user input exactly as entered without interpreting HTML tags.

`textContent` is the best choice.

It is also slightly faster than `innerHTML` because it does not parse HTML.

---

## Syntax

```javascript
element.textContent="New Text";
```

---

## Example 1 - Change Text

```html
<!DOCTYPE html>
<html>
<head>
<title>textContent</title>
</head>
<body>

<h1 id="title">

Welcome Students

</h1>

<button onclick="changeText()">

Change Text

</button>

<script>

function changeText(){

document.getElementById("title").textContent="JavaScript DOM";

}

</script>

</body>
</html>
```

---

## Example 2 - Show HTML Tags as Text

```html
<!DOCTYPE html>
<html>
<head>
<title>textContent</title>
</head>
<body>

<div id="box">

Hello

</div>

<button onclick="showText()">

Show

</button>

<script>

function showText(){

document.getElementById("box").textContent="<h1>Hello Students</h1>";

}

</script>

</body>
</html>
```

### Output

Instead of creating a heading, it displays:

```
<h1>Hello Students</h1>
```

---

## Difference Between innerHTML, innerText and textContent

| innerHTML | innerText | textContent |
|------------|-----------|-------------|
| Reads and writes HTML | Reads and writes only visible text | Reads and writes all text |
| Supports HTML tags | Ignores HTML tags | Shows HTML tags as text |
| Parses HTML | Plain Text | Plain Text |

---

## Important Points

- Faster than `innerHTML`.
- Does not render HTML tags.
- Best for displaying user input safely.

---

## Interview Questions

1. What is `textContent`?
2. Difference between `innerText` and `textContent`?
3. Difference between `innerHTML` and `textContent`?

---

## Assignment

Create a button.

When clicking it,

display `<b>Hello Students</b>` using `textContent`.

---

# setTimeout()

## Definition

The `setTimeout()` method executes a function **only once** after a specified delay.

The delay is measured in **milliseconds (ms).**

```
1000 ms = 1 second
```

---

## Why do we use setTimeout()?

It is used for

- Splash Screens
- Notifications
- Automatic Messages
- Delayed Animations
- Redirecting Pages

---

## Syntax

```javascript
setTimeout(functionName,time);
```

or

```javascript
setTimeout(function(){

// code

},3000);
```

---

## Example 1 - Alert After 3 Seconds

```html
<!DOCTYPE html>
<html>
<head>
<title>setTimeout()</title>
</head>
<body>

<script>

setTimeout(function(){

alert("Welcome Students");

},3000);

</script>

</body>
</html>
```

---

## Example 2 - Change Text After 5 Seconds

```html
<!DOCTYPE html>
<html>
<head>
<title>setTimeout()</title>
</head>
<body>

<h1 id="heading">

Loading...

</h1>

<script>

setTimeout(function(){

document.getElementById("heading").innerHTML="Page Loaded Successfully";

},5000);

</script>

</body>
</html>
```

---

## Important Points

- Executes only once.
- Time is measured in milliseconds.
- Returns a timeout ID.

---

## Interview Questions

1. What is setTimeout()?
2. How many times does it execute?
3. What is the unit of time used?

---

## Assignment

Display "Welcome to JavaScript" after 4 seconds.

---

# setInterval()

## Definition

The `setInterval()` method executes a function **repeatedly** after a specified interval.

Unlike `setTimeout()`, it keeps running until it is stopped.

---

## Why do we use setInterval()?

It is used for

- Digital Clock
- Countdown Timer
- Live Score
- Weather Updates
- Auto Refresh
- Animations

---

## Syntax

```javascript
setInterval(functionName,time);
```

---

## Example 1 - Show Alert Every 5 Seconds

```html
<!DOCTYPE html>
<html>
<head>
<title>setInterval()</title>
</head>
<body>

<script>

setInterval(function(){

alert("JavaScript DOM");

},5000);

</script>

</body>
</html>
```

---

## Example 2 - Digital Clock

```html
<!DOCTYPE html>
<html>
<head>
<title>Digital Clock</title>
</head>
<body>

<h1 id="clock"></h1>

<script>

setInterval(function(){

let d=new Date();

document.getElementById("clock").innerHTML=d.toLocaleTimeString();

},1000);

</script>

</body>
</html>
```

---

## Example 3 - Counter

```html
<!DOCTYPE html>
<html>
<head>
<title>Counter</title>
</head>
<body>

<h1 id="count">

0

</h1>

<script>

let i=0;

setInterval(function(){

i++;

document.getElementById("count").innerHTML=i;

},1000);

</script>

</body>
</html>
```

---

## Important Points

- Executes repeatedly.
- Runs until stopped.
- Time is measured in milliseconds.

---

## Interview Questions

1. What is setInterval()?
2. Difference between setTimeout() and setInterval()?
3. Give two real-world applications of setInterval().

---

## Assignment

Create a counter that increases every second using `setInterval()`.

---

# clearInterval()

## Definition

The `clearInterval()` method is used to **stop** a running `setInterval()`.

---

## Why do we use clearInterval()?

Suppose a counter is increasing every second.

If we want to stop it,

we use `clearInterval()`.

---

## Syntax

```javascript
clearInterval(intervalID);
```

---

## Example 1 - Stop Counter

```html
<!DOCTYPE html>
<html>
<head>
<title>clearInterval()</title>
</head>
<body>

<h1 id="count">

0

</h1>

<button onclick="stopCounter()">

Stop Counter

</button>

<script>

let i=0;

let timer=setInterval(function(){

i++;

document.getElementById("count").innerHTML=i;

},1000);

function stopCounter(){

clearInterval(timer);

}

</script>

</body>
</html>
```

---

## Example 2 - Stop Clock

```html
<!DOCTYPE html>
<html>
<head>
<title>Stop Clock</title>
</head>
<body>

<h1 id="clock"></h1>

<button onclick="stopClock()">

Stop Clock

</button>

<script>

let timer=setInterval(function(){

let d=new Date();

document.getElementById("clock").innerHTML=d.toLocaleTimeString();

},1000);

function stopClock(){

clearInterval(timer);

}

</script>

</body>
</html>
```

---

## Difference Between setTimeout() and setInterval()

| setTimeout() | setInterval() |
|---------------|---------------|
| Executes once | Executes repeatedly |
| Stops automatically | Requires `clearInterval()` to stop |
| Used for delayed execution | Used for repeated execution |

---

## Important Points

- Stops only `setInterval()`.
- Requires the interval ID returned by `setInterval()`.
- Used for timers, counters, and clocks.

---

## Interview Questions

1. What is `clearInterval()`?
2. Why do we need the interval ID?
3. Can `clearInterval()` stop `setTimeout()`?
4. Difference between `clearInterval()` and `setInterval()`?

---

## Assignment

Create a webpage with:

- Start Counter button
- Stop Counter button

The counter should increase every second and stop when the **Stop Counter** button is clicked.

---
# Mini Project 1 - Live Character Counter

## Objective

Count the number of characters entered in a textarea.

---

## Complete Program

```html
<!DOCTYPE html>
<html>
<head>
<title>Character Counter</title>
</head>
<body>

<h2>Character Counter</h2>

<textarea
id="text"
rows="5"
cols="30"
onkeyup="countCharacters()">
</textarea>

<h3>

Characters :
<span id="count">0</span>

</h3>

<script>

function countCharacters(){

let text=document.getElementById("text").value;

document.getElementById("count").innerHTML=text.length;

}

</script>

</body>
</html>
```

---

## Concepts Used

- DOM
- value
- innerHTML
- onkeyup

---

# Mini Project 2 - Digital Clock

## Objective

Display the current time and update it every second.

---

## Complete Program

```html
<!DOCTYPE html>
<html>
<head>
<title>Digital Clock</title>
</head>
<body>

<h1 id="clock"></h1>

<script>

setInterval(function(){

let d=new Date();

document.getElementById("clock").innerHTML=d.toLocaleTimeString();

},1000);

</script>

</body>
</html>
```

---

## Concepts Used

- Date Object
- setInterval()
- innerHTML

---

# Mini Project 3 - Counter Application

## Objective

Increase and decrease a counter using buttons.

---

## Complete Program

```html
<!DOCTYPE html>
<html>
<head>
<title>Counter</title>
</head>
<body>

<h1 id="count">

0

</h1>

<button onclick="increase()">

+

</button>

<button onclick="decrease()">

-

</button>

<script>

let count=0;

function increase(){

count++;

document.getElementById("count").innerHTML=count;

}

function decrease(){

count--;

document.getElementById("count").innerHTML=count;

}

</script>

</body>
</html>
```

---

## Concepts Used

- Variables
- Functions
- DOM
- innerHTML

---

# Mini Project 4 - Password Show / Hide

## Objective

Show and hide the password.

---

## Complete Program

```html
<!DOCTYPE html>
<html>
<head>
<title>Password Toggle</title>
</head>
<body>

<input
type="password"
id="password">

<button onclick="showPassword()">

Show / Hide

</button>

<script>

function showPassword(){

let pass=document.getElementById("password");

if(pass.type=="password"){

pass.type="text";

}

else{

pass.type="password";

}

}

</script>

</body>
</html>
```

---

## Concepts Used

- value
- type
- if else

---

# Mini Project 5 - Light ON / OFF

## Objective

Switch a bulb ON and OFF.

---

## Complete Program

```html
<!DOCTYPE html>
<html>
<head>
<title>Bulb</title>
</head>
<body>

<img
id="bulb"
src="https://www.w3schools.com/js/pic_bulboff.gif">

<br><br>

<button onclick="lightOn()">

ON

</button>

<button onclick="lightOff()">

OFF

</button>

<script>

function lightOn(){

document.getElementById("bulb").src="https://www.w3schools.com/js/pic_bulbon.gif";

}

function lightOff(){

document.getElementById("bulb").src="https://www.w3schools.com/js/pic_bulboff.gif";

}

</script>

</body>
</html>
```

---

## Concepts Used

- getElementById()
- src
- Event Handling

---

# Mini Project 6 - Random Background Color

## Objective

Generate a random background color whenever the button is clicked.

---

## Complete Program

```html
<!DOCTYPE html>
<html>
<head>
<title>Random Color</title>
</head>
<body>

<button onclick="randomColor()">

Generate Color

</button>

<script>

function randomColor(){

let colors=[

"red",
"blue",
"green",
"yellow",
"orange",
"pink",
"purple"

];

let random=Math.floor(Math.random()*colors.length);

document.body.style.backgroundColor=colors[random];

}

</script>

</body>
</html>
```

---

## Concepts Used

- Arrays
- Math.random()
- Math.floor()
- style

---

# Mini Project 7 - Simple Calculator

## Objective

Perform Addition of two numbers.

---

## Complete Program

```html
<!DOCTYPE html>
<html>
<head>
<title>Calculator</title>
</head>
<body>

<input
type="number"
id="num1"
placeholder="First Number">

<br><br>

<input
type="number"
id="num2"
placeholder="Second Number">

<br><br>

<button onclick="add()">

Add

</button>

<h2 id="result"></h2>

<script>

function add(){

let a=parseInt(document.getElementById("num1").value);

let b=parseInt(document.getElementById("num2").value);

document.getElementById("result").innerHTML="Result : "+(a+b);

}

</script>

</body>
</html>
```

---

## Concepts Used

- value
- parseInt()
- innerHTML

---

# Mini Project 8 - Image Changer

## Objective

Change images when the button is clicked.

---

## Complete Program

```html
<!DOCTYPE html>
<html>
<head>
<title>Image Changer</title>
</head>
<body>

<img
id="photo"
src="https://picsum.photos/250">

<br><br>

<button onclick="changeImage()">

Change Image

</button>

<script>

function changeImage(){

document.getElementById("photo").src="https://picsum.photos/251";

}

</script>

</body>
</html>
```

---

## Concepts Used

- src
- getElementById()

---

# Frequently Asked Interview Questions

## Basic Level

1. What is JavaScript?
2. What is DOM?
3. What is the full form of DOM?
4. What is the difference between HTML and DOM?
5. What is the Window Object?
6. What is the Document Object?
7. What is a Node?
8. What is the DOM Tree?

---

## DOM Methods

9. What is `getElementById()`?
10. Difference between `getElementById()` and `querySelector()`?
11. Difference between `querySelector()` and `querySelectorAll()`?
12. What does `getElementsByClassName()` return?
13. What does `getElementsByTagName()` return?

---

## DOM Properties

14. Difference between `innerHTML` and `innerText`?
15. Difference between `innerText` and `textContent`?
16. What is the `style` property?
17. What is the `value` property?

---

## DOM Attributes

18. What is `setAttribute()`?
19. What is `getAttribute()`?
20. What is `removeAttribute()`?

---

## DOM Classes

21. Difference between:

- `classList.add()`
- `classList.remove()`
- `classList.toggle()`

---

## DOM Manipulation

22. What is `createElement()`?
23. What is `appendChild()`?
24. Difference between `appendChild()` and `replaceChild()`?
25. What is `remove()`?

---

## Events

26. What is an Event?
27. Difference between `onclick` and `addEventListener()`?
28. Name different Mouse Events.
29. Name different Keyboard Events.
30. What is `event.key`?
31. What is `preventDefault()`?

---

## Timers

32. Difference between `setTimeout()` and `setInterval()`?
33. What is `clearInterval()`?

---

# Practice Assignments

### Assignment 1

Create a webpage that changes the heading color when a button is clicked.

---

### Assignment 2

Create a Dark Mode toggle using `classList.toggle()`.

---

### Assignment 3

Create a webpage where pressing:

- A → Apple
- B → Ball
- C → Cat

is displayed on the screen.

---

### Assignment 4

Create a Registration Form and validate that all fields are filled before submitting.

---

### Assignment 5

Create a Digital Clock using `setInterval()`.

---

### Assignment 6

Create a Live Character Counter.

---

### Assignment 7

Create an Image Gallery where clicking **Next** changes the image.

---

### Assignment 8

Create a Simple To-Do List using:

- createElement()
- appendChild()
- remove()

---
