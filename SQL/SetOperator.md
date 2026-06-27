Task 1: Matrix/Pivot Query for Job Salary by Department
SQL
SELECT JOB,
       SUM(DECODE(DEPTNO, 10, SAL, 0)) AS "Dept 10 Sal",
       SUM(DECODE(DEPTNO, 20, SAL, 0)) AS "Dept 20 Sal",
       SUM(DECODE(DEPTNO, 30, SAL, 0)) AS "Dept 30 Sal",
       SUM(SAL) AS "Total Sal"
FROM EMP
WHERE DEPTNO IN (10, 20, 30)
GROUP BY JOB;
Task 2: Union Aggregate Summaries (Dept, Job, and Grand Total)
SQL
SELECT TO_CHAR(DEPTNO) AS "Group By Element", 'DEPARTMENT' AS "Type", SUM(SAL) AS "Total Salary"
FROM EMP
GROUP BY DEPTNO

UNION ALL

SELECT JOB, 'JOB TYPE', SUM(SAL)
FROM EMP
GROUP BY JOB

UNION ALL

SELECT 'ALL EMPLOYEES', 'GRAND TOTAL', SUM(SAL)
FROM EMP;
Task 3: Order Rows across Departments using Set Operator
SQL
SELECT JOB, DEPTNO, 1 AS sort_order FROM EMP WHERE DEPTNO = 20
UNION ALL
SELECT JOB, DEPTNO, 2 FROM EMP WHERE DEPTNO = 10
UNION ALL
SELECT JOB, DEPTNO, 3 FROM EMP WHERE DEPTNO = 30
ORDER BY sort_order;