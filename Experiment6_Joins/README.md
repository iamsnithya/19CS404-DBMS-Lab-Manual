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
From the following tables write a SQL query to locate those salespeople who do not live in the same city where their customers live and have received a commission of more than 12% from the company. Return Customer Name, customer city, Salesman, salesman city, commission.  



```sql
select c.cust_name AS "Customer Name", c.city AS "city", s.name AS "Salesman", s.city AS "city", s.commission
from customer c
join salesman s
  on c.salesman_id = s.salesman_id
where c.city <> s.city
  and s.commission > 0.12
```

**Output:**

<img width="1220" height="532" alt="image" src="https://github.com/user-attachments/assets/89fd00a6-d9bc-415a-9f1f-eb08563528ef" />


**Question 2**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the first name from the "doctors" table (aliased as "doctor_name"), with an inner join on the "doctor_id" column and a condition filtering for patients with a date of birth after '1990-01-01'.



```sql
select p.first_name as patient_name, d.first_name as doctor_name
from patients as p
inner join doctors as d on p.doctor_id = d.doctor_id
where p.date_of_birth > '1990-01-01'
```

**Output:**

<img width="653" height="383" alt="image" src="https://github.com/user-attachments/assets/28a3e8ba-0c2f-45f1-89ba-1ca4b50a3095" />


**Question 3**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and all columns from the "test_results" table (aliased as "t"), with an inner join on the "patient_id" column.



```sql
select patient_name.first_name as patient_name, t.*
from patients as patient_name
inner join test_results as t on patient_name.patient_id = t.patient_id
```

**Output:**

<img width="1250" height="421" alt="image" src="https://github.com/user-attachments/assets/869bc7a4-0f54-4ebd-8a0e-3dd634cbb02b" />


**Question 4**
---
Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), with a left join on the "salesman_id" column and a condition filtering for customers in the city 'London'.



```sql
select DISTINCT s.name
from salesman s
left join customer c
  on s.salesman_id = c.salesman_id
where c.city = 'London'
```

**Output:**

<img width="385" height="417" alt="image" src="https://github.com/user-attachments/assets/2dc85016-d863-40e4-9188-74a968701f3a" />


**Question 5**
---
Write the SQL query that achieves the selection of the first name from the "patients" table and all columns from the "surgeries" table, with an inner join on the "patient_id" column and a condition filtering for patients with a date of birth after '1990-01-01'.



```sql
select p.first_name, s.*
from patients p
inner join surgeries s on p.patient_id = s.patient_id
where p.date_of_birth > '1990-01-01'
```

**Output:**

<img width="1248" height="361" alt="image" src="https://github.com/user-attachments/assets/83a17f1d-40b3-4fe5-90fa-61dba66ae929" />


**Question 6**
---
Write the SQL query that achieves the selection of the "nurse_id" from the "nurses" table (aliased as "n") and the "department_name" from the "departments" table, with an inner join on the "department_id" column and conditions filtering for a nurse with the first name 'David' and last name 'Moore'.



```sql
select n.nurse_id, d.department_name
from nurses as n
inner join departments as d on n.department_id = d.department_id
where n.first_name = 'David' and n.last_name = 'Moore'
```

**Output:**

<img width="596" height="380" alt="image" src="https://github.com/user-attachments/assets/de6ebd25-9f26-41fd-8618-e4396a5efa1f" />


**Question 7**
---
Write the SQL query that achieves the selection of all columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column and a condition filtering for salesmen with the name 'Mc Lyon'.



```sql
select c.*
from customer as c
left join salesman as s on c.salesman_id = s.salesman_id
where s.name = 'Mc Lyon'
```

**Output:**

<img width="1228" height="361" alt="image" src="https://github.com/user-attachments/assets/7ce58986-f8e2-46be-a00c-bdcb4e8e92a9" />


**Question 8**
---
Write the SQL query that achieves the selection of all columns from the "nurses" table (aliased as "n") and the "department_name" column from the "departments" table, with an inner join on the "department_id" column.



```sql
select n.*, d.department_name
from nurses as n
inner join departments as d on n.department_id = d.department_id
```

**Output:**

<img width="1285" height="476" alt="image" src="https://github.com/user-attachments/assets/2115c373-6a11-4e6c-b5f6-125e5dfeb674" />


**Question 9**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name"), with an inner join on the "doctor_id" column and conditions filtering for patients whose doctor has the first name 'Emily', last name 'Johnson', and a non-null discharge date.



```sql
select patient_name.first_name as patient_name
from patients as patient_name
inner join doctors as d on patient_name.doctor_id = d.doctor_id
where d.first_name = 'Emily'
  and d.last_name = 'Johnson'
  and patient_name.discharge_date IS not null
```

**Output:**

<img width="393" height="362" alt="image" src="https://github.com/user-attachments/assets/3f0975a6-2f9e-4d8f-a3ca-87e7e0626f5c" />


**Question 10**
---
Write the SQL query that accomplishes the selection of the first name from the "patients" table and all columns from the "surgeries" table, with an inner join on the "patient_id" column and a condition filtering for patients with the first name 'Alice'.



```sql
select p.first_name, s.*
from patients p
inner join surgeries s
  on p.patient_id = s.patient_id
where p.first_name = 'Alice'
```

**Output:**

<img width="1236" height="357" alt="image" src="https://github.com/user-attachments/assets/78d081e8-8a13-446c-802c-a69feaccf21f" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
