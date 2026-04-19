# DBMS Lab – Experiment 7

## Aim  
To perform miscellaneous SQL queries using EMPLOYEE table.

---

## Problem Statement  
Perform the following queries.

---

# Question No 1: Compute the number of days remaining in this year

### Query
```sql
SELECT DATEDIFF(CONCAT(YEAR(CURDATE()),'-12-31'),CURDATE()) AS remaining_days;
```

### Output
```text
Output will vary depending on current date
```

---

# Question No 2: Highest salary, lowest salary and their difference

### Query
```sql
SELECT MAX(sal) AS max_sal,MIN(sal) AS min_sal,MAX(sal)-MIN(sal) AS difference FROM employee;
```

### Output
```text
+---------+---------+------------+
| max_sal | min_sal | difference |
+---------+---------+------------+
| 5500    | 880     | 4620       |
+---------+---------+------------+
1 row in set (0.00 sec)
```

---

# Question No 3: Employees whose commission is greater than 25% of salary

### Query
```sql
SELECT ename FROM employee WHERE comm>0.25*sal;
```

### Output
```text
+--------+
| ename  |
+--------+
| ALLEN  |
| WARD   |
| MARTIN |
+--------+
3 rows in set (0.00 sec)
```

---

# Question No 4: Display salary in dollar format

### Query
```sql
SELECT ename,CONCAT('$',sal) AS salary FROM employee;
```

### Output
```text
+--------+--------+
| ename  | salary |
+--------+--------+
| SMITH  | $880   |
| ALLEN  | $1600  |
| WARD   | $1250  |
| JONES  | $3273  |
| MARTIN | $1250  |
| BLAKE  | $3135  |
| CLARK  | $2695  |
| SCOTT  | $3300  |
| KING   | $5500  |
| TURNER | $1500  |
| ADAMS  | $1210  |
| JAMES  | $1045  |
| FORD   | $3300  |
| MILLER | $1430  |
+--------+--------+
14 rows in set (0.00 sec)
```

---

# Question No 5: Matrix query for job and salary based on department

### Query
```sql
SELECT job,SUM(CASE WHEN deptno=10 THEN sal END) AS Dept10,SUM(CASE WHEN deptno=20 THEN sal END) AS Dept20,SUM(CASE WHEN deptno=30 THEN sal END) AS Dept30,SUM(sal) AS Total FROM employee GROUP BY job;
```

### Output
```text
+-----------+--------+--------+--------+-------+
| job       | Dept10 | Dept20 | Dept30 | Total |
+-----------+--------+--------+--------+-------+
| CLERK     | 1430   | 2090   | 1045   | 4565  |
| SALESMAN  | NULL   | NULL   | 5600   | 5600  |
| MANAGER   | NULL   | 5968   | 3135   | 9103  |
| ANALYST   | NULL   | 6600   | NULL   | 6600  |
| PRESIDENT | NULL   | 5500   | NULL   | 5500  |
+-----------+--------+--------+--------+-------+
5 rows in set (0.00 sec)
```

---

# Question No 6: Total employees and count hired in each year

### Query
```sql
SELECT COUNT(*) AS total,SUM(YEAR(hiredate)=1980) AS y1980,SUM(YEAR(hiredate)=1981) AS y1981,SUM(YEAR(hiredate)=1982) AS y1982,SUM(YEAR(hiredate)=1983) AS y1983 FROM employee;
```

### Output
```text
+-------+-------+-------+-------+-------+
| total | y1980 | y1981 | y1982 | y1983 |
+-------+-------+-------+-------+-------+
| 14    | 1     | 10    | 2     | 1     |
+-------+-------+-------+-------+-------+
1 row in set (0.00 sec)
```

---

# Question No 7: Last Sunday of current month

### Query
```sql
SELECT DATE_SUB(LAST_DAY(CURDATE()),INTERVAL (DAYOFWEEK(LAST_DAY(CURDATE()))-1) DAY) AS last_sunday;
```

### Output
```text
Output will vary depending on current date
```

---

# Question No 8: Department number and total employees

### Query
```sql
SELECT deptno,COUNT(*) AS total_emp FROM employee GROUP BY deptno;
```

### Output
```text
+--------+-----------+
| deptno | total_emp |
+--------+-----------+
| 10     | 1         |
| 20     | 6         |
| 30     | 6         |
| 40     | 1         |
+--------+-----------+
4 rows in set (0.00 sec)
```

---

# Question No 9: Jobs and total employees in each job

### Query
```sql
SELECT job,COUNT(*) AS total_emp FROM employee GROUP BY job;
```

### Output
```text
+-----------+-----------+
| job       | total_emp |
+-----------+-----------+
| CLERK     | 4         |
| SALESMAN  | 4         |
| MANAGER   | 3         |
| ANALYST   | 2         |
| PRESIDENT | 1         |
+-----------+-----------+
5 rows in set (0.00 sec)
```

---

# Question No 10: Department number and total salary

### Query
```sql
SELECT deptno,SUM(sal) AS total_sal FROM employee GROUP BY deptno;
```

### Output
```text
+--------+-----------+
| deptno | total_sal |
+--------+-----------+
| 10     | 1430      |
| 20     | 16858     |
| 30     | 9780      |
| 40     | 3300      |
+--------+-----------+
4 rows in set (0.00 sec)
```

---

## Conclusion  
All queries were successfully executed using SQL functions and grouping operations.
