# HTML Complete Notes - Day 1

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

# Day 1 Practice Tasks

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

# Day 1 Interview Questions

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

# Day 1 Summary

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

**End of Day 1 Notes**
# HTML Complete Notes - Day 2

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

# Day 2 Summary

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
        content="Advanced HTML Day 2">

    <meta
        name="keywords"
        content="HTML,CSS,JavaScript">

    <meta
        name="author"
        content="Maheswaram">

    <title>Advanced HTML - Day 2</title>

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
            Complete Day 2 Demonstration File
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

        Day 2 Advanced HTML Completed

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


# Day 3 - HTML Semantic Tags & CSS Basics

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
# Day 3 - HTML Semantic Tags & CSS Basics

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
    <title>Day 3 HTML & CSS Concepts</title>

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

Create a complete Student Portfolio Website using all concepts learned in Day 1, Day 2, and Day 3.

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
# Day 3 Summary

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
