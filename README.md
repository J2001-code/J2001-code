# Employee Management Database (Using Oracle as RDBMS)

This README provides an overview of the Employee Management Database, designed specifically for Oracle courses to manage and store information related to employees and organizational structure. It includes tables for Countries, Departments, Roles, Managers, Employees, Allowance, and Attendance records.

## Table Structures

### Employees Table

```sql
CREATE TABLE Employees(
    employee_id INT PRIMARY KEY,
    Ename VARCHAR(100),
    Erole VARCHAR(50),
    email VARCHAR(100)
);
```
### client table
```sql
CREATE TABLE Clients(
    client_id INT PRIMARY KEY,
    Cname VARCHAR(100),
    contact_info VARCHAR(100)
);
```

# My image

![Alt text](https://github.com/J2001-code/J2001-code/blob/main/employees%20table.JPG)
