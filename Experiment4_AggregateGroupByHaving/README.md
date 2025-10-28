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
Write a SQL query to calculate the total number of working hours of all employees

```sql
select sum(workhour) as "Total working hours"
from employee1

```

**Output:**

<img width="543" height="377" alt="image" src="https://github.com/user-attachments/assets/51144c43-6f11-48fe-a702-b8fedf00a497" />


**Question 2**
---
Write a SQL query to calculate the average purchase amount of all orders. Return average purchase amount.-- Paste Question 2 here

```sql
select avg(purch_amt) as AVERAGE
from orders
```

**Output:**

<img width="396" height="381" alt="image" src="https://github.com/user-attachments/assets/64c8e503-50ca-48e4-9215-528d1533a65b" />


**Question 3**
---
Write a SQL query to find how many employees have an income greater than 50K?

```sql
select count(*) as employees_count
from employee
where income > 50
```

**Output:**

<img width="512" height="382" alt="image" src="https://github.com/user-attachments/assets/0020ed55-5d14-4ca0-bb18-d3904027fe09" />


**Question 4**
---
What is the count of male and female patients?

```sql
select gender, count(*) as TotalPatients
from  Patients 
group by gender
```

**Output:**

<img width="665" height="435" alt="image" src="https://github.com/user-attachments/assets/fb433276-c45d-4a4c-8088-690872c48846" />


**Question 5**
---
What is the total number of appointments scheduled for each day?

```sql
select date(AppointmentDateTime) as AppointmentDate, count(*) as TotalAppointments
from Appointments
group by date(AppointmentDateTime)
```

**Output:**

<img width="837" height="725" alt="image" src="https://github.com/user-attachments/assets/6b9dacf7-fc29-4a0e-803b-b820242e6f44" />


**Question 6**
---
How many appointments are scheduled for each doctor?

```sql
select DoctorID, count(*) as TotalAppointments
from Appointments
group by DoctorID 
```

**Output:**

<img width="763" height="705" alt="image" src="https://github.com/user-attachments/assets/e38ebd78-2b9f-4777-9b4f-66419d37fa23" />


**Question 7**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the total work hours for each occupation, and excludes occupations where the total work hour sum is not greater than 20.

```sql
select occupation, sum(workhour) as "SUM(workhour)"
from employee1
group by occupation
having workhour < 20
```

**Output:**

<img width="656" height="538" alt="image" src="https://github.com/user-attachments/assets/5511d5da-69ee-4f10-bc36-2f6db41e1e43" />


**Question 8**
---
Write the SQL query that achieves the grouping of data by city, calculates the total income for each city, and includes only those cities where the total income sum is greater than 200,000.

```sql
select city, sum(income) as Income
from employee
group by city
having income > 200000
```

**Output:**

<img width="630" height="607" alt="image" src="https://github.com/user-attachments/assets/9c5d5417-bbaf-40c0-a3d0-51bcec2fd2e7" />


**Question 9**
---
Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and includes only those age groups where the minimum income is less than 400,000.

```sql
select age, min(income) as "MIN(income)"
from employee
group by age
having income < 400000
```

**Output:**

<img width="653" height="456" alt="image" src="https://github.com/user-attachments/assets/6d3e4e77-fc6e-4110-9deb-f6e68cf467f3" />


**Question 10**
---
Write the SQL query that accomplishes the grouping of data by age intervals using the expression (age/5)5, calculates the minimum age for each group, and excludes groups where the minimum age is not less than 25.

```sql
select (age/5)*5 as age_group, min(age) as  "MIN(age)"
from customer1
group by (age/5)*5
having age<25
```

**Output:**

<img width="582" height="380" alt="image" src="https://github.com/user-attachments/assets/ba5d9c94-b565-4cfe-950e-e962edd371a4" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
