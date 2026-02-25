# DBMS Lab – Experiment 1

## Aim  
To perform DDL and DML operations on the `Employee_Master` table.

---

## Problem Statement  
1. Create `Employee_Master` table with data using `Employee` table.  
2. Delete all records from `Employee_Master` whose `DeptNo` is 10.  
3. Update 10% increase in salary for `DeptNo` 20 in `Employee_Master`.  
4. Alter `SAL` with size 10,2 in `Employee_Master`.  
5. Drop `Employee_Master` table.  

---

# Step 1: Create Employee_Master Table

### Query
```sql
CREATE TABLE Employee_Master AS
SELECT * FROM Employee;
```

### Output  
Table `Employee_Master` created successfully with 14 rows copied.

---

# Step 2: Delete Records Where DeptNo = 10

### Query
```sql
DELETE FROM Employee_Master
WHERE DeptNo = 10;
```

### Output  
1 row deleted successfully.

---

# Step 3: Update 10% Salary Increase for DeptNo = 20

### Query
```sql
UPDATE Employee_Master
SET Sal = Sal + (Sal * 0.10)
WHERE DeptNo = 20;
```

### Output  
Salary updated successfully for employees in `DeptNo = 20`.

---

# Step 4: Alter SAL Column Size

### Query
```sql
ALTER TABLE Employee_Master
MODIFY Sal DECIMAL(10,2);
```

### Output  
Column `SAL` modified to `DECIMAL(10,2)` successfully.

---

# Step 5: Drop Employee_Master Table

### Query
```sql
DROP TABLE Employee_Master;
```

### Output  
Table `Employee_Master` dropped successfully.

---

## Conclusion  
`Employee_Master` table was successfully created, modified, updated, and deleted using DDL and DML commands.
