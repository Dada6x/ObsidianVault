hello this is from the GitHub site 
i think its working 
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