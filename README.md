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

### claims table

```sql
CREATE TABLE Claims(
    claim_id INT PRIMARY KEY,
    policy_id INT,
    amount DECIMAL(10, 2),
    status VARCHAR(50),
    date_filed DATE,
    FOREIGN KEY (policy_id) REFERENCES Policies(policy_id)
);
```
### policies table

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
### inserting data into employee table
```sql
INSERT INTO Employees(employee_id, Ename, Erole, email) VALUES (1, 'Alice', 'Manager', 'alice@gmail.com');
INSERT INTO Employees(employee_id, Ename, Erole, email) VALUES (2, 'Bob', 'Sales Agent', 'bob@gmail.com');
INSERT INTO Employees(employee_id, Ename, Erole, email) VALUES (3, 'Charlie', 'Underwriter', 'charlie@gmail.com');
INSERT INTO Employees(employee_id, Ename, Erole, email) VALUES (4, 'Diana', 'Claims Adjuster', 'diana@gmail.com');
INSERT INTO Employees(employee_id, Ename, Erole, email) VALUES (5, 'Evan', 'Customer Service', 'evan@gmail.com');
INSERT INTO Employees(employee_id, Ename, Erole, email) VALUES (6, 'Fiona', 'Accountant', 'fiona@gmail.com');
```
### insert into clients table
```sql
INSERT INTO Clients (client_id, Cname, contact_info) VALUES (1, 'John Doe', 'john.doe@example.com');
INSERT INTO Clients (client_id, Cname, contact_info) VALUES (2, 'Jane Smith', 'jane.smith@example.com');
```
### insert into policies table
```sql
INSERT INTO Policies (policy_id, client_id, employee_id, policy_type, start_date, end_date) VALUES (1, 1, 2, 'Health Insurance', '', '');
INSERT INTO Policies (policy_id, client_id, employee_id, policy_type, start_date, end_date) VALUES (2, 2, 2, 'Car Insurance', '', '');

```
### insert into claims table
```sql
INSERT INTO Claims (claim_id, policy_id, amount, status, date_filed) VALUES (1, 1, 500.00, 'Pending', '');

```
### update employees table
```sql
UPDATE Employees SET email = 'alice.new@gmail.com' WHERE employee_id = 1;
```
### update claims table
```sql
UPDATE Claims SET status = 'Approved' WHERE claim_id = 1;
```
### Delete
```sql
DELETE FROM Claims WHERE claim_id = 1;
```
### select
```sql
select * from Employees;
```






# My image

![Alt text](https://github.com/J2001-code/J2001-code/blob/main/employees%20table.JPG)
