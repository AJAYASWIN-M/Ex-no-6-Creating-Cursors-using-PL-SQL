# Ex. No: 6 Creating Cursors using PL/SQL

## DATE:

### AIM: To create a cursor using PL/SQL.

### Steps:
1. Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
2. Create a cursor named as employee_cursor
3. Using cursor read each record and display the result
4. Close the cursor

### Program:
```sql
SQL> CREATE TABLE emp(empid number, empname varchar(10), dept varchar(10),salary number);


INSERT INTO emp(empid, empname,dept,salary)
values(1,'ajay',100000,200000);
INSERT INTO emp(empid, empname, dept, salary)
values(2,'aswin','HR',600000);
INSERT INTO emp(empid, empname, dept, salary)
values(3,'ajayaswin','seo',500000);

```
### Create employee table

![ex 6 1](https://github.com/AJAYASWIN-M/Ex-no-6-Creating-Cursors-using-PL-SQL/assets/118679692/553a8d92-1c9c-4581-ad7d-1dadb028e1ce)

### PLSQL Cursor code
```sql
SQL> SET SERVEROUTPUT ON;
SQL> DECLARE
  2  CURSOR employee_cursor IS
  3  SELECT empid, empname, dept, salary
  4  FROM emp;
  5  empid number;
  6  empname varchar(10);
  7  empdept varchar(10);
  8  salary number;
  9  BEGIN
 10     OPEN employee_cursor;
 11     LOOP
 12             FETCH employee_cursor INTO empid, empname, empdept, salary;
 13             EXIT WHEN employee_cursor%NOTFOUND;
 14             DBMS_OUTPUT.PUT_LINE('**********************');
 15             DBMS_OUTPUT.PUT_LINE('EMPLOYEE ID: ' || empid);
 16             DBMS_OUTPUT.PUT_LINE('EMPLOYEE NAME: ' || empname);
 17             DBMS_OUTPUT.PUT_LINE('DEPARTMENT: ' || empdept);
 18             DBMS_OUTPUT.PUT_LINE('SALARY: ' || salary);
 19             DBMS_OUTPUT.PUT_LINE('**********************');
 20     END LOOP;
 21     CLOSE employee_cursor;
 22  END;
 23  /
```
### Output:
![ex 6](https://github.com/AJAYASWIN-M/Ex-no-6-Creating-Cursors-using-PL-SQL/assets/118679692/4b3b29d1-0da1-4768-bcbe-079c20f11a7c)

### Result:
The program has been successfully implemented.
