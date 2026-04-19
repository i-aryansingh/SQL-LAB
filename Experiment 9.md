# DBMS Lab – Experiment 9

## Aim  
To perform Subqueries on EMPLOYEE and DEPARTMENT tables.

---

## Problem Statement  
Perform the following queries using EMPLOYEE and DEPARTMENT tables.

---

# Question No 1: Display the name of employee who earns highest salary

### Query
```sql
SELECT ename FROM employee WHERE sal=(SELECT MAX(sal) FROM employee);
```

### Output
```text
+-------+
| ename |
+-------+
| KING  |
+-------+
1 row in set (0.00 sec)
```

---

# Question No 2: Display employee number and name of clerk earning highest salary

### Query
```sql
SELECT empno,ename FROM employee WHERE job='CLERK' AND sal=(SELECT MAX(sal) FROM employee WHERE job='CLERK');
```

### Output
```text
+-------+--------+
| empno | ename  |
+-------+--------+
|  7934 | MILLER |
+-------+--------+
1 row in set (0.00 sec)
```

---

# Question No 3: Display names of salesman earning more than highest clerk salary

### Query
```sql
SELECT ename FROM employee WHERE job='SALESMAN' AND sal>(SELECT MAX(sal) FROM employee WHERE job='CLERK');
```

### Output
```text
+--------+
| ename  |
+--------+
| ALLEN  |
| TURNER |
+--------+
2 rows in set (0.00 sec)
```

---

# Question No 4: Display clerks earning more than JAMES and less than SCOTT

### Query
```sql
SELECT ename FROM employee WHERE job='CLERK' AND sal>(SELECT sal FROM employee WHERE ename='JAMES') AND sal<(SELECT sal FROM employee WHERE ename='SCOTT');
```

### Output
```text
+--------+
| ename  |
+--------+
| ADAMS  |
| MILLER |
+--------+
2 rows in set (0.00 sec)
```

---

# Question No 5: Display employees earning more than JAMES or more than SCOTT

### Query
```sql
SELECT ename FROM employee WHERE sal>(SELECT sal FROM employee WHERE ename='JAMES') OR sal>(SELECT sal FROM employee WHERE ename='SCOTT');
```

### Output
```text
+--------+
| ename  |
+--------+
| ALLEN  |
| WARD   |
| JONES  |
| MARTIN |
| BLAKE  |
| CLARK  |
| SCOTT  |
| KING   |
| TURNER |
| ADAMS  |
| FORD   |
| MILLER |
+--------+
12 rows in set (0.00 sec)
```

---

# Question No 6: Display employees earning highest salary in their departments

### Query
```sql
SELECT ename FROM employee e WHERE sal=(SELECT MAX(sal) FROM employee WHERE deptno=e.deptno);
```

### Output
```text
+--------+
| ename  |
+--------+
| BLAKE  |
| SCOTT  |
| KING   |
| MILLER |
+--------+
4 rows in set (0.00 sec)
```

---

# Question No 7: Display employees earning highest salary in their job groups

### Query
```sql
SELECT ename FROM employee e WHERE sal=(SELECT MAX(sal) FROM employee WHERE job=e.job);
```

### Output
```text
+--------+
| ename  |
+--------+
| ALLEN  |
| JONES  |
| SCOTT  |
| KING   |
| FORD   |
| MILLER |
+--------+
6 rows in set (0.00 sec)
```

---

# Question No 8: Display employees working in ACCOUNTING department

### Query
```sql
SELECT ename FROM employee WHERE deptno=(SELECT deptno FROM department WHERE dname='ACCOUNTING');
```

### Output
```text
+--------+
| ename  |
+--------+
| MILLER |
+--------+
1 row in set (0.00 sec)
```

---

# Question No 9: Display employees working in CHICAGO

### Query
```sql
SELECT ename FROM employee WHERE deptno=(SELECT deptno FROM department WHERE location='chicago');
```

### Output
```text
+-------+
| ename |
+-------+
| SMITH |
| JONES |
| CLARK |
| KING  |
| ADAMS |
| FORD  |
+-------+
6 rows in set (0.00 sec)
```

---

# Question No 10: Display job groups having total salary greater than max salary of managers

### Query
```sql
SELECT job FROM employee GROUP BY job HAVING SUM(sal)>(SELECT MAX(sal) FROM employee WHERE job='MANAGER');
```

### Output
```text
+-----------+
| job       |
+-----------+
| ANALYST   |
| CLERK     |
| MANAGER   |
| PRESIDENT |
| SALESMAN  |
+-----------+
5 rows in set (0.00 sec)
```

---

## Conclusion  
All subqueries were successfully executed using EMPLOYEE and DEPARTMENT tables.
