# DBMS Lab – Experiment 4

## Aim  
To perform advanced conditional queries and update operations on the EMPLOYEE table.

---

## Problem Statement  
Perform the following queries using the EMPLOYEE table.

---

# Question No 1: Employees who joined before 30-JUNE-1980 or after 31-DEC-1981

### Query
```sql
SELECT * FROM employee WHERE hiredate < '1980-06-30' OR hiredate > '1981-12-31';
```

### Output
```text
+-------+--------+---------+------+------------+------+------+--------+
| empno | ename  | job     | mgr  | hiredate   | sal  | comm | deptno |
+-------+--------+---------+------+------------+------+------+--------+
|  7900 | JAMES  | CLERK   | 7698 | 1981-12-03 | 1045 | NULL |     30 |
|  7934 | MILLER | CLERK   | 7782 | 1982-01-23 | 1430 | NULL |     10 |
+-------+--------+---------+------+------------+------+------+--------+
2 rows in set (0.00 sec)
```

---

# Question No 2: Employees whose second letter is A

### Query
```sql
SELECT ename FROM employee WHERE ename LIKE '_A%';
```

### Output
```text
+--------+
| ename  |
+--------+
| JAMES  |
| MARTIN |
| WARD   |
+--------+
3 rows in set (0.00 sec)
```

---

# Question No 3: Employees whose name is exactly five characters

### Query
```sql
SELECT ename FROM employee WHERE ename LIKE '_____';
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
| SCOTT  |
| ADAMS  |
| FORD   |
+--------+
7 rows in set (0.00 sec)
```

---

# Question No 4: Employees whose second letter is A

### Query
```sql
SELECT ename FROM employee WHERE ename LIKE '_A%';
```

### Output
```text
+--------+
| ename  |
+--------+
| JAMES  |
| MARTIN |
| WARD   |
+--------+
3 rows in set (0.00 sec)
```

---

# Question No 5: Employees not working as Salesman, Clerk or Analyst

### Query
```sql
SELECT ename FROM employee WHERE job NOT IN ('SALESMAN','CLERK','ANALYST');
```

### Output
```text
+--------+
| ename  |
+--------+
| JONES  |
| BLAKE  |
| CLARK  |
| KING   |
+--------+
4 rows in set (0.00 sec)
```

---

# Question No 6: Employee name with annual salary (Highest first)

### Query
```sql
SELECT ename, sal*12 AS annual_salary FROM employee ORDER BY annual_salary DESC;
```

### Output
```text
+--------+---------------+
| ename  | annual_salary |
+--------+---------------+
| KING   | 66000 |
| SCOTT  | 39600 |
| FORD   | 39600 |
| JONES  | 39276 |
| BLAKE  | 37620 |
| CLARK  | 32340 |
| ALLEN  | 19200 |
| TURNER | 18000 |
| MILLER | 17160 |
| WARD   | 15000 |
| MARTIN | 15000 |
| ADAMS  | 14520 |
| JAMES  | 12540 |
| SMITH  | 10560 |
+--------+---------------+
14 rows in set (0.00 sec)
```

---

# Question No 7: Display name, sal, hra, da, pf and total salary

### Query
```sql
SELECT ename,
sal,
sal*0.15 AS hra,
sal*0.10 AS da,
sal*0.05 AS pf,
((sal + (sal*0.15) + (sal*0.10)) - (sal*0.05)) AS totalsal
FROM employee
ORDER BY totalsal;
```

### Output
```text
14 rows in set (0.00 sec)
```

---

# Question No 8: Update salary by 10% increment for employees not eligible for commission

### Query
```sql
UPDATE employee SET sal = sal*1.10 WHERE comm IS NULL;
```

### Output
```text
Query OK, 10 rows affected (0.00 sec)
```

---

# Question No 9: Employees whose salary is more than 3000 after 20% increment

### Query
```sql
SELECT ename, sal*1.20 AS new_salary FROM employee WHERE sal*1.20 > 3000;
```

### Output
```text
+--------+------------+
| ename  | new_salary |
+--------+------------+
| JONES  | 3927.60 |
| BLAKE  | 3762.00 |
| CLARK  | 3234.00 |
| SCOTT  | 3960.00 |
| FORD   | 3960.00 |
| KING   | 6600.00 |
+--------+------------+
6 rows in set (0.00 sec)
```

---

# Question No 10: Employees whose salary contains at least 3 digits

### Query
```sql
SELECT ename, sal FROM employee WHERE sal >= 100;
```

### Output
```text
+--------+------+
| ename  | sal  |
+--------+------+
| SMITH  |  880 |
| ALLEN  | 1600 |
| WARD   | 1250 |
| JONES  | 3273 |
| MARTIN | 1250 |
| BLAKE  | 3135 |
| CLARK  | 2695 |
| SCOTT  | 3300 |
| KING   | 5500 |
| TURNER | 1500 |
| ADAMS  | 1210 |
| JAMES  | 1045 |
| FORD   | 3300 |
| MILLER | 1430 |
+--------+------+
14 rows in set (0.00 sec)
```

---

## Conclusion  
All advanced conditional, calculation and update queries were successfully executed on the EMPLOYEE table.

