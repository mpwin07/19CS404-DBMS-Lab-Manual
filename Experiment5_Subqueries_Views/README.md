# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose AGE is LESS than $30

Sample table: CUSTOMERS
```sql
select * from CUSTOMERS
WHERE AGE<30
```

**Output:**

![image](https://github.com/user-attachments/assets/d78c5bd1-5cac-44f4-ace9-fa0e11873e91)

**Question 2**
---
Write a SQL query to Retrieve the medications with dosages equal to the lowest dosage

Table Name: Medications (attributes: medication_id, medication_name, dosage)
```sql
SELECT medication_id as medic, medication_name,dosage from Medications
order by dosage ASC
limit 1
```

**Output:**

![image](https://github.com/user-attachments/assets/b7b50ca4-414a-4c17-8f01-585f630dd7f7)

**Question 3**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is greater than $1500.

Sample table: CUSTOMERS
```sql
select * from CUSTOMERS
where SALARY>1500
```

**Output:**

![image](https://github.com/user-attachments/assets/7c129553-de8c-4063-b185-6d5fae18d6e9)

**Question 4**
---
From the following tables, write a SQL query to find all the orders issued by the salesman 'Paul Adam'. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.
```sql
select * from orders
where salesman_id=(
      select salesman_id
      from salesman
      where name = 'Paul Adam')
```

**Output:**

![image](https://github.com/user-attachments/assets/643e9c11-3377-43ea-9925-2c2e224b1548)

**Question 5**
---
From the following tables write a SQL query to find salespeople who had more than one customer. Return salesman_id and name.
```sql
SELECT s.salesman_id , s.name
from salesman s
join customer c on s.salesman_id = c.salesman_id
group by s.salesman_id,s.name
having count(c.customer_id)>1
```

**Output:**

![image](https://github.com/user-attachments/assets/dc0203d7-11b0-4558-8836-d6b2db4a780c)

**Question 6**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose Address as Delhi

Sample table: CUSTOMERS
```sql
SELECT *
FROM CUSTOMERS
WHERE ADDRESS="Delhi"
```

**Output:**

![image](https://github.com/user-attachments/assets/f47837a4-f650-412f-977d-4f3b45e708fd)

**Question 7**
---
Write a query to display all the customers whose ID is the difference between the salesperson ID of Mc Lyon and 2001.
```sql
SELECT customer_id, cust_name, city, grade, salesman_id
FROM customer
WHERE customer_id = (
    SELECT salesman_id
    FROM salesman
    WHERE name = 'Mc Lyon'
) - 2001;
```

**Output:**

![image](https://github.com/user-attachments/assets/65b2f62b-4f9c-4e0a-91ca-a3752b653eb4)

**Question 8**
---
From the following tables, write a SQL query to find all the orders generated in New York city. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.
```sql
SELECT ord_no, purch_amt, ord_date, customer_id, orders.salesman_id
FROM orders
JOIN salesman ON orders.salesman_id = salesman.salesman_id
WHERE salesman.city = 'New York';
```

**Output:**

![image](https://github.com/user-attachments/assets/ae84f906-a066-4ff6-8b4d-8992ab68e585)

**Question 9**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is LESS than $2500.

Sample table: CUSTOMERS

```sql
SELECT * FROM CUSTOMERS
WHERE SALARY<2500
```

**Output:**

![image](https://github.com/user-attachments/assets/bc9932ff-2396-4818-a9ee-5c3bdc8e7482)

**Question 10**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is EQUAL TO $1500.

Sample table: CUSTOMERS
```sql
SELECT * FROM CUSTOMERS
WHERE SALARY=1500
```

**Output:**

![image](https://github.com/user-attachments/assets/fc63f288-f660-4c57-8491-fec8ac14a9b6)


## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
