# Task 1 & 2: Basic Aggregations (Rounded to whole numbers)
SQL
SELECT ROUND(MAX(SAL)) AS "Maximum",
       ROUND(MIN(SAL)) AS "Minimum",
       ROUND(SUM(SAL)) AS "Sum",
       ROUND(AVG(SAL)) AS "Average"
FROM EMP;
# Task 3: Aggregations by Job Type
SQL
SELECT JOB,
       ROUND(MAX(SAL)) AS "Maximum",
       ROUND(MIN(SAL)) AS "Minimum",
       ROUND(SUM(SAL)) AS "Sum",
       ROUND(AVG(SAL)) AS "Average"
FROM EMP
GROUP BY JOB;
# Task 4: Count of headcount per Job Type
SQL
SELECT JOB, COUNT(*) AS "Number of People"
FROM EMP
GROUP BY JOB;
# Task 5: Count of unique Managers
SQL
SELECT COUNT(DISTINCT MGR) AS "Number of Managers"
FROM EMP;
# Task 6: Difference between highest and lowest salaries
SQL
SELECT MAX(SAL) - MIN(SAL) AS "DIFFERENCE"
FROM EMP;
# Task 7: Lowest paid employee per manager (Filtered and Sorted)
SQL
SELECT MGR, MIN(SAL)
FROM EMP
WHERE MGR IS NOT NULL
GROUP BY MGR
HAVING MIN(SAL) > 2000
ORDER BY MIN(SAL) DESC;
# Task 8: Matrix/Pivot headcount report by Hire Years
SQL
SELECT COUNT(*) AS "TOTAL EMPLOYEES",
       COUNT(DECODE(TO_CHAR(HIREDATE, 'YYYY'), '1980', 1)) AS "HIRED IN 1980",
       COUNT(DECODE(TO_CHAR(HIREDATE, 'YYYY'), '1981', 1)) AS "HIRED IN 1981",
       COUNT(DECODE(TO_CHAR(HIREDATE, 'YYYY'), '1982', 1)) AS "HIRED IN 1982"
FROM EMP;