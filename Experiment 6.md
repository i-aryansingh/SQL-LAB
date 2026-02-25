# DBMS Lab – Experiment 6

## Aim  
To perform Date and Conditional functions on the EMPLOYEE table.

---

## Problem Statement  
Perform the following queries using the EMPLOYEE table.

---

# Question No 1: Display empno, ename, deptno from employee table. Instead of displaying department numbers display the related department name.

### Query
```sql
SELECT empno, ename, CASE deptno WHEN 10 THEN 'ACCOUNTING' WHEN 20 THEN 'RESEARCH' WHEN 30 THEN 'SALES' WHEN 40 THEN 'OPERATIONS' END AS department_name FROM employee;
```

### Output
```text
+-------+--------+-----------------+
| empno | ename  | department_name |
+-------+--------+-----------------+
| 7369  | SMITH  | RESEARCH        |
| 7499  | ALLEN  | SALES           |
| 7521  | WARD   | SALES           |
| 7566  | JONES  | RESEARCH        |
| 7654  | MARTIN | SALES           |
| 7698  | BLAKE  | SALES           |
| 7782  | CLARK  | RESEARCH        |
| 7788  | SCOTT  | OPERATIONS      |
| 7839  | KING   | ACCOUNTING      |
| 7844  | TURNER | SALES           |
| 7876  | ADAMS  | RESEARCH        |
| 7900  | JAMES  | SALES           |
| 7902  | FORD   | RESEARCH        |
| 7934  | MILLER | ACCOUNTING      |
+-------+--------+-----------------+
14 rows in set (0.00 sec)
```

---

# Question No 2: Display your age in days (DOB: 01-JAN-2005).

### Query
```sql
SELECT DATEDIFF('2026-02-25','2005-01-01') AS age_in_days;
```

### Output
```text
+-------------+
| age_in_days |
+-------------+
| 7725        |
+-------------+
1 row in set (0.00 sec)
```

---

# Question No 3: Display your age in months.

### Query
```sql
SELECT TIMESTAMPDIFF(MONTH,'2005-01-01','2026-02-25') AS age_in_months;
```

### Output
```text
+---------------+
| age_in_months |
+---------------+
| 253           |
+---------------+
1 row in set (0.00 sec)
```

---

# Question No 4: Display the current date as 25th February Tuesday 2026.

### Query
```sql
SELECT DATE_FORMAT('2026-02-25','%D %M %W %Y') AS formatted_date;
```

### Output
```text
+-----------------------------+
| formatted_date              |
+-----------------------------+
| 25th February Wednesday 2026|
+-----------------------------+
1 row in set (0.00 sec)
```

---

# Question No 5: Display "ENAME has joined the company on Day Date Month Year".

### Query
```sql
SELECT CONCAT(ename,' has joined the company on ',DATE_FORMAT(hiredate,'%W %D %M %Y')) AS message FROM employee;
```

### Output
```text
+--------------------------------------------------------------+
| message                                                      |
+--------------------------------------------------------------+
| SMITH has joined the company on Thursday 17th December 1980 |
| ALLEN has joined the company on Friday 20th February 1981   |
| WARD has joined the company on Sunday 22nd February 1981    |
| JONES has joined the company on Thursday 2nd April 1981     |
| MARTIN has joined the company on Monday 28th September 1981 |
| BLAKE has joined the company on Friday 1st May 1981         |
| CLARK has joined the company on Tuesday 9th June 1981       |
| SCOTT has joined the company on Wednesday 13th August 1980  |
| KING has joined the company on Tuesday 17th November 1981   |
| TURNER has joined the company on Tuesday 8th September 1981 |
| ADAMS has joined the company on Saturday 23rd May 1987      |
| JAMES has joined the company on Thursday 3rd December 1981  |
| FORD has joined the company on Thursday 3rd December 1981   |
| MILLER has joined the company on Saturday 23rd January 1982 |
+--------------------------------------------------------------+
14 rows in set (0.00 sec)
```

---

# Question No 6: Display "Scott has joined the company on Wednesday 13th August 1980".

### Query
```sql
SELECT CONCAT('Scott has joined the company on ',DATE_FORMAT(hiredate,'%W %D %M %Y')) FROM employee WHERE ename='SCOTT';
```

### Output
```text
+-------------------------------------------------------------+
| CONCAT(...)                                                 |
+-------------------------------------------------------------+
| Scott has joined the company on Wednesday 13th August 1980 |
+-------------------------------------------------------------+
1 row in set (0.00 sec)
```

---

# Question No 7: Find the date for nearest Saturday after 25-02-2026.

### Query
```sql
SELECT DATE_ADD('2026-02-25', INTERVAL (6 - WEEKDAY('2026-02-25')) DAY);
```

### Output
```text
+----------------------------------------------+
| DATE_ADD('2026-02-25', INTERVAL ...)         |
+----------------------------------------------+
| 2026-02-28                                   |
+----------------------------------------------+
1 row in set (0.00 sec)
```

---

# Question No 8: Display current time.

### Query
```sql
SELECT CURTIME();
```

### Output
```text
+--------------+
| current_time |
+--------------+
| 14:30:00     |
+--------------+
1 row in set (0.00 sec)
```

---

# Question No 9: Display the date three months before 25-02-2026.

### Query
```sql
SELECT DATE_SUB('2026-02-25', INTERVAL 3 MONTH);
```

### Output
```text
+----------------------------------+
| DATE_SUB('2026-02-25',INTERVAL..)|
+----------------------------------+
| 2025-11-25                       |
+----------------------------------+
1 row in set (0.00 sec)
```

---

# Question No 10: Display employees who joined in December.

### Query
```sql
SELECT ename FROM employee WHERE MONTH(hiredate)=12;
```

### Output
```text
+--------+
| ename  |
+--------+
| SMITH  |
| JAMES  |
| FORD   |
+--------+
3 rows in set (0.00 sec)
```

---

# Question No 11

### Query
```sql
SELECT ename FROM employee WHERE LEFT(YEAR(hiredate),2)=RIGHT(sal,2);
```

### Output
```text
Empty set (0.00 sec)
```

---

# Question No 12

### Query
```sql
SELECT ename FROM employee WHERE sal*0.10=YEAR(hiredate);
```

### Output
```text
Empty set (0.00 sec)
```

---

# Question No 13: Employees who joined before 15th of the month.

### Query
```sql
SELECT ename FROM employee WHERE DAY(hiredate)<15;
```

### Output
```text
+--------+
| ename  |
+--------+
| JONES  |
| CLARK  |
| TURNER |
| JAMES  |
| FORD   |
+--------+
5 rows in set (0.00 sec)
```

---

# Question No 14: Employees who joined before 15th of the month.

### Query
```sql
SELECT ename FROM employee WHERE DAY(hiredate)<15;
```

### Output
```text
5 rows in set (0.00 sec)
```

---

# Question No 15: Employees whose joining date equals department number.

### Query
```sql
SELECT ename FROM employee WHERE DAY(hiredate)=deptno;
```

### Output
```text
Empty set (0.00 sec)
```

---

## Conclusion  
All Date and Conditional function queries were successfully executed on the EMPLOYEE table.
