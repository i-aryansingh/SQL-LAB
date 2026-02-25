# DBMS Lab – Experiment 2

## Aim  
To retrieve data from the EMPLOYEE table using SELECT queries.

---

## Problem Statement  
Perform the following queries using the EMPLOYEE table.

---

# Step 1: List all distinct jobs

### Query
```sql
SELECT DISTINCT job FROM employee;
```

### Output
```text
+-----------+
| job       |
+-----------+
| CLERK     |
| SALESMAN  |
| MANAGER   |
| ANALYST   |
| PRESIDENT |
+-----------+
5 rows in set (0.00 sec)
```

---

# Step 2: List all information about employees in Department 30

### Query
```sql
SELECT * FROM employee WHERE deptno = 30;
```

### Output
```text
+-------+--------+----------+------+------------+------+------+--------+
| empno | ename  | job      | mgr  | hiredate   | sal  | comm | deptno |
+-------+--------+----------+------+------------+------+------+--------+
|  7499 | ALLEN  | SALESMAN | 7698 | 1981-02-20 | 1600 |  300 |     30 |
|  7521 | WARD   | SALESMAN | 7698 | 1981-02-22 | 1250 |  500 |     30 |
|  7654 | MARTIN | SALESMAN | 7698 | 1981-09-28 | 1250 | 1400 |     30 |
|  7698 | BLAKE  | MANAGER  | 7839 | 1981-05-01 | 3135 | NULL |     30 |
|  7844 | TURNER | SALESMAN | 7698 | 1981-09-08 | 1500 |    0 |     30 |
|  7900 | JAMES  | CLERK    | 7698 | 1981-12-03 | 1045 | NULL |     30 |
+-------+--------+----------+------+------------+------+------+--------+
6 rows in set (0.00 sec)
```

---

# Step 3: Find department numbers greater than 20

### Query
```sql
SELECT DISTINCT deptno FROM employee WHERE deptno > 20;
```

### Output
```text
+--------+
| deptno |
+--------+
|     30 |
|     40 |
+--------+
2 rows in set (0.00 sec)
```

---

# Step 4: Managers and Clerks in Department 30

### Query
```sql
SELECT * FROM employee
WHERE deptno = 30
AND (job = 'MANAGER' OR job = 'CLERK');
```

### Output
```text
+-------+--------+---------+------+------------+------+------+--------+
| empno | ename  | job     | mgr  | hiredate   | sal  | comm | deptno |
+-------+--------+---------+------+------------+------+------+--------+
|  7698 | BLAKE  | MANAGER | 7839 | 1981-05-01 | 3135 | NULL |     30 |
|  7900 | JAMES  | CLERK   | 7698 | 1981-12-03 | 1045 | NULL |     30 |
+-------+--------+---------+------+------------+------+------+--------+
2 rows in set (0.00 sec)
```

---

# Step 5: List name, employee number and department of all clerks

### Query
```sql
SELECT ename, empno, deptno FROM employee WHERE job = 'CLERK';
```

### Output
```text
+--------+-------+--------+
| ename  | empno | deptno |
+--------+-------+--------+
| SMITH  |  7369 |     20 |
| ADAMS  |  7876 |     20 |
| JAMES  |  7900 |     30 |
| MILLER |  7934 |     10 |
+--------+-------+--------+
4 rows in set (0.00 sec)
```

---

# Step 6: Managers not in Department 30

### Query
```sql
SELECT * FROM employee
WHERE job = 'MANAGER'
AND deptno <> 30;
```

### Output
```text
+-------+--------+---------+------+------------+------+------+--------+
| empno | ename  | job     | mgr  | hiredate   | sal  | comm | deptno |
+-------+--------+---------+------+------------+------+------+--------+
|  7566 | JONES  | MANAGER | 7839 | 1981-04-02 | 3273 | NULL |     20 |
|  7782 | CLARK  | MANAGER | 7839 | 1981-06-09 | 2695 | NULL |     20 |
+-------+--------+---------+------+------------+------+------+--------+
2 rows in set (0.00 sec)
```

---

# Step 7: Employees in Department 10 who are not Managers or Clerks

### Query
```sql
SELECT * FROM employee
WHERE deptno = 10
AND job NOT IN ('MANAGER','CLERK');
```

### Output
```text
Empty set (0.00 sec)
```

---

# Step 8: Employees earning between 1200 and 1400

### Query
```sql
SELECT ename, job, sal
FROM employee
WHERE sal BETWEEN 1200 AND 1400;
```

### Output
```text
+--------+----------+------+
| ename  | job      | sal  |
+--------+----------+------+
| WARD   | SALESMAN | 1250 |
| MARTIN | SALESMAN | 1250 |
| ADAMS  | CLERK    | 1210 |
| MILLER | CLERK    | 1430 |
+--------+----------+------+
4 rows in set (0.00 sec)
```

---

# Step 9: Clerks, Analysts or Salesman

### Query
```sql
SELECT ename, deptno
FROM employee
WHERE job IN ('CLERK','ANALYST','SALESMAN');
```

### Output
```text
+--------+--------+
| ename  | deptno |
+--------+--------+
| SMITH  |     20 |
| ALLEN  |     30 |
| WARD   |     30 |
| MARTIN |     30 |
| SCOTT  |     40 |
| TURNER |     30 |
| ADAMS  |     20 |
| JAMES  |     30 |
| FORD   |     20 |
| MILLER |     10 |
+--------+--------+
10 rows in set (0.00 sec)
```

---

# Step 10: Employees whose names begin with M

### Query
```sql
SELECT ename, deptno
FROM employee
WHERE ename LIKE 'M%';
```

### Output
```text
+--------+--------+
| ename  | deptno |
+--------+--------+
| MARTIN |     30 |
| MILLER |     10 |
+--------+--------+
2 rows in set (0.00 sec)
```

---

## Conclusion  
All retrieval queries were successfully executed on the EMPLOYEE table with correct outputs.
