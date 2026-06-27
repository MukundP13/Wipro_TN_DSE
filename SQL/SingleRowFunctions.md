# Task 1: Display current date
SQL
SELECT SYSDATE AS "Date" 
FROM DUAL;
# Task 2: Salary increased by 15.5% (Whole number)
SQL
SELECT EMPNO, ENAME, SAL, ROUND(SAL * 1.155) AS "New Salary"
FROM EMP;
# Task 3: Calculate the salary increase
SQL
SELECT EMPNO, ENAME, SAL, ROUND(SAL * 1.155) AS "New Salary",
       ROUND(SAL * 1.155) - SAL AS "Increase"
FROM EMP;
# Task 4: Capitalize first letter, length check for J, A, M names
SQL
SELECT INITCAP(ENAME) AS "Employee Name", LENGTH(ENAME) AS "Name Length"
FROM EMP
WHERE ENAME LIKE 'J%' OR ENAME LIKE 'A%' OR ENAME LIKE 'M%'
ORDER BY ENAME;
# Task 5: Prompt for starting letter
SQL
SELECT INITCAP(ENAME) AS "Employee Name", LENGTH(ENAME) AS "Name Length"
FROM EMP
WHERE ENAME LIKE '&starting_letter%'
ORDER BY ENAME;
# Task 6: Length of employment in months (Rounded up)
SQL
SELECT ENAME, CEIL(MONTHS_BETWEEN(SYSDATE, HIREDATE)) AS "MONTHS_WORKED"
FROM EMP
ORDER BY "MONTHS_WORKED";
# Task 7: Text formatting template (Dream Salaries)
SQL
SELECT ENAME || ' earns monthly but wants ' || TO_CHAR(SAL * 3) AS "Dream Salaries"
FROM EMP;
# Task 8: Left-pad salary with '$' to 15 characters
SQL
SELECT ENAME, LPAD(TO_CHAR(SAL), 15, '$') AS "SALARY"
FROM EMP;
# Task 9: Six-month review date (First Monday after 6 months) formatted
SQL
SELECT ENAME, HIREDATE, 
       TO_CHAR(NEXT_DAY(ADD_MONTHS(HIREDATE, 6), 'MONDAY'), 'Day, "the" Ddspth "of" Month, YYYY') AS "REVIEW"
FROM EMP;
# Task 10: Hire day of the week (Starting with Monday)
SQL
SELECT ENAME, HIREDATE, TO_CHAR(HIREDATE, 'Day') AS "DAY"
FROM EMP
ORDER BY TO_CHAR(HIREDATE - 1, 'D');
# Task 11: Handle null commission values with text
SQL
SELECT ENAME, NVL(TO_CHAR(COMM), 'No Commission') AS "COMM"
FROM EMP;
# Task 12: Salary represented by asterisks ($1000 = *)
SQL
SELECT RPAD(SUBSTR(ENAME, 1, 8), 8) || ' ' || RPAD('*', FLOOR(SAL/1000), '*') AS "EMPLOYEES_AND_THEIR_SALARIES"
FROM EMP
ORDER BY SAL DESC;
# Task 13: Job grading using DECODE
SQL
SELECT ENAME, JOB,
       DECODE(JOB, 'PRESIDENT', 'A',
                   'MANAGER',   'B',
                   'SALESMAN',  'C',
                   'CLERK',     'D',
                                'Unknown') AS "GRADE"
FROM EMP;
# Task 14: Job grading using CASE
SQL
SELECT ENAME, JOB,
       CASE JOB
            WHEN 'PRESIDENT' THEN 'A'
            WHEN 'MANAGER'   THEN 'B'
            WHEN 'SALESMAN'  THEN 'C'
            WHEN 'CLERK'     THEN 'D'
            ELSE 'Unknown'
       END AS "GRADE"
FROM EMP;