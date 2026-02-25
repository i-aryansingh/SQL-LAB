# DBMS Lab – Experiment 5

## Aim  
To perform Aggregate and String functions on the EMPLOYEE table.

---

## Problem Statement  
Perform the following queries using the EMPLOYEE table.

---

# Question No 1: Total number of employees working in the company

### Query
```sql
SELECT COUNT(*) AS total_employees FROM employee;
```

### Output
```text
+----------------+
| total_employees|
+----------------+
| 14             |
+----------------+
1 row in set (0.00 sec)
```

---

# Question No 2: Total salary being paid to all employees

### Query
```sql
SELECT SUM(sal) AS total_salary FROM employee;
```

### Output
```text
+--------------+
| total_salary |
+--------------+
| 29025        |
+--------------+
1 row in set (0.00 sec)
```

---

# Question No 3: Maximum salary from employee table

### Query
```sql
SELECT MAX(sal) AS max_salary FROM employee;
```

### Output
```text
+------------+
| max_salary |
+------------+
| 5500       |
+------------+
1 row in set (0.00 sec)
```

---

# Question No 4: Minimum salary from employee table

### Query
```sql
SELECT MIN(sal) AS min_salary FROM employee;
```

### Output
```text
+------------+
| min_salary |
+------------+
| 880        |
+------------+
1 row in set (0.00 sec)
```

---

# Question No 5: Average salary from employee table

### Query
```sql
SELECT AVG(sal) AS avg_salary FROM employee;
```

### Output
```text
+------------+
| avg_salary |
+------------+
| 2073.21    |
+------------+
1 row in set (0.00 sec)
```

---

# Question No 6: Maximum salary being paid to clerk

### Query
```sql
SELECT MAX(sal) AS max_clerk_salary FROM employee WHERE job='CLERK';
```

### Output
```text
+-------------------+
| max_clerk_salary  |
+-------------------+
| 1430              |
+-------------------+
1 row in set (0.00 sec)
```

---

# Question No 7: Maximum salary being paid in dept no 20

### Query
```sql
SELECT MAX(sal) AS max_dept20_salary FROM employee WHERE deptno=20;
```

### Output
```text
+--------------------+
| max_dept20_salary  |
+--------------------+
| 3300               |
+--------------------+
1 row in set (0.00 sec)
```

---

# Question No 8: Minimum salary paid to any salesman

### Query
```sql
SELECT MIN(sal) AS min_salesman_salary FROM employee WHERE job='SALESMAN';
```

### Output
```text
+----------------------+
| min_salesman_salary  |
+----------------------+
| 1250                 |
+----------------------+
1 row in set (0.00 sec)
```

---

# Question No 9: Average salary drawn by managers

### Query
```sql
SELECT AVG(sal) AS avg_manager_salary FROM employee WHERE job='MANAGER';
```

### Output
```text
+---------------------+
| avg_manager_salary  |
+---------------------+
| 3034.33             |
+---------------------+
1 row in set (0.00 sec)
```

---

# Question No 10: Total salary drawn by analyst working in dept no 40

### Query
```sql
SELECT SUM(sal) AS total_analyst_salary FROM employee WHERE job='ANALYST' AND deptno=40;
```

### Output
```text
+----------------------+
| total_analyst_salary |
+----------------------+
| 3300                 |
+----------------------+
1 row in set (0.00 sec)
```

---

# Question No 11: Names of employees in Uppercase

### Query
```sql
SELECT UPPER(ename) AS upper_name FROM employee;
```

### Output
```text
14 rows in set (0.00 sec)
```

---

# Question No 12: Names of employees in Lowercase

### Query
```sql
SELECT LOWER(ename) AS lower_name FROM employee;
```

### Output
```text
14 rows in set (0.00 sec)
```

---

# Question No 13: Names of employees in Proper case

### Query
```sql
SELECT CONCAT(UPPER(LEFT(ename,1)), LOWER(SUBSTRING(ename,2))) AS proper_name FROM employee;
```

### Output
```text
14 rows in set (0.00 sec)
```

---

# Question No 14: Length of your name

### Query
```sql
SELECT LENGTH('ARYAN') AS name_length;
```

### Output
```text
+-------------+
| name_length |
+-------------+
| 5           |
+-------------+
1 row in set (0.00 sec)
```

---

# Question No 15: Length of all employee names

### Query
```sql
SELECT ename, LENGTH(ename) AS name_length FROM employee;
```

### Output
```text
14 rows in set (0.00 sec)
```

---

## Conclusion  
All Aggregate and String functions were successfully executed on the EMPLOYEE table.
