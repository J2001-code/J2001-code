 👋 Hi, I’m @J2001-code
- 👀 I’m interested in ...Database development with PL/SQL
- 🌱 I’m currently learning ...SOFTWARE ENGINEERING
  - 📫 How to reach me ..niyomwungerijanvier2001@gmail.com



# Employee Management Database (Using Oracle as RDBMS)

This README provides an overview of the Employee Management Database, designed specifically for Oracle courses to manage and store information related to employees and organizational structure, that Related to Provide Insurance service . It includes tables for Employees, Clients, Claims and Policies.

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
### Policies table

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
### Inserting data into employee table
```sql
INSERT INTO Employees(employee_id, Ename, Erole, email) VALUES (1, 'Alice', 'Manager', 'alice@gmail.com');
INSERT INTO Employees(employee_id, Ename, Erole, email) VALUES (2, 'Bob', 'Sales Agent', 'bob@gmail.com');
INSERT INTO Employees(employee_id, Ename, Erole, email) VALUES (3, 'Charlie', 'Underwriter', 'charlie@gmail.com');
INSERT INTO Employees(employee_id, Ename, Erole, email) VALUES (4, 'Diana', 'Claims Adjuster', 'diana@gmail.com');
INSERT INTO Employees(employee_id, Ename, Erole, email) VALUES (5, 'Evan', 'Customer Service', 'evan@gmail.com');
INSERT INTO Employees(employee_id, Ename, Erole, email) VALUES (6, 'Fiona', 'Accountant', 'fiona@gmail.com');
```
### Insert Into clients Table
```sql
INSERT INTO Clients (client_id, Cname, contact_info) VALUES (1, 'John Doe', 'john.doe@example.com');
INSERT INTO Clients (client_id, Cname, contact_info) VALUES (2, 'Jane Smith', 'jane.smith@example.com');
```
### Insert Into Policies Table
```sql
INSERT INTO Policies (policy_id, client_id, employee_id, policy_type, start_date, end_date) VALUES (1, 1, 2, 'Health Insurance', '', '');
INSERT INTO Policies (policy_id, client_id, employee_id, policy_type, start_date, end_date) VALUES (2, 2, 2, 'Car Insurance', '', '');

```
### Insert into claims table
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
### Inner joins to retrieve policies and their related employees and clients
```sql
SELECT 
    Policies.policy_id, 
    Clients.Cname AS client_name, 
    Employees.Ename AS employee_name, 
    Policies.policy_type, 
    Policies.start_date, 
    Policies.end_date
FROM 
    Policies
INNER JOIN Clients ON Policies.client_id = Clients.client_id
INNER JOIN Employees ON Policies.employee_id = Employees.employee_id;
```
### Inner joins to retrieve claims,policies and claims
```sql
SELECT 
    Claims.claim_id, 
    Claims.amount, 
    Claims.status, 
    Claims.date_filed, 
    Policies.policy_type, 
    Clients.Cname AS client_name
FROM 
    Claims
INNER JOIN Policies ON Claims.policy_id = Policies.policy_id
INNER JOIN Clients ON Policies.client_id = Clients.client_id;
```
### left join to retrieve all Employees nd their associated policies
```sql
SELECT 
    Employees.Ename AS employee_name, 
    Employees.Erole, 
    Policies.policy_id, 
    Policies.policy_type, 
    Policies.start_date, 
    Policies.end_date
FROM 
    Employees
LEFT JOIN Policies ON Employees.employee_id = Policies.employee_id;
```

### Inner joins to retrieve claims and the employees(claims adjusters) who managed the policies
```sql
SELECT 
    Claims.claim_id, 
    Claims.amount, 
    Claims.status, 
    Claims.date_filed, 
    Employees.Ename AS employee_name
FROM 
    Claims
INNER JOIN Policies ON Claims.policy_id = Policies.policy_id
INNER JOIN Employees ON Policies.employee_id = Employees.employee_id;
```
### JOIN CLIENTS WITH THEIR POLICIES AND CLAIMS
```SQL
SELECT 
    Clients.Cname AS client_name, 
    Policies.policy_type, 
    Claims.claim_id, 
    Claims.amount, 
    Claims.status
FROM 
    Clients
INNER JOIN Policies ON Clients.client_id = Policies.client_id
LEFT JOIN Claims ON Policies.policy_id = Claims.policy_id;
```
## JOINS WITH SUBQUERY TO FINND TOTAL CLAIMS AMOUNT FOR EACH CLIENT
```sql
SELECT 
    C.client_id, 
    C.Cname AS client_name, 
    (SELECT SUM(amount) 
     FROM Claims CL 
     INNER JOIN Policies P ON CL.policy_id = P.policy_id
     WHERE P.client_id = C.client_id) AS total_claims_amount
FROM 
    Clients C;
```
# Conceptual, logical and physical data model
![Alt text](![2nd img](https://github.com/user-attachments/assets/c9dc029a-8fbe-43b8-908d-3bd49c064e95)
)






