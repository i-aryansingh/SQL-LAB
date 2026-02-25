# DBMS Lab – Experiment 3

## Aim  
To perform various conditional and sorting queries on the EMPLOYEE table.

---

## Problem Statement  
Perform the following queries using the EMPLOYEE table.

---

# Step 1: List all employees and jobs in Department 30 in descending order by salary

### Query
```sql
SELECT ename, job, sal FROM employee WHERE deptno = 30 ORDER BY sal DESC;
```

### Output
```text
+--------+----------+------+
| ename  | job      | sal  |
+--------+----------+------+
| BLAKE  | MANAGER  | 3135 |
| ALLEN  | SALESMAN | 1600 |
| TURNER | SALESMAN | 1500 |
| WARD   | SALESMAN | 1250 |
| MARTIN | SALESMAN | 1250 |
| JAMES  | CLERK    | 1045 |
+--------+----------+------+
6 rows in set (0.00 sec)
```

---

# Step 2: List job and Department Number of employees whose name are five letters long begin with “A” and end with “N”

### Query
```sql
SELECT job, deptno FROM employee WHERE ename LIKE 'A___N';
```

### Output
```text
Empty set (0.00 sec)
```

---

# Step 3: Display the name of employees whose name start with alphabet S

### Query
```sql
SELECT ename FROM employee WHERE ename LIKE 'S%';
```

### Output
```text
+--------+
| ename  |
+--------+
| SMITH  |
| SCOTT  |
+--------+
2 rows in set (0.00 sec)
```

---

# Step 4: Display the names of employees whose name ends with alphabet S

### Query
```sql
SELECT ename FROM employee WHERE ename LIKE '%S';
```

### Output
```text
+-------+
| ename |
+-------+
| JONES |
| ADAMS |
| JAMES |
+-------+
3 rows in set (0.00 sec)
```

---

# Step 5: Display employees working in department number 10 or 20 or 40 or employees working as clerks, salesman or analyst

### Query
```sql
SELECT ename FROM employee WHERE deptno IN (10,20,40) OR job IN ('CLERK','SALESMAN','ANALYST');
```

### Output
```text
+--------+
| ename  |
+--------+
| SMITH  |
| ALLEN  |
| WARD   |
| JONES  |
| MARTIN |
| CLARK  |
| SCOTT  |
| KING   |
| TURNER |
| ADAMS  |
| JAMES  |
| FORD   |
| MILLER |
+--------+
13 rows in set (0.00 sec)
```

---

# Step 6: Display employee number and names for employees who earn commission

### Query
```sql
SELECT empno, ename FROM employee WHERE comm IS NOT NULL;
```

### Output
```text
+-------+--------+
| empno | ename  |
+-------+--------+
|  7499 | ALLEN  |
|  7521 | WARD   |
|  7654 | MARTIN |
|  7844 | TURNER |
+-------+--------+
4 rows in set (0.00 sec)
```

---

# Step 7: Display employee number and total salary for each employee

### Query
```sql
SELECT empno, sal + IFNULL(comm,0) AS total_salary FROM employee;
```

### Output
```text
+-------+--------------+
| empno | total_salary |
+-------+--------------+
|  7369 |          880 |
|  7499 |         1900 |
|  7521 |         1750 |
|  7566 |         3273 |
|  7654 |         2650 |
|  7698 |         3135 |
|  7782 |         2695 |
|  7788 |         3300 |
|  7839 |         5500 |
|  7844 |         1500 |
|  7876 |         1210 |
|  7900 |         1045 |
|  7902 |         3300 |
|  7934 |         1430 |
+-------+--------------+
14 rows in set (0.00 sec)
```

---

# Step 8: Display employee number and annual salary for each employee

### Query
```sql
SELECT empno, sal*12 AS annual_salary FROM employee;
```

### Output
```text
+-------+---------------+
| empno | annual_salary |
+-------+---------------+
|  7369 |         10560 |
|  7499 |         19200 |
|  7521 |         15000 |
|  7566 |         39276 |
|  7654 |         15000 |
|  7698 |         37620 |
|  7782 |         32340 |
|  7788 |         39600 |
|  7839 |         66000 |
|  7844 |         18000 |
|  7876 |         14520 |
|  7900 |         12540 |
|  7902 |         39600 |
|  7934 |         17160 |
+-------+---------------+
14 rows in set (0.00 sec)
```

---

# Step 9: Display the names of all employees working as clerks and drawing a salary more than 3000

### Query
```sql
SELECT ename FROM employee WHERE job = 'CLERK' AND sal > 3000;
```

### Output
```text
Empty set (0.00 sec)
```

---

# Step 10: Display the names of employees working as clerk, salesman or analyst and drawing a salary more than 3000

### Query
```sql
SELECT ename FROM employee WHERE job IN ('CLERK','SALESMAN','ANALYST') AND sal > 3000;
```

### Output
```text
+--------+
| ename  |
+--------+
| SCOTT  |
| FORD   |
+--------+
2 rows in set (0.00 sec)
```

---

## Conclusion  
All conditional and sorting queries were successfully executed on the EMPLOYEE table with correct outputs.
