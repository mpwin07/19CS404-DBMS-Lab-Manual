# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--
 Update the total selling price to quantity sold multiplied by updated selling price per unit where product id is 10 in the sales table.

SALES TABLE
name               type
-----------------  ---------------
sale_id            INT
sale_date          DATE
product_id         INT
quantity           INT
sell_price         DECIMAL(10,2)
total_sell_price   DECIMAL(10,2)

```sql
UPDATE SALES
SET total_sell_price = quantity*sell_price
WHERE product_id=10;
```

**Output:**

![image](https://github.com/user-attachments/assets/d8ac3cde-1efd-4a8d-9d36-b98525010afa)

**Question 2**
---
Write a SQL statement to change the first_name column of employees table with 'John' for those employees whose department_id is 80 and gets a commission_pct below 0.35.

```sql
UPDATE EMPLOYEES
SET FIRST_NAME = 'John'
WHERE DEPARTMENT_ID = 80 AND COMMISSION_PCT < 0.35
```

**Output:**

![image](https://github.com/user-attachments/assets/a67c7003-3e6e-4fc7-a312-ccb94fb4cc75)


**Question 3**
---
Write a SQL query to reduce the reorder level by 30% where cost price is more than 50 and quantity in stock is less than 100 in the products table.

Products Table 

name          type       
----------    ---------- 
product_id     INT PRIMARY KEY        
product_name   VARCHAR(10) 
category       VARCHAR(50) 
cost_price     DECIMAL(10) 
sell_price     DECIMAL(10) 
reorder_lvl    INT        
quantity       INT        
supplier_id    INT   
```sql
UPDATE PRODUCTS
SET reorder_lvl = reorder_lvl*0.7
WHERE cost_price>50 AND quantity<100;
```

**Output:**

![image](https://github.com/user-attachments/assets/1fbbe8ae-8e27-4ba1-836d-a08f3e8a9f36)

**Question 4**
---
Write a SQL statement to Increase the selling price per unit by 5% for product ID 15 who's sale is on '2023-01-31'.

sales(sale_id,sale_date,product_id,quantity,sell_price,total_sell_price)
```sql
UPDATE sales
SET sell_price = sell_price*(1.05)
WHERE product_id = 15 AND sale_date = '2023-01-31';
```

**Output:**

![image](https://github.com/user-attachments/assets/eb1f4376-4180-4a3d-a7b5-11270c76f675)

**Question 5**
---
Increase the reorder level by 30% for products from 'Food' category having quantity in stock less than 50% of existing reorder level in the products table
name               type
--------------  ----------
product_id         INT
product_name       VARCHAR(10)
category           VARCHAR(50)
cost_price         DECIMAL(10)
sell_price         DECIMAL(10)
reorder_lvl        INT
quantity              INT
supplier_id           INT
```sql
UPDATE PRODUCTS
SET reorder_lvl = reorder_lvl * 1.3
WHERE category= 'Food' AND quantity<(reorder_lvl*0.5);
```

**Output:**

![image](https://github.com/user-attachments/assets/4541ea37-eadd-4041-9d0c-aa51f4f89ab1)

**Question 6**
---
Write a SQL query to Delete customers from 'customer' table where 'CUST_CITY' is not 'New York' and 'OUTSTANDING_AMT' is greater than 5000.
```sql
DELETE FROM Customer
WHERE CUST_CITY<>'New York' AND OUTSTANDING_AMT>5000;
```

**Output:**

![image](https://github.com/user-attachments/assets/baa7ba98-58bb-4653-b4ae-5b1d01885ecd)

**Question 7**
---
Write a SQL query to remove rows from the table 'customer' with the following condition -

1. 'cust_country' must be 'India',

2. 'cus_city' must not be 'Chennai',
```sql
DELETE FROM customer
WHERE cust_country='India' AND cust_city<>'Chennai';
```

**Output:**

![image](https://github.com/user-attachments/assets/e3390be2-d65c-40e1-b177-cfc1a40a0b5b)

**Question 8**
---
Write a SQL query to delete a doctor from Doctors table whos specialization is 'Cardiology'
```sql
DELETE FROM Doctors
WHERE specialization = 'Cardiology';
```

**Output:**

![image](https://github.com/user-attachments/assets/fed8ef3e-f3c3-4423-b1b3-f8add5a208d9)

**Question 9**
---
Write a SQL query to Delete customers with 'GRADE' 3 or 'AGENT_CODE' 'A008' whose 'OUTSTANDING_AMT' is less than 5000
```sql
DELETE FROM Customer
WHERE AGENT_CODE = 'A008' AND OUTSTANDING_AMT < 5000;
```

**Output:**

![image](https://github.com/user-attachments/assets/1120c4f4-0fac-4544-a25a-720d89088912)

**Question 10**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is exactly 2.
```sql
DELETE FROM Customer
WHERE GRADE = 2;
```

**Output:**

![image](https://github.com/user-attachments/assets/ccc10abb-2c13-42d6-a848-c439ccdcb5bc)

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
