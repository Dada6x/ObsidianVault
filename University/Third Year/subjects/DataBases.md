مادة قواعد المعطيات سنة 3 فصل تاني 


What is an Data Base ??
هي نظام يستخدم لتنظيم البيانات وتخزينها بطريقة مرتبة داخل جداول كل جدول يحتوي على معلومات معينة وله خصائص خاصة به وترتبط الجداول ببعضها البعض من خالل عالقات تكمن أهميتها في أنها تسهل حفظ البيانات ومعالجتها في مكان واحد وبشكل منظم وسهل الاستخدام

ولتعريف قاعدة بيانات توجد ثلاث مستويات .

#  1. conceptual Level مفاهيمي

descibe the general skeletonization of the DB without going deep into 'how to store the Data' its focuses on **Types of Data and the ReleationShips betwwen them**
![[Pasted image 20250710173826.png]]


# 2. Logical Level 

detailed Description of the DB contains the names of the tables , fieldsn and types of the Data , the primery Keyes the Foregin Keys , But **it dosent give a damn about how to store the shitty Data**

![[Pasted image 20250710174203.png]]

# 3. Physical LEvel 
it deal with "How to Store Data on the HardDrive " so its only give its shits on the `indexs `
 `partitioning`
 ![[Pasted image 20250710174603.png]]


# ~={red}ERD=~
***stands for the entity Relatinship Diagram.***
to make an ERD for any System we need to follow theses steps :
- Understanding the requirements of the system
- define the Main entities
- define the attributes of each entite
- define the releationship between entities
- Drawing the shit out of it 
## RelationShips in ERD
### One to One
Each person has one passport.
#### One to Many
One teacher teaches many students.
### Many to Many
Students can enroll in many courses, and each course can have many students.






# محاضرات العملي 

```
 -- 1. Select all students who live in London, Paris, or Berlin
SELECT * FROM Students WHERE city IN ('London', 'Paris', 'Berlin');

-- 2. Select students whose name starts with 'A'
SELECT * FROM Students WHERE student_name LIKE 'A%';

-- 3. Select students aged between 18 and 25
SELECT * FROM Students WHERE age BETWEEN 18 AND 25;

-- 4. Select students who do not have an email (email is NULL)
SELECT * FROM Students WHERE email IS NULL;

-- 5. Count number of students in each city
SELECT city, COUNT(*) AS student_count FROM Students GROUP BY city;

-- 6. Show only cities with more than 3 students
SELECT city, COUNT(*) AS student_count FROM Students GROUP BY city HAVING COUNT(*) > 3;

-- 7. Select student names and their grades by joining Students and Grades tables
SELECT Students.student_name, Grades.student_grade
FROM Students
JOIN Grades ON Students.id = Grades.id;

-- Alternative join syntax
SELECT Students.student_name, Grades.student_grade
FROM Students, Grades
WHERE Students.id = Grades.id;

-- 8. Calculate average grade per student
SELECT Students.student_name, AVG(Grades.student_grade) AS avg_grade
FROM Students
JOIN Grades ON Students.id = Grades.id
GROUP BY Students.student_name;

-- 9. Select publishers’ names and total price of all their books
SELECT Publishers.pub_name, SUM(Titles.price) AS totalBookPrices
FROM Publishers
JOIN Titles ON Publishers.pub_id = Titles.pub_id
GROUP BY Publishers.pub_name;

-- 10. Select book titles and types starting with Q, W, or E, ordered alphabetically
SELECT title, type
FROM Titles
WHERE title LIKE 'Q%' OR title LIKE 'W%' OR title LIKE 'E%'
ORDER BY title ASC;

-- 11. Concatenate first and last name as full name (make sure these columns exist)
SELECT CONCAT(first_name, ' ', last_name) AS FullName FROM Students;

-- 12. Calculate exact years since hire date for each student
SELECT student_name,
       DATEDIFF(YEAR, hire_date, GETDATE())
       - CASE 
           WHEN MONTH(hire_date) > MONTH(GETDATE())
             OR (MONTH(hire_date) = MONTH(GETDATE()) AND DAY(hire_date) > DAY(GETDATE()))
           THEN 1 ELSE 0
         END AS years_since_hire
FROM Students;

```




# Sub queries 

```
-- 1. Select names of students who have grades greater than 85
SELECT student_name 
FROM Students 
WHERE id IN (
  SELECT id 
  FROM Grades 
  WHERE student_grade > 85
);

-- 2. Select titles of books with price greater than average price
SELECT title
FROM Titles
WHERE price > (
  SELECT AVG(price) FROM Titles
);

-- 3. Select publisher names who have published books priced over 100
SELECT pub_name
FROM Publishers
WHERE pub_id IN (
  SELECT pub_id
  FROM Titles
  WHERE price > 100
);

-- 4. Select students whose grade equals the highest grade
SELECT *
FROM Students
WHERE id IN (
  SELECT id
  FROM Grades
  WHERE student_grade = (
    SELECT MAX(student_grade) FROM Grades
  )
);

-- 5. Select titles where type is the most common book type
SELECT title
FROM Titles
WHERE type = (
  SELECT type
  FROM Titles
  GROUP BY type
  ORDER BY COUNT(*) DESC
  LIMIT 1
);

-- 6. Select student names with grades above average grade
SELECT student_name
FROM Students s
WHERE id IN (
  SELECT id
  FROM Grades
  WHERE student_grade > (
    SELECT AVG(student_grade) FROM Grades
  )
);

```

# JOINS 

```
-- 1. INNER JOIN: Students with grades
SELECT * FROM Students JOIN Grades ON Students.id = Grades.id;

-- 2. LEFT JOIN: All students even without grades
SELECT * FROM Students LEFT JOIN Grades ON Students.id = Grades.id;

-- 3. RIGHT JOIN: All grades even if student missing
SELECT * FROM Students RIGHT JOIN Grades ON Students.id = Grades.id;

-- 4. Students with grade > 90
SELECT student_name
FROM Students
WHERE id IN (
  SELECT id FROM Grades WHERE student_grade > 90
);

-- 5. Book titles and publisher names
SELECT title, pub_name
FROM Titles
JOIN Publishers ON Titles.pub_id = Publishers.pub_id;

-- 6. All publishers and the books they published (even if none)
SELECT pub_name, title
FROM Publishers
LEFT JOIN Titles ON Publishers.pub_id = Titles.pub_id;

-- 7. All possible combinations of student names and book titles
SELECT student_name, title
FROM Students
CROSS JOIN Titles;

```

# DDL
Data Definition Language

|Command|Purpose|
|---|---|
|`CREATE`|Create tables, views, databases|
|`ALTER`|Modify existing structure|
|`DROP`|Delete tables or databases|
|`TRUNCATE`|Delete all data, keep structure|

# DML
Data Manipulation Language

| Command  | Purpose              |
| -------- | -------------------- |
| `SELECT` | Retrieve data        |
| `INSERT` | Add new data         |
| `UPDATE` | Modify existing data |
| `DELETE` | Remove data          |

# TCL 
Transition Control Language a

| Command                       | Purpose                    |
| ----------------------------- | -------------------------- |
| `BEGIN` / `START TRANSACTION` | Start a transaction        |
| `COMMIT`                      | Save all changes           |
| `ROLLBACK`                    | Undo changes               |
| `SAVEPOINT`                   | Set a point to rollback to |

# EDR 
```
Students
---------
student_id (PK)
name
email

Courses
--------
course_id (PK)
title
credits

Enrollments
-------------
enrollment_id (PK)
student_id (FK)
course_id (FK)
enrolled_on

```


