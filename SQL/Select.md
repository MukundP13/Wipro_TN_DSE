#Task 1: Structure & Contents of DEPT Table

SQL
-- To see the table structure (columns and data types)
DESC DEPT;

-- To see all records/contents
SELECT * FROM DEPT;


#Task 2: Structure & Contents of EMP Table

SQL
-- To see the table structure
DESC EMP;

-- To see all records/contents
SELECT * FROM EMP;


#Task 3: Display Ename and Deptno for Empno 7788

SQL
SELECT ENAME, DEPTNO 
FROM EMP 
WHERE EMPNO = 7788;