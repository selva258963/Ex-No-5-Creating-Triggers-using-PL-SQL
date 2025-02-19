# Ex. No: 5 Creating Triggers using PL/SQL
## DATE: 1/9/23
### AIM: To create a Trigger using PL/SQL.

### Steps:
1. Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
2. Create salary_log table with following attributes (log_id NUMBER GENERATED ALWAYS AS IDENTITY, empid NUMBER,empname VARCHAR(10),old_salary NUMBER,new_salary NUMBER,update_date DATE);
3. Create a trigger named as log_salary-update.
4. Inside the trigger block, Insert the values into the salary_log table whenever the salary is updated.
5. End the trigger.
6. Update the salary of an employee in employee table.
7. Whenever a salary is updated for the employee it must be logged into the salary_log table with old salary and new salary.
8. Display the employee table, salary_log table.

### Create employee table
![image](https://github.com/selva258963/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/121961701/d4b5bfe9-fe64-4d02-ace0-edc517a60624)


### Create salary_log table
![image](https://github.com/selva258963/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/121961701/e0b75f07-02ff-4a43-9a4a-175c2d0f22c1)


### PLSQL Trigger code
```
set serveroutput on
CREATE OR REPLACE TRIGGER log_salary1_update
BEFORE UPDATE ON emp1
FOR EACH ROW
DECLARE
old_salary NUMBER;
new_salary NUMBER;
BEGIN
old_salary := :OLD.salary;
new_salary := :NEW.salary;
INSERT INTO sal_log1(empid, empname, old_salary, new_salary, update_date)
VALUES(:OLD.empid, :OLD.empname, old_salary, new_salary, SYSDATE);
END IF;
END;
/
```
Trigger created.

### Output:

![image](https://github.com/selva258963/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/121961701/656e8e1a-0a3d-4b4e-b600-9ef0a8f1c827)


### Result:
Thus , the output has been successfully verified.
