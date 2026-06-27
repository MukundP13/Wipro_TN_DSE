#Task 1
Current Form: 2NF

Reason: It's in 2NF because the primary key is just a single column (EMPNO), so there are no partial dependencies. But it violates 3NF because there is a transitive dependency: EMPNO determines DEPTNO, and DEPTNO determines DNAME and LOC.

Solution (Split into 2 tables):

EMP (EMPNO [PK], ENAME, SAL, DEPTNO [FK])

DEPT (DEPTNO [PK], DNAME, LOC)

#Task 2
Current Form: 2NF

Reason: Same as above, the key is just ROLLNO so it's automatically in 2NF. It fails 3NF because MARKS determines GRADE, which is a non-key attribute depending on another non-key attribute. Also, EXAM details shouldn't be spammed for every student.

Solution (Split into 3 tables):

STUDENT_INFO (ROLLNO [PK], NAME, AGE)

STUDENT_MARKS (ROLLNO [PK], EXAM [PK], MARKS)

GRADING (MARKS [PK], GRADE)

#Task 3
Problem: This table violates 2NF because it has a composite primary key (EMPNO, PROJECT_NO) and there is a partial dependency. CUSTOMERNAME only depends on PROJECT_NO, not the whole key. This causes redundant data and anomalies (like if you delete an employee, you accidentally lose the project's customer info too).

Solution (Split into 2 tables):

EMP_PROJECT (EMPNO [PK], PROJECT_NO [PK], NO_OF_DAYS)

PROJECT_CUSTOMERS (PROJECT_NO [PK], CUSTOMERNAME)