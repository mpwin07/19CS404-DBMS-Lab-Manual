# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
What is the most common diagnosis among patients?
```sql
select Diagnosis, count(*) as DiagnosisCount from MedicalRecords
group by Diagnosis
order by DiagnosisCount DESC
limit 1 
```

**Output:**

![image](https://github.com/user-attachments/assets/0820458e-1cda-4d48-9c87-89c9c901fccf)

**Question 2**
---
How many appointments are scheduled for each doctor?
```sql
select DoctorID , count(*) as TotalAppointments from Appointments
group by DoctorID
```

**Output:**

![image](https://github.com/user-attachments/assets/2615a89a-6928-4fb4-8361-8a290a09036a)

**Question 3**
---
What is the average dosage prescribed for each medication?
```sql
Select Medication , AVG(Dosage) AS AvgDosage from Prescriptions
group by Dosage
order by Medication ASC
```

**Output:**

![image](https://github.com/user-attachments/assets/c2e36f95-42cc-4f67-95ec-9a9108ec54b0)

**Question 4**
---
Write a SQL query to find the total income of employees aged 40 or above.

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
```sql
SELECT sum(income) AS total_income from employee
where age>=40
```

**Output:**

![image](https://github.com/user-attachments/assets/95db1051-0235-4b6b-8189-f2c3738369f0)

**Question 5**
---
Write a SQL query to find the number of employees who are having the same age removing the duplicate values.

Sample table: employee


```sql
select count(DISTINCT age) AS "COUNT" from employee
```

**Output:**

![image](https://github.com/user-attachments/assets/d3cf6a89-bdff-4fef-886a-682c85112209)

**Question 6**
---
Write the SQL query that achieves the selection of category and calculates the sum of the product of price and category ID as Revenue for each category from the "products" table, and includes only those products where the total revenue is greater than 25.
```sql
select category_id, sum(price*category_id) as Revenue from products
group by category_id
having Revenue>25
```

**Output:**

![image](https://github.com/user-attachments/assets/6c174003-9f77-48fe-a481-4727bad496b5)

**Question 7**
---
Write a SQL query to determine the number of customers who received at least one grade for their activity.

Sample table: customer
```sql
select count(*) as "COUNT" from customer
where grade>=1
```

**Output:**

![image](https://github.com/user-attachments/assets/5732eadf-44b3-4378-923b-cdbf1d040247)

**Question 8**
---
Write the SQL query that accomplishes the grouping of data by age, calculates the maximum income for each age group, and includes only those age groups where the maximum income is greater than 2,000,000.
```sql
select age , MAX(income) AS "MAX(income)" from employee
group by age
having "MAX(income)">=2000000
```

**Output:**

![image](https://github.com/user-attachments/assets/387c84b5-c998-4c7e-b586-3e95d08d893f)

**Question 9**
---
Write a SQL query to find the youngest employee in the company?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER

```sql
select name as Employee_Name , min(age) AS Age from employee
```

**Output:**

![image](https://github.com/user-attachments/assets/bf225b77-5cb7-41c5-90b7-d87a9f5ea115)

**Question 10**
---
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the average work hours for each date, and excludes dates where the average work hour is not less than 10.
```sql
select jdate, avg(workhour) as "AVG(workhour)" from employee1
group by jdate
having "AVG(workhour)"<=10
```

**Output:**

![image](https://github.com/user-attachments/assets/85e9a65d-daa5-4e3c-933a-4c194a6576b7)


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
