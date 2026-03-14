# 📘 SQL Complete 5-Day Course
### By Akanksha Kumari | HNB Garhwal University
### GitHub: github.com/Akanksha-Ceris

> **How to use this file:**
> - Open MySQL Workbench side by side with VS Code
> - Read concept → type query in Workbench → write your understanding here
> - Push to GitHub every day after studying!

---

# ⚙️ SETUP GUIDE — Before Day 1
s
## How to Run SQL in MySQL Workbench

**Step 1** — Open MySQL Workbench
**Step 2** — Click on your local connection (usually says `Local instance 3306`)
**Step 3** — A query editor opens — this is where you type SQL
**Step 4** — Type your query
**Step 5** — Press **`Ctrl + Enter`** to run ONE query
**Step 6** — Press **`Ctrl + Shift + Enter`** to run ALL queries
**Step 7** — Results appear at the bottom!

## How to Run SQL in VS Code

**Step 1** — Install extension called **"MySQL"** by cweijan
```
Go to Extensions (Ctrl+Shift+X) → Search "MySQL" → Install
```
**Step 2** — Connect to your database
```
Click database icon on left → Click + → Enter:
Host: 127.0.0.1
Port: 3306
Username: root
Password: (your MySQL password)
```
**Step 3** — Right click your database → New Query
**Step 4** — Type SQL → Press **`Ctrl + Enter`** to run!

## GitHub Setup — Do This Once

Open VS Code Terminal (`Ctrl + backtick`) and type:
```bash
# Configure your identity
git config --global user.name "Akanksha Kumari"
git config --global user.email "akanksha.parmanent@gmail.com"

# Initialize this folder as a git repo
git init

# Add all files
git add .

# First commit
git commit -m "Started SQL Notes"
```

Then on GitHub.com:
1. Click New Repository
2. Name: `SQL-Notes`
3. Click Create
4. Copy the push commands and paste in terminal

**Every day after studying run:**
```bash
git add .
git commit -m "Day 1 complete - Basics and SELECT"
git push
```

---

# 📅 DAY 1 — Database Basics + SELECT + Filtering

## 🤔 What is SQL? (In Simple Words)

SQL = Structured Query Language

Imagine you have a huge notebook with thousands of student records.
Finding one student manually takes forever.
SQL lets you say: *"Give me all students from Delhi with marks above 80"*
And it finds them in milliseconds!

```
Real life = Database
One register = One Table
One row in register = One Record
One column = One Property (name, age, marks)
```

---

## 🛠️ Step 1 — Create Your Practice Database

Type this in MySQL Workbench and press Ctrl+Enter:

```sql
-- Create a new database
CREATE DATABASE sql_practice;

-- Select it to use
USE sql_practice;

-- Confirm you are using it
SELECT DATABASE();
```

**What you should see:** `sql_practice` in the result ✅

---

## 🛠️ Step 2 — Create Your First Table

```sql
CREATE TABLE students (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    age INT,
    city VARCHAR(50),
    marks FLOAT,
    gender VARCHAR(10)
);
```

**Understanding each part:**
```
id INT AUTO_INCREMENT PRIMARY KEY
→ id is a number that increases automatically (1,2,3...)
→ PRIMARY KEY means each id is unique — no duplicates

name VARCHAR(50) NOT NULL
→ VARCHAR = text that can vary in length
→ (50) = maximum 50 characters
→ NOT NULL = cannot be left empty

marks FLOAT
→ FLOAT = decimal numbers like 85.5, 90.0
```

**Check your table was created:**
```sql
DESCRIBE students;
```

---

## 🛠️ Step 3 — Insert Data

```sql
INSERT INTO students (name, age, city, marks, gender)
VALUES
('Akanksha', 21, 'Dehradun', 85.5, 'Female'),
('Priya', 20, 'Delhi', 90.0, 'Female'),
('Rohit', 22, 'Mumbai', 75.0, 'Male'),
('Sneha', 21, 'Dehradun', 88.0, 'Female'),
('Amit', 23, 'Bangalore', 60.5, 'Male'),
('Neha', 20, 'Delhi', 92.0, 'Female'),
('Vikram', 22, 'Chennai', 55.0, 'Male'),
('Pooja', 21, 'Pune', 78.5, 'Female'),
('Rahul', 20, 'Mumbai', 82.0, 'Male'),
('Anjali', 22, 'Delhi', 88.5, 'Female');
```

**Check data was inserted:**
```sql
SELECT * FROM students;
```

---

## 🔍 SELECT — Fetching Data

```sql
-- Get everything (all rows, all columns)
SELECT * FROM students;

-- Get specific columns only
SELECT name, marks FROM students;
SELECT name, age, city FROM students;

-- Give columns a nickname (alias)
SELECT name AS student_name, marks AS score FROM students;
```

---

## 🔍 WHERE — Filtering Data

```sql
-- Equal to
SELECT * FROM students WHERE city = 'Delhi';

-- Not equal
SELECT * FROM students WHERE city != 'Delhi';

-- Greater than
SELECT * FROM students WHERE marks > 80;

-- Less than
SELECT * FROM students WHERE marks < 70;

-- Greater than or equal
SELECT * FROM students WHERE marks >= 85;

-- Two conditions with AND
SELECT * FROM students WHERE city = 'Delhi' AND marks > 85;

-- Two conditions with OR
SELECT * FROM students WHERE city = 'Delhi' OR city = 'Mumbai';

-- BETWEEN (both values included)
SELECT * FROM students WHERE marks BETWEEN 75 AND 90;

-- IN (multiple values at once)
SELECT * FROM students WHERE city IN ('Delhi', 'Mumbai', 'Pune');

-- NOT IN
SELECT * FROM students WHERE city NOT IN ('Delhi', 'Mumbai');

-- LIKE (pattern search)
SELECT * FROM students WHERE name LIKE 'A%';    -- starts with A
SELECT * FROM students WHERE name LIKE '%a';    -- ends with a
SELECT * FROM students WHERE name LIKE '%oh%';  -- contains oh
```

---

## 📊 ORDER BY and LIMIT

```sql
-- Sort by marks highest to lowest
SELECT * FROM students ORDER BY marks DESC;

-- Sort by marks lowest to highest
SELECT * FROM students ORDER BY marks ASC;

-- Sort by name alphabetically
SELECT * FROM students ORDER BY name ASC;

-- Get only top 3 students
SELECT * FROM students ORDER BY marks DESC LIMIT 3;

-- Get only first 5 rows
SELECT * FROM students LIMIT 5;
```

---

## ✏️ Day 1 Practice — Try These Yourself

```sql
-- Practice 1: Get all female students
-- YOUR ANSWER:

-- Practice 2: Get top 5 students by marks
-- YOUR ANSWER:

-- Practice 3: Get students from Delhi with marks above 85
-- YOUR ANSWER:

-- Practice 4: Get students whose name starts with 'P'
-- YOUR ANSWER:

-- Practice 5: Get students aged between 20 and 22
-- YOUR ANSWER:
```

## 📝 My Day 1 Notes (Write your understanding here)
```
What I understood today:


Commands I found difficult:


My doubts:


```

---

# 📅 DAY 2 — Aggregate Functions + GROUP BY

## 🤔 What are Aggregate Functions?

Normal SELECT gives you many rows.
Aggregate functions give you ONE answer from many rows.

```
Think of it like this:
You have marks of 10 students.
AVG(marks) gives you ONE number — the average.
MAX(marks) gives you ONE number — the highest.
```

---

## 🔢 The 5 Most Important Aggregate Functions

```sql
-- COUNT: how many rows?
SELECT COUNT(*) FROM students;
SELECT COUNT(*) FROM students WHERE city = 'Delhi';
SELECT COUNT(*) AS total_students FROM students;

-- SUM: add all values
SELECT SUM(marks) FROM students;
SELECT SUM(marks) AS total_marks FROM students;

-- AVG: average value
SELECT AVG(marks) FROM students;
SELECT AVG(marks) AS average_marks FROM students;

-- MAX: highest value
SELECT MAX(marks) FROM students;
SELECT MAX(marks) AS highest_marks FROM students;

-- MIN: lowest value
SELECT MIN(marks) FROM students;
SELECT MIN(marks) AS lowest_marks FROM students;

-- All together in one query!
SELECT
    COUNT(*) AS total_students,
    ROUND(AVG(marks), 2) AS average_marks,
    MAX(marks) AS highest,
    MIN(marks) AS lowest,
    SUM(marks) AS total
FROM students;
```

---

## 📦 GROUP BY — Calculate Per Group

```sql
-- How many students in each city?
SELECT city, COUNT(*) AS student_count
FROM students
GROUP BY city;

-- Average marks per city
SELECT city, ROUND(AVG(marks), 2) AS avg_marks
FROM students
GROUP BY city;

-- Highest marks per city
SELECT city, MAX(marks) AS highest_marks
FROM students
GROUP BY city;

-- Multiple calculations per city
SELECT
    city,
    COUNT(*) AS students,
    ROUND(AVG(marks), 2) AS avg_marks,
    MAX(marks) AS highest
FROM students
GROUP BY city
ORDER BY avg_marks DESC;

-- Group by gender
SELECT gender, COUNT(*) AS count, AVG(marks) AS avg_marks
FROM students
GROUP BY gender;
```

---

## 🔍 HAVING — Filter Groups

```
Remember this rule:
WHERE  → filters rows BEFORE grouping
HAVING → filters groups AFTER grouping
```

```sql
-- Cities with more than 1 student
SELECT city, COUNT(*) AS count
FROM students
GROUP BY city
HAVING count > 1;

-- Cities where average marks is above 80
SELECT city, ROUND(AVG(marks), 2) AS avg_marks
FROM students
GROUP BY city
HAVING avg_marks > 80;

-- Cities with more than 1 student AND average above 80
SELECT city, COUNT(*) AS count, AVG(marks) AS avg_marks
FROM students
GROUP BY city
HAVING count > 1 AND avg_marks > 80;
```

---

## 🔢 DISTINCT — Remove Duplicates

```sql
-- See all unique cities (no repeats)
SELECT DISTINCT city FROM students;

-- Count unique cities
SELECT COUNT(DISTINCT city) AS unique_cities FROM students;

-- Unique genders
SELECT DISTINCT gender FROM students;
```

---

## ✏️ Day 2 Practice

```sql
-- Practice 1: Find average marks of female students
-- YOUR ANSWER:

-- Practice 2: Find city with highest number of students
-- YOUR ANSWER:

-- Practice 3: Find cities where average marks is above 85
-- YOUR ANSWER:

-- Practice 4: Count male and female students separately
-- YOUR ANSWER:

-- Practice 5: Find total marks scored by all Delhi students
-- YOUR ANSWER:
```

## 📝 My Day 2 Notes
```
What I understood today:


Difference between WHERE and HAVING in my own words:


My doubts:


```

---

# 📅 DAY 3 — JOINS (Most Important Topic!)

## 🤔 What is a JOIN? (Super Simple)

```
Imagine two registers:
Register 1 = Students (name, age, course_id)
Register 2 = Courses (id, course_name, duration)

JOIN connects them using the matching id.
So you can see: student name + their course name together!
```

Without JOIN — you need to look at two tables separately.
With JOIN — you get combined information in one result!

---

## 🛠️ Setup — Create Tables for JOIN Practice

```sql
-- Create courses table
CREATE TABLE courses (
    id INT AUTO_INCREMENT PRIMARY KEY,
    course_name VARCHAR(50),
    duration_months INT,
    fees INT
);

-- Insert courses
INSERT INTO courses (course_name, duration_months, fees)
VALUES
('Python Programming', 3, 5000),
('Machine Learning', 6, 15000),
('Web Development', 4, 8000),
('Data Science', 5, 12000),
('Deep Learning', 4, 10000);

-- Add course_id column to students
ALTER TABLE students ADD course_id INT;

-- Assign courses to some students
UPDATE students SET course_id = 1 WHERE name = 'Akanksha';
UPDATE students SET course_id = 2 WHERE name = 'Priya';
UPDATE students SET course_id = 3 WHERE name = 'Rohit';
UPDATE students SET course_id = 2 WHERE name = 'Sneha';
UPDATE students SET course_id = 4 WHERE name = 'Neha';
UPDATE students SET course_id = 1 WHERE name = 'Anjali';
-- Note: Amit, Vikram, Pooja, Rahul have no course (NULL)

-- Check your data
SELECT * FROM students;
SELECT * FROM courses;
```

---

## 🔗 INNER JOIN — Only Matching Rows

```
INNER JOIN shows rows that exist in BOTH tables.
Students without a course = NOT shown.
Courses with no students = NOT shown.
```

```sql
-- Basic INNER JOIN
SELECT students.name, students.marks, courses.course_name
FROM students
INNER JOIN courses ON students.course_id = courses.id;

-- With alias (shorter code)
SELECT s.name, s.marks, c.course_name, c.duration_months
FROM students s
INNER JOIN courses c ON s.course_id = c.id;

-- With WHERE filter
SELECT s.name, s.marks, c.course_name
FROM students s
INNER JOIN courses c ON s.course_id = c.id
WHERE s.marks > 80;

-- With ORDER BY
SELECT s.name, s.marks, c.course_name
FROM students s
INNER JOIN courses c ON s.course_id = c.id
ORDER BY s.marks DESC;
```

---

## 🔗 LEFT JOIN — All Left Table Rows

```
LEFT JOIN shows ALL rows from left table.
If no match in right table → shows NULL.
All students shown, even those without a course.
```

```sql
-- All students with their course (NULL if no course)
SELECT s.name, s.marks, c.course_name
FROM students s
LEFT JOIN courses c ON s.course_id = c.id;

-- Find students who have NO course enrolled
SELECT s.name, s.city
FROM students s
LEFT JOIN courses c ON s.course_id = c.id
WHERE c.id IS NULL;
```

---

## 🔗 RIGHT JOIN — All Right Table Rows

```
RIGHT JOIN shows ALL rows from right table.
All courses shown, even those with no students.
```

```sql
-- All courses with their students
SELECT s.name, c.course_name, c.fees
FROM students s
RIGHT JOIN courses c ON s.course_id = c.id;

-- Find courses with no students enrolled
SELECT c.course_name
FROM students s
RIGHT JOIN courses c ON s.course_id = c.id
WHERE s.id IS NULL;
```

---

## 📊 JOIN with Aggregate Functions

```sql
-- How many students per course?
SELECT
    c.course_name,
    COUNT(s.id) AS student_count,
    ROUND(AVG(s.marks), 2) AS avg_marks
FROM courses c
LEFT JOIN students s ON c.id = s.course_id
GROUP BY c.course_name
ORDER BY student_count DESC;

-- Most popular course
SELECT c.course_name, COUNT(s.id) AS enrolled
FROM courses c
LEFT JOIN students s ON c.id = s.course_id
GROUP BY c.course_name
ORDER BY enrolled DESC
LIMIT 1;
```

---

## 🔗 Joining More Than Two Tables

```sql
-- Create a third table
CREATE TABLE teachers (
    id INT AUTO_INCREMENT PRIMARY KEY,
    teacher_name VARCHAR(50),
    course_id INT
);

INSERT INTO teachers (teacher_name, course_id)
VALUES
('Dr. Sharma', 1),
('Dr. Gupta', 2),
('Dr. Singh', 3),
('Dr. Verma', 4);

-- Join all 3 tables
SELECT s.name, c.course_name, t.teacher_name
FROM students s
INNER JOIN courses c ON s.course_id = c.id
INNER JOIN teachers t ON c.id = t.course_id
ORDER BY s.name;
```

---

## ✏️ Day 3 Practice

```sql
-- Practice 1: Get all students with their course names (LEFT JOIN)
-- YOUR ANSWER:

-- Practice 2: Find students doing Machine Learning
-- YOUR ANSWER:

-- Practice 3: Count students per course including empty courses
-- YOUR ANSWER:

-- Practice 4: Find students with marks > 85 and their course name
-- YOUR ANSWER:

-- Practice 5: Find which course has the highest average student marks
-- YOUR ANSWER:
```

## 📝 My Day 3 Notes
```
INNER JOIN in my own words:


LEFT JOIN in my own words:


Difference between LEFT and INNER JOIN:


My doubts:


```

---

# 📅 DAY 4 — Subqueries + UPDATE + DELETE + Functions

## 🔍 Subqueries — Query Inside a Query

```
A subquery is a SELECT inside another SELECT.
The inner query runs first.
Its result is used by the outer query.

Think of it like:
"Find students with marks above [the average marks]"
First calculate average → then find students above it.
```

```sql
-- Find students with marks above average
SELECT name, marks
FROM students
WHERE marks > (SELECT AVG(marks) FROM students);

-- Find students in same city as Akanksha
SELECT name, city
FROM students
WHERE city = (SELECT city FROM students WHERE name = 'Akanksha');

-- Find students doing the most expensive course
SELECT s.name, c.course_name, c.fees
FROM students s
INNER JOIN courses c ON s.course_id = c.id
WHERE c.fees = (SELECT MAX(fees) FROM courses);

-- Find students with marks above average AND from Delhi
SELECT name, marks, city
FROM students
WHERE marks > (SELECT AVG(marks) FROM students)
AND city = 'Delhi';

-- Subquery in FROM clause
SELECT city, avg_marks
FROM (
    SELECT city, ROUND(AVG(marks), 2) AS avg_marks
    FROM students
    GROUP BY city
) AS city_averages
WHERE avg_marks > 80;
```

---

## ✏️ UPDATE — Change Existing Data

```sql
-- Update one student marks
UPDATE students SET marks = 95.0 WHERE name = 'Akanksha';

-- Update multiple columns at once
UPDATE students SET city = 'Haridwar', age = 22 WHERE name = 'Rohit';

-- Give 5 bonus marks to all Delhi students
UPDATE students SET marks = marks + 5 WHERE city = 'Delhi';

-- Update based on condition
UPDATE students SET marks = marks * 1.1 WHERE marks < 70;

-- Always verify after update
SELECT * FROM students WHERE name = 'Akanksha';
SELECT * FROM students WHERE city = 'Delhi';
```

---

## 🗑️ DELETE — Remove Data

```sql
-- Delete one specific row
DELETE FROM students WHERE name = 'Vikram';

-- Delete based on condition
DELETE FROM students WHERE marks < 60;

-- Delete from specific city
DELETE FROM students WHERE city = 'Chennai';

-- Verify deletion
SELECT * FROM students;

-- TRUNCATE: delete ALL rows but keep table structure
-- TRUNCATE TABLE students;  ← careful with this!

-- DROP: delete the whole table permanently
-- DROP TABLE students;  ← very careful with this!
```

---

## 🔤 String Functions

```sql
-- UPPER and LOWER
SELECT UPPER(name) FROM students;
SELECT LOWER(name) FROM students;

-- LENGTH
SELECT name, LENGTH(name) AS name_length FROM students;

-- CONCAT: join strings
SELECT CONCAT(name, ' is from ', city) AS info FROM students;
SELECT CONCAT(name, ' scored ', marks, ' marks') AS result FROM students;

-- SUBSTRING: get part of string
SELECT SUBSTRING(name, 1, 3) FROM students;  -- first 3 characters

-- TRIM: remove spaces
SELECT TRIM('  hello  ');

-- REPLACE: replace text
SELECT REPLACE(city, 'Delhi', 'New Delhi') FROM students;

-- INSTR: find position of character
SELECT INSTR(name, 'a') FROM students;
```

---

## 🔢 Number Functions

```sql
-- ROUND: round to decimal places
SELECT name, ROUND(marks, 0) FROM students;
SELECT ROUND(85.567, 2);  -- returns 85.57

-- CEIL: always round up
SELECT CEIL(85.1);   -- returns 86
SELECT CEIL(85.9);   -- returns 86

-- FLOOR: always round down
SELECT FLOOR(85.1);  -- returns 85
SELECT FLOOR(85.9);  -- returns 85

-- ABS: absolute value (remove negative)
SELECT ABS(-50);  -- returns 50

-- MOD: remainder after division
SELECT MOD(10, 3);  -- returns 1

-- POWER: raise to power
SELECT POWER(2, 10);  -- returns 1024
```

---

## 📅 Date Functions

```sql
-- Current date and time
SELECT NOW();       -- 2024-03-14 10:30:00
SELECT CURDATE();   -- 2024-03-14
SELECT CURTIME();   -- 10:30:00

-- Extract parts
SELECT YEAR(NOW());    -- 2024
SELECT MONTH(NOW());   -- 3
SELECT DAY(NOW());     -- 14
SELECT HOUR(NOW());    -- 10

-- Add or subtract days
SELECT DATE_ADD(CURDATE(), INTERVAL 7 DAY);   -- 7 days later
SELECT DATE_SUB(CURDATE(), INTERVAL 30 DAY);  -- 30 days ago

-- Difference between dates
SELECT DATEDIFF('2024-12-31', CURDATE()) AS days_until_new_year;
```

---

## ✏️ Day 4 Practice

```sql
-- Practice 1: Find students with marks above average
-- YOUR ANSWER:

-- Practice 2: Update all Mumbai students — give 10 bonus marks
-- YOUR ANSWER:

-- Practice 3: Delete students with marks below 65
-- YOUR ANSWER:

-- Practice 4: Show all names in uppercase with their city
-- YOUR ANSWER:

-- Practice 5: Show student name and how many characters in their name
-- YOUR ANSWER:
```

## 📝 My Day 4 Notes
```
Subquery in my own words:


Difference between DELETE and TRUNCATE and DROP:


My doubts:


```

---

# 📅 DAY 5 — Advanced SQL + Real World Project

## 🪟 Window Functions

```
Window functions are like GROUP BY but they
DO NOT collapse rows into one.
Every row keeps its own data PLUS gets extra calculated info.
```

```sql
-- RANK: rank students by marks
SELECT
    name,
    marks,
    RANK() OVER (ORDER BY marks DESC) AS rank_position
FROM students;

-- ROW_NUMBER: simple serial number
SELECT
    ROW_NUMBER() OVER (ORDER BY marks DESC) AS row_num,
    name,
    marks
FROM students;

-- DENSE_RANK: no gaps in ranking
SELECT
    name,
    marks,
    DENSE_RANK() OVER (ORDER BY marks DESC) AS dense_rank
FROM students;

-- Rank WITHIN each city
SELECT
    name,
    city,
    marks,
    RANK() OVER (PARTITION BY city ORDER BY marks DESC) AS city_rank
FROM students;

-- Running total (cumulative sum)
SELECT
    name,
    marks,
    SUM(marks) OVER (ORDER BY id) AS running_total
FROM students;
```

---

## 📋 Views — Save a Query as Virtual Table

```sql
-- Create a view for top students
CREATE VIEW top_students AS
SELECT name, city, marks
FROM students
WHERE marks > 80
ORDER BY marks DESC;

-- Use the view exactly like a table
SELECT * FROM top_students;

-- Filter the view
SELECT * FROM top_students WHERE city = 'Delhi';

-- Update a view
CREATE OR REPLACE VIEW top_students AS
SELECT name, city, marks, gender
FROM students
WHERE marks > 85;

-- Drop view
DROP VIEW top_students;
```

---

## 🔒 Stored Procedures — Save SQL as a Function

```sql
-- Create a procedure
DELIMITER //
CREATE PROCEDURE get_city_students(IN city_name VARCHAR(50))
BEGIN
    SELECT name, marks, city
    FROM students
    WHERE city = city_name
    ORDER BY marks DESC;
END //
DELIMITER ;

-- Call the procedure
CALL get_city_students('Delhi');
CALL get_city_students('Mumbai');

-- Procedure with multiple parameters
DELIMITER //
CREATE PROCEDURE get_students_by_marks(IN min_marks FLOAT, IN max_marks FLOAT)
BEGIN
    SELECT name, marks, city
    FROM students
    WHERE marks BETWEEN min_marks AND max_marks
    ORDER BY marks DESC;
END //
DELIMITER ;

CALL get_students_by_marks(75, 90);
```

---

## 🔑 Indexes — Make Queries Faster

```sql
-- Create index (speeds up searches on that column)
CREATE INDEX idx_city ON students(city);
CREATE INDEX idx_marks ON students(marks);

-- Show all indexes on a table
SHOW INDEX FROM students;

-- Drop index
DROP INDEX idx_city ON students;
```

---

## 🎯 Day 5 — Complete Real World Project

Build a complete **Library Management System** database!

```sql
-- Create fresh database
CREATE DATABASE library_management;
USE library_management;

-- Table 1: Books
CREATE TABLE books (
    id INT AUTO_INCREMENT PRIMARY KEY,
    title VARCHAR(100) NOT NULL,
    author VARCHAR(50),
    genre VARCHAR(30),
    price DECIMAL(8,2),
    quantity INT DEFAULT 1,
    published_year INT
);

-- Table 2: Members
CREATE TABLE members (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    email VARCHAR(100) UNIQUE,
    city VARCHAR(50),
    join_date DATE DEFAULT (CURDATE()),
    membership_type VARCHAR(20) DEFAULT 'Basic'
);

-- Table 3: Borrowings
CREATE TABLE borrowings (
    id INT AUTO_INCREMENT PRIMARY KEY,
    member_id INT,
    book_id INT,
    borrow_date DATE DEFAULT (CURDATE()),
    return_date DATE,
    returned BOOLEAN DEFAULT FALSE,
    FOREIGN KEY (member_id) REFERENCES members(id),
    FOREIGN KEY (book_id) REFERENCES books(id)
);

-- Insert Books
INSERT INTO books (title, author, genre, price, quantity, published_year)
VALUES
('Python Crash Course', 'Eric Matthes', 'Technology', 499, 3, 2019),
('Atomic Habits', 'James Clear', 'Self-Help', 399, 5, 2018),
('Deep Learning', 'Ian Goodfellow', 'Technology', 899, 2, 2016),
('The Alchemist', 'Paulo Coelho', 'Fiction', 299, 4, 1988),
('Clean Code', 'Robert Martin', 'Technology', 599, 2, 2008),
('Ikigai', 'Hector Garcia', 'Self-Help', 350, 6, 2016),
('Harry Potter', 'J.K. Rowling', 'Fiction', 450, 3, 1997);

-- Insert Members
INSERT INTO members (name, email, city, membership_type)
VALUES
('Akanksha Kumari', 'akanksha@gmail.com', 'Dehradun', 'Premium'),
('Priya Singh', 'priya@gmail.com', 'Delhi', 'Basic'),
('Rohit Sharma', 'rohit@gmail.com', 'Mumbai', 'Basic'),
('Sneha Gupta', 'sneha@gmail.com', 'Dehradun', 'Premium'),
('Amit Kumar', 'amit@gmail.com', 'Bangalore', 'Basic');

-- Insert Borrowings
INSERT INTO borrowings (member_id, book_id, borrow_date, return_date, returned)
VALUES
(1, 1, '2024-01-10', '2024-01-24', TRUE),
(1, 3, '2024-02-01', NULL, FALSE),
(2, 2, '2024-01-15', '2024-01-29', TRUE),
(3, 4, '2024-02-10', NULL, FALSE),
(4, 1, '2024-02-05', '2024-02-19', TRUE),
(5, 5, '2024-02-15', NULL, FALSE),
(2, 3, '2024-03-01', NULL, FALSE);

-- ================================
-- NOW WRITE THESE QUERIES:
-- ================================

-- Q1: Show all books currently borrowed (not returned)
SELECT m.name AS member, b.title AS book, br.borrow_date
FROM borrowings br
JOIN members m ON br.member_id = m.id
JOIN books b ON br.book_id = b.id
WHERE br.returned = FALSE;

-- Q2: Most borrowed book
SELECT b.title, COUNT(br.id) AS times_borrowed
FROM books b
LEFT JOIN borrowings br ON b.id = br.book_id
GROUP BY b.title
ORDER BY times_borrowed DESC
LIMIT 1;

-- Q3: Members who have never borrowed a book
SELECT m.name, m.email
FROM members m
LEFT JOIN borrowings br ON m.id = br.member_id
WHERE br.id IS NULL;

-- Q4: Average books borrowed per member
SELECT ROUND(COUNT(*) / COUNT(DISTINCT member_id), 2) AS avg_books_per_member
FROM borrowings;

-- Q5: Books by genre with count and avg price
SELECT genre, COUNT(*) AS book_count, ROUND(AVG(price), 2) AS avg_price
FROM books
GROUP BY genre
ORDER BY book_count DESC;

-- Q6: Members with most borrowings
SELECT m.name, COUNT(br.id) AS total_borrowed
FROM members m
LEFT JOIN borrowings br ON m.id = br.member_id
GROUP BY m.name
ORDER BY total_borrowed DESC;
```

---

## ✏️ Day 5 Final Practice Tasks

```sql
-- Task 1: Add 3 more books of your choice
-- Task 2: Add yourself as a member and borrow 2 books
-- Task 3: Find all Technology books sorted by price
-- Task 4: Create a view called 'active_borrowings' for unreturned books
-- Task 5: Find which city has the most library members
```

## 📝 My Day 5 Notes
```
What I understood today:


Most useful thing I learned this week:


Things I want to practice more:


```

---

# 📌 COMPLETE SQL CHEATSHEET

## Database Commands
```sql
CREATE DATABASE name;
USE name;
SHOW DATABASES;
DROP DATABASE name;
```

## Table Commands
```sql
CREATE TABLE name (col1 type, col2 type);
DESCRIBE table_name;
SHOW TABLES;
ALTER TABLE name ADD column_name type;
DROP TABLE name;
```

## CRUD Operations
```sql
INSERT INTO table (col1, col2) VALUES (val1, val2);
SELECT * FROM table;
UPDATE table SET col = val WHERE condition;
DELETE FROM table WHERE condition;
```

## Filtering
```sql
WHERE col = value          -- equal
WHERE col != value         -- not equal
WHERE col > value          -- greater than
WHERE col BETWEEN a AND b  -- range
WHERE col IN (a, b, c)     -- multiple values
WHERE col LIKE 'A%'        -- pattern
WHERE col IS NULL          -- empty values
AND / OR                   -- combine conditions
```

## Sorting and Limiting
```sql
ORDER BY col ASC    -- low to high
ORDER BY col DESC   -- high to low
LIMIT n             -- only n rows
```

## Aggregate Functions
```sql
COUNT(*) -- count rows
SUM(col) -- add all
AVG(col) -- average
MAX(col) -- highest
MIN(col) -- lowest
```

## Grouping
```sql
GROUP BY col          -- group rows
HAVING condition      -- filter groups
DISTINCT              -- unique values
```

## Joins
```sql
INNER JOIN  -- only matching rows
LEFT JOIN   -- all left + matching right
RIGHT JOIN  -- all right + matching left
```

## Advanced
```sql
-- Subquery
SELECT * FROM table WHERE col = (SELECT MAX(col) FROM table);

-- Window Function
RANK() OVER (ORDER BY col DESC)
PARTITION BY col

-- View
CREATE VIEW name AS SELECT ...;

-- Stored Procedure
CREATE PROCEDURE name() BEGIN ... END;
CALL name();
```

---

## 🌐 Best Resources

| Resource | Best For | Link |
|---|---|---|
| W3Schools SQL | Quick reference + try online | w3schools.com/sql |
| SQLZoo | Interactive practice | sqlzoo.net |
| HackerRank SQL | Practice problems | hackerrank.com/domains/sql |
| LeetCode SQL | Interview prep | leetcode.com |
| MySQL Docs | Official reference | dev.mysql.com/doc |

---

## 📤 Push to GitHub — Daily Routine

```bash
# After every study session:
git add .
git commit -m "Day 1 complete - Basics and SELECT"
git push

# Check status anytime
git status

# See your commit history
git log --oneline
```

---

*Notes by Akanksha Kumari | HNB Garhwal University | github.com/Akanksha-Ceris*
