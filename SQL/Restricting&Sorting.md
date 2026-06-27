Task 1: Sort by column position (Commission earners)
SQL
SELECT ENAME, SAL, COMM 
FROM EMP 
WHERE COMM IS NOT NULL AND COMM > 0
ORDER BY 2 DESC, 3 DESC;
Task 2: Unique job codes
SQL
SELECT DISTINCT JOB 
FROM EMP;
Task 3: Descriptive column headings (Aliases)
SQL
SELECT EMPNO AS "Emp #", ENAME AS "Employee", JOB AS "Job", HIREDATE AS "Hire Date"
FROM EMP;
Task 4: Concatenate Name and Job
SQL
SELECT ENAME || ', ' || JOB AS "Employee and Title"
FROM EMP;
Task 5: Comma-separated output column
SQL
SELECT ENAME || ',' || JOB || ',' || HIREDATE || ',' || MGR AS "THE_OUTPUT"
FROM EMP;
Task 6: Filter for SCOTT or TURNER
SQL
SELECT ENAME, JOB, HIREDATE
FROM EMP
WHERE ENAME IN ('SCOTT', 'TURNER')
ORDER BY HIREDATE ASC;
Task 7: Dept 20 or 30 sorted alphabetically
SQL
SELECT ENAME, DEPTNO
FROM EMP
WHERE DEPTNO IN (20, 30)
ORDER BY ENAME ASC;
Task 8: Filter by Dept, Salary range, and add Aliases
SQL
SELECT ENAME AS "Employee", SAL AS "Monthly Salary"
FROM EMP
WHERE SAL BETWEEN 2000 AND 3000
  AND DEPTNO IN (20, 30);
Task 9: Hired in 1981
SQL
SELECT ENAME, HIREDATE
FROM EMP
WHERE HIREDATE LIKE '%81' 
   OR HIREDATE BETWEEN '01-JAN-1981' AND '31-DEC-1981';
Task 10: Input Prompt for Salary
SQL
SELECT ENAME, SAL
FROM EMP
WHERE SAL > &enter_salary_amount;
Task 11: No Manager (Top level)
SQL
SELECT ENAME, JOB
FROM EMP
WHERE MGR IS NULL;
Task 12: Prompt for Manager ID and Sort Column
SQL
SELECT EMPNO, ENAME, SAL, DEPTNO
FROM EMP
WHERE MGR = &enter_mgr_id
ORDER BY &select_sort_column_position_or_name;
Task 13: Prompt for Manager and Sorting (Duplicate requirement)
SQL
SELECT EMPNO, ENAME, SAL, DEPTNO
FROM EMP
WHERE MGR = &enter_mgr_id
ORDER BY &sort_column;
Task 14: Third letter is 'A'
SQL
SELECT ENAME
FROM EMP
WHERE ENAME LIKE '__A%';
Task 15: Name contains both 'A' and 'S'
SQL
SELECT ENAME
FROM EMP
WHERE ENAME LIKE '%A%' AND ENAME LIKE '%S%';
Task 16: Specific Job and specific Salary matches
SQL
SELECT ENAME, JOB, SAL
FROM EMP
WHERE JOB = 'CLERK' 
  AND SAL IN (800, 950, 1300);