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

