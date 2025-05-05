# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
Insert a student with RollNo 201, Name David Lee, Gender M, Subject Physics, and MARKS 92 into the Student_details table.

```sql
insert into Student_details(RollNo, Name, Gender, Subject, MARKS)
Values(201, 'David Lee', 'M', 'Physics', 92);
```

**Output:**

![image](https://github.com/user-attachments/assets/429395e8-8976-4fc8-8d7b-76b6cb694518)


**Question 2**
---
Create a table named Products with the following constraints:

ProductID should be the primary key.
ProductName should be NOT NULL.
Price should be greater than 0.
Stock should be greater than or equal to 0.

```sql
create table Products(
ProductID int primary key,
ProductName varchar(255) NOT NULL,
Price real check (Price>0),
Stock int check(Stock>=0)
);
```

**Output:**

![image](https://github.com/user-attachments/assets/fe67fde7-690d-4ae5-b349-045ac5a0c569)


**Question 3**
---
Create a table named Shipments with the following constraints:
ShipmentID as INTEGER should be the primary key.
ShipmentDate as DATE.
SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID).
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```sql
create table Shipments(
ShipmentID int primary key,
ShipmentDate date,
SupplierID int,
OrderID int,
foreign key (SupplierID) references Suppliers(SupplierID),
foreign key (OrderID) references Orders(OrderID)
);
```

**Output:**

![image](https://github.com/user-attachments/assets/3a44b801-8517-46c1-8d39-7de18e542cfd)


**Question 4**
---
Write a SQL Query to add an attribute designation in the employee table with the data type VARCHAR(50).

```sql
alter table employee add column designation varchar(50);
```

**Output:**

![image](https://github.com/user-attachments/assets/dcb47bfe-867d-4072-b494-d850371fe3e6)


**Question 5**
---
Write a SQL query to add a new column MobileNumber of type NUMBER and a new column Address of type VARCHAR(100) to the Student_details table.

```sql
ALTER table Student_details 
add column MobileNumber NUMBER; 

ALTER table Student_details 
add column Address VARCHAR(100);
```

**Output:**

![image](https://github.com/user-attachments/assets/0b2e9196-3c00-4c31-b08a-518b5b03a8f7)


**Question 6**
---
Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should set NULL on updates and deletes.
item_desc and rate should not accept NULL.

```sql
create table item(
item_id TEXT primary key,
item_desc TEXT,
rate INTEGER,
icom_id TEXT(4),
FOREIGN KEY (icom_id) REFERENCES company(com_id)
ON UPDATE SET NULL
ON DELETE SET NULL
);
```

**Output:**

![image](https://github.com/user-attachments/assets/69708c0c-19b2-4691-8ee5-fda2630a6a82)


**Question 7**
---
Insert all students from Archived_students table into the Student_details table.

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           RollNo      INT           0                       1
1           Name        VARCHAR(100)  0                       0
2           Gender      VARCHAR(10)   0                       0
3           Subject     VARCHAR(50)   0                       0
4           MARKS       INT           0                       0

```sql
INSERT INTO Student_details(RollNo,      Name,           Gender,      Subject,     MARKS)
SELECT RollNo,      Name,           Gender,      Subject,     MARKS FROM Archived_students;
```

**Output:**

![image](https://github.com/user-attachments/assets/d4b97cb0-283d-48a1-b0c9-23adf43f50a3)


**Question 8**
---
Create a table named Attendance with the following constraints:
AttendanceID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
AttendanceDate as DATE.
Status as TEXT should be one of 'Present', 'Absent', 'Leave'.

```sql
CREATE TABLE Attendance(
AttendanceID INTEGER PRIMARY KEY,
EmployeeID INTEGER,
AttendanceDate DATE,
Status TEXT CHECK(Status IN ( 'Present', 'Absent', 'Leave')),
FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID)
);
```

**Output:**

![image](https://github.com/user-attachments/assets/f45392a1-fc0f-400e-9c92-2614372ecabc)


**Question 9**
---
Create a table named Employees with the following columns:

EmployeeID as INTEGER
FirstName as TEXT
LastName as TEXT
HireDate as DATE

```sql
CREATE TABLE Employees(
EmployeeID INTEGER,
FirstName TEXT,
LastName TEXT,
HireDate DATE
);
```

**Output:**

![image](https://github.com/user-attachments/assets/c3b757f0-3e2f-49a8-a770-33091e569bd0)

**Question 10**
---
Insert the following products into the Products table:

Name        Category     Price       Stock
----------  -----------  ----------  ----------
Smartphone  Electronics  800         150
Headphones  Accessories  200         300

```sql
INSERT INTO Products(Name, Category, Price, Stock)
VALUES
('Smartphone', 'Electronics', 800,150),
('Headphones', 'Accessories', 200,300);
```

**Output:**

![image](https://github.com/user-attachments/assets/3991560a-91f4-467a-91bb-8cf236113aac)



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
