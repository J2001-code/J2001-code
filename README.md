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

```sql
CREATE TABLE Policies(
    policy_id INT PRIMARY KEY,
    client_id INT,
    employee_id INT,
    policy_type VARCHAR(50),
    start_date DATE,
    end_date DATE,
    FOREIGN KEY (client_id) REFERENCES Clients(client_id),
    FOREIGN KEY (employee_id) REFERENCES Employees(employee_id)
);
```

# My image

![Alt text](https://github.com/J2001-code/J2001-code/blob/main/employees%20table.JPG)
