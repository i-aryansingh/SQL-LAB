# DBMS Lab – Experiment 6

## Aim  
To perform JOIN operations on EMPLOYEE, DEPARTMENT and SALGRADE tables.

---

## Problem Statement  
Perform the following queries using EMPLOYEE, DEPARTMENT and SALGRADE tables.

---

# Question No 1: Display all employees with their department name

### Query
```sql
SELECT e.ename,d.dname FROM employee e JOIN department d ON e.deptno=d.deptno;
```

### Output
```text
+--------+------------+
| ename  | dname      |
+--------+------------+
| MILLER | ACCOUNTING |
| SMITH  | RESEARCH   |
| JONES  | RESEARCH   |
| CLARK  | RESEARCH   |
| KING   | RESEARCH   |
| ADAMS  | RESEARCH   |
| FORD   | RESEARCH   |
| ALLEN  | SALES      |
| WARD   | SALES      |
| MARTIN | SALES      |
| BLAKE  | SALES      |
| TURNER | SALES      |
| JAMES  | SALES      |
| SCOTT  | OPERATIONS |
+--------+------------+
14 rows in set (0.00 sec)
```

---

# Question No 2: Display employees whose manager is JONES

### Query
```sql
SELECT e.ename,m.ename FROM employee e JOIN employee m ON e.mgr=m.empno WHERE m.ename='JONES';
```

### Output
```text
+-------+-------+
| ename | ename |
+-------+-------+
| SCOTT | JONES |
| FORD  | JONES |
+-------+-------+
2 rows in set (0.00 sec)
```

---

# Question No 3: Employee name, job, dept name, manager name and grade

### Query
```sql
SELECT e.ename,e.job,d.dname,m.ename,s.grade FROM employee e JOIN department d ON e.deptno=d.deptno LEFT JOIN employee m ON e.mgr=m.empno JOIN salgrade s ON e.sal BETWEEN s.losal AND s.hisal ORDER BY d.dname;
```

### Output
```text
+--------+-----------+------------+-------+-------+
| ename  | job       | dname      | ename | grade |
+--------+-----------+------------+-------+-------+
| MILLER | CLERK     | ACCOUNTING | CLARK | C     |
| SCOTT  | ANALYST   | OPERATIONS | JONES | E     |
| CLARK  | MANAGER   | RESEARCH   | KING  | D     |
| JONES  | MANAGER   | RESEARCH   | KING  | E     |
| SMITH  | CLERK     | RESEARCH   | FORD  | A     |
| KING   | PRESIDENT | RESEARCH   | NULL  | E     |
| FORD   | ANALYST   | RESEARCH   | JONES | E     |
| ADAMS  | CLERK     | RESEARCH   | SCOTT | B     |
| MARTIN | SALESMAN  | SALES      | BLAKE | B     |
| JAMES  | CLERK     | SALES      | BLAKE | A     |
| ALLEN  | SALESMAN  | SALES      | BLAKE | C     |
| TURNER | SALESMAN  | SALES      | BLAKE | C     |
| BLAKE  | MANAGER   | SALES      | KING  | E     |
| WARD   | SALESMAN  | SALES      | BLAKE | B     |
+--------+-----------+------------+-------+-------+
14 rows in set (0.00 sec)
```

---

# Question No 4: Employees except clerk with grade and department (highest salary first)

### Query
```sql
SELECT e.ename,e.job,s.grade,d.dname FROM employee e JOIN department d ON e.deptno=d.deptno JOIN salgrade s ON e.sal BETWEEN s.losal AND s.hisal WHERE e.job<>'CLERK' ORDER BY e.sal DESC;
```

### Output
```text
+--------+-----------+-------+------------+
| ename  | job       | grade | dname      |
+--------+-----------+-------+------------+
| KING   | PRESIDENT | E     | RESEARCH   |
| SCOTT  | ANALYST   | E     | OPERATIONS |
| FORD   | ANALYST   | E     | RESEARCH   |
| JONES  | MANAGER   | E     | RESEARCH   |
| BLAKE  | MANAGER   | E     | SALES      |
| CLARK  | MANAGER   | D     | RESEARCH   |
| ALLEN  | SALESMAN  | C     | SALES      |
| TURNER | SALESMAN  | C     | SALES      |
| MARTIN | SALESMAN  | B     | SALES      |
| WARD   | SALESMAN  | B     | SALES      |
+--------+-----------+-------+------------+
10 rows in set (0.00 sec)
```

---

# Question No 5: Employee name, job and manager (including no manager)

### Query
```sql
SELECT e.ename,e.job,IFNULL(m.ename,'NO MANAGER') FROM employee e LEFT JOIN employee m ON e.mgr=m.empno;
```

### Output
```text
14 rows in set (0.00 sec)
```

---

# Question No 6: Employees earning 36000 per year or not clerks

### Query
```sql
SELECT e.ename,e.job,e.sal*12,e.deptno,d.dname,s.grade FROM employee e JOIN department d ON e.deptno=d.deptno JOIN salgrade s ON e.sal BETWEEN s.losal AND s.hisal WHERE e.sal*12>=36000 OR e.job<>'CLERK';
```

### Output
```text
10 rows in set (0.00 sec)
```

---

# Question No 7: Employees earning 30000 per year and not clerks

### Query
```sql
SELECT e.ename,e.job,e.sal*12,e.deptno,d.dname,s.grade FROM employee e JOIN department d ON e.deptno=d.deptno JOIN salgrade s ON e.sal BETWEEN s.losal AND s.hisal WHERE e.sal*12>=30000 AND e.job<>'CLERK';
```

### Output
```text
6 rows in set (0.00 sec)
```

---

# Question No 8: Employee and manager name and number

### Query
```sql
SELECT e.ename,e.empno,IFNULL(m.ename,'NO MANAGER'),IFNULL(m.empno,'') FROM employee e LEFT JOIN employee m ON e.mgr=m.empno;
```

### Output
```text
14 rows in set (0.00 sec)
```

---

# Question No 9: Department name, department number and total salary

### Query
```sql
SELECT d.dname,d.deptno,SUM(e.sal) FROM employee e JOIN department d ON e.deptno=d.deptno GROUP BY d.deptno,d.dname;
```

### Output
```text
+------------+--------+------------+
| dname      | deptno | SUM(e.sal) |
+------------+--------+------------+
| ACCOUNTING | 10     | 1430       |
| RESEARCH   | 20     | 16858      |
| SALES      | 30     | 9780       |
| OPERATIONS | 40     | 3300       |
+------------+--------+------------+
4 rows in set (0.00 sec)
```

---

# Question No 10: Employee number, name and department location

### Query
```sql
SELECT e.empno,e.ename,d.location FROM employee e JOIN department d ON e.deptno=d.deptno;
```

### Output
```text
14 rows in set (0.00 sec)
```

---

# Question No 11: Employee name and department name

### Query
```sql
SELECT e.ename,d.dname FROM employee e JOIN department d ON e.deptno=d.deptno;
```

### Output
```text
14 rows in set (0.00 sec)
```

---

## Conclusion  
All JOIN operations were successfully executed using EMPLOYEE, DEPARTMENT and SALGRADE tables.
