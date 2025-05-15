# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
Write the SQL query that achieves the selection of all columns from the "patients" table and the specialization from the "doctors" table (aliased as "doctor_specialization"), with an inner join on the "doctor_id" column.


```sql
SELECT 
    p.*, 
    d.specialization AS doctor_specialization
FROM 
    patients p
INNER JOIN 
    doctors d ON p.doctor_id = d.doctor_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/825b52e5-80ca-4afb-86e9-9b0a3e226bd2)

**Question 2**
---
From the following tables write a SQL query to display the customer name, customer city, grade, salesman, salesman city. The results should be sorted by ascending customer_id.  

```sql
SELECT c.cust_name,c.city,c.grade,s.name as Salesman,s.city
from customer c
join salesman s on s.salesman_id = c.salesman_id
order by c.customer_id ASC
```

**Output:**

![image](https://github.com/user-attachments/assets/18759ab2-da2e-4624-a393-810607272027)

**Question 3**
---
 From the following tables write a SQL query to find salespeople who received commissions of more than 12 percent from the company. Return Customer Name, customer city, Salesman, commission.  


```sql
SELECT c.cust_name as "Customer Name" ,c.city, s.name as Salesman,s.commission
from customer c
join salesman s on s.salesman_id = c.salesman_id
where s.commission>0.12
```

**Output:**

![image](https://github.com/user-attachments/assets/5e59dded-3503-4835-a2bf-13b65ebda7cd)

**Question 4**
---
Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column.


```sql
SELECT c.cust_name,o.ord_no,o.ord_date,o.purch_amt
from CUSTOMER c
left join ORDERS o on o.customer_id = c.customer_id
```

**Output:**

![image](https://github.com/user-attachments/assets/067dd17b-04b2-4005-85b8-a7a46fb88d65)

**Question 5**
---
From the following tables write a SQL query to find those customers with a grade less than 300. Return cust_name, customer city, grade, Salesman, salesmancity. The result should be ordered by ascending customer_id. 


```sql
SELECT c.cust_name    ,    c.city  ,           c.grade, s.name as  Salesman,s.city
from customer c
join salesman s on s.salesman_id = c.salesman_id
where c.grade<300
order by c.customer_id ASC
```

**Output:**

![image](https://github.com/user-attachments/assets/193213c2-3229-43fd-bba5-707e592b3eb6)

**Question 6**
---
Write the SQL query that achieves the selection of the "cust_name" and "city" columns from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column and a condition filtering for customers in the city 'London'.


```sql
SELECT 
    c.cust_name, 
    c.city, 
    o.ord_no, 
    o.ord_date, 
    o.purch_amt
FROM 
    customer c
LEFT JOIN 
    orders o ON c.customer_id = o.customer_id
WHERE 
    c.city = 'London';
```

**Output:**

![image](https://github.com/user-attachments/assets/9cc4a3bb-3660-40f1-a6b4-fd649c5201af)

**Question 7**
---
From the following tables write a SQL query to find the details of an order. Return ord_no, ord_date, purch_amt, Customer Name, grade, Salesman, commission. 


```sql
SELECT 
    o.ord_no,
    o.ord_date,
    o.purch_amt,
    c.cust_name AS "Customer Name",
    c.grade,
    s.name AS "Salesman",
    s.commission
FROM 
    orders o
JOIN 
    customer c ON o.customer_id = c.customer_id
JOIN 
    salesman s ON o.salesman_id = s.salesman_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/9f9e9b5d-adf6-41ea-b8f0-57f6fb9d5bec)

**Question 8**
---
write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.


```sql
SELECT 
    s.name AS Salesman,
    c.cust_name,
    s.city
FROM 
    salesman s
JOIN 
    customer c ON s.city = c.city;
```

**Output:**

![image](https://github.com/user-attachments/assets/ea2de0cd-8c45-40d0-8e0a-ff1d5aace3cb)

**Question 9**
---
Write the SQL query that achieves the selection of all columns from the "patients" table (aliased as "p"), with an inner join on the "patient_id" column and a condition filtering for test results with a test date between '2024-03-01' and '2024-03-31'.


```sql
SELECT p.*
FROM patients p
INNER JOIN test_results t ON p.patient_id = t.patient_id
WHERE t.test_date BETWEEN '2024-03-01' AND '2024-03-31';
```

**Output:**


![image](https://github.com/user-attachments/assets/ea2de0cd-8c45-40d0-8e0a-ff1d5aace3cb)


**Question 10**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and all columns from the "test_results" table (aliased as "t"), with an inner join on the "patient_id" column.


```sql
SELECT 
    p.first_name AS patient_name,
    t.*
FROM 
    patients p
INNER JOIN 
    test_results t ON p.patient_id = t.patient_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/2b998725-fe59-4a73-a883-6ae3fc5ca4f8)


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
