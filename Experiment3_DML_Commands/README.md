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
Write a SQL query to calculate the discount amount for each product. Return product_id, original_price, discount_percentage, and discount_amount.

```sql
SELECT product_id,  
       original_price, 
       discount_percentage,  
       original_price * discount_percentage AS discount_amount
       
FROM Products
```

**Output:**

<img width="1220" height="310" alt="image" src="https://github.com/user-attachments/assets/22f81723-c3c8-410b-8c6e-b56afbed52ab" />


**Question 2**
---
Write a SQL query to locate the details of customers with grade values above 100. Return customer_id, cust_name, city, grade, and salesman_id.

```sql
SELECT customer_id, cust_name, city, grade, salesman_id
FROM customer
WHERE grade>100;
```

**Output:**

<img width="1191" height="453" alt="image" src="https://github.com/user-attachments/assets/20dde793-19e2-46d6-b67f-c033165a037b" />


**Question 3**
---
Write a SQL query to delete a specific doctor from Doctors table whose ID is 1.

```sql
DELETE FROM Doctors
WHERE doctor_id = 1;

```

**Output:**

<img width="1185" height="286" alt="image" src="https://github.com/user-attachments/assets/565260cd-2278-4bbd-a4f6-f5944b176411" />


**Question 4**
---
Write a SQL statement to get the EmployeeID, FirstName, BirthDate, Age from employees table whose age is older than 50.

```sql
SELECT 
  EmployeeID,
  FirstName,
  BirthDate,
  CAST((CAST(strftime('%Y%m%d','2023-12-30') AS INTEGER) 
        - CAST(strftime('%Y%m%d', BirthDate) AS INTEGER)) / 10000 AS INTEGER) AS age
FROM employees
WHERE CAST((CAST(strftime('%Y%m%d','2023-12-30') AS INTEGER) 
            - CAST(strftime('%Y%m%d', BirthDate) AS INTEGER)) / 10000 AS INTEGER) > 50;
```

**Output:**

<img width="918" height="595" alt="image" src="https://github.com/user-attachments/assets/e5e4f494-0a04-4291-b581-58f855ad8e21" />


**Question 5**
---
Write a SQL query to categorize decimal as 'High', 'Medium', or 'Low' based on whether it is greater than 100, between 50 and 100, or less than 50 in the Calculations table

```sql
SELECT id,decimal,

CASE
WHEN decimal >= 100 then 'High'
WHEN decimal BETWEEN 50 AND 100 then 'Medium'
ELSE 'Low'   
   
   
END AS category   
FROM Calculations
```

**Output:**

<img width="728" height="496" alt="image" src="https://github.com/user-attachments/assets/2c2b6129-8e4e-48c1-8b07-0316997ec544" />


**Question 6**
---
Write a SQL query to find customers who are either from the city 'New York' or who do not have a grade greater than 100. Return customer_id, cust_name, city, grade, and salesman_id.

```sql
SELECT customer_id, cust_name, city, grade, salesman_id
FROM customer
WHERE city = 'New York'
   OR grade <=100;
```

**Output:**

<img width="1170" height="431" alt="image" src="https://github.com/user-attachments/assets/86738659-b32a-44a8-b3cd-1894f72b21a3" />


**Question 7**
---
Write a SQL statement to retrieve city(column name) of all customers from customers table without any repeats.

```sql
SELECT DISTINCT city
FROM customers
```

**Output:**

<img width="350" height="547" alt="image" src="https://github.com/user-attachments/assets/2bdff354-9071-4b03-a8a5-1eccafdc37e6" />


**Question 8**
---
Write a SQL query to Delete customers from 'customer' table where 'AGENT_CODE' is either 'A003' or 'A008'.

```sql
DELETE FROM customer
WHERE AGENT_CODE  IN ('A003' , 'A008');
```

**Output:**

<img width="627" height="938" alt="image" src="https://github.com/user-attachments/assets/3e5e72a6-df36-4150-a3fa-21923a427e76" />


**Question 9**
---
Write a SQL query to Delete customers with 'GRADE' 2 and 'CUST_NAME' starting with 'M', and whose 'PAYMENT_AMT' is less than 3000

```sql
DELETE FROM customer
WHERE GRADE = 2
   AND CUST_NAME LIKE 'M%'
   AND PAYMENT_AMT <= 3000;
```

**Output:**

<img width="1063" height="153" alt="image" src="https://github.com/user-attachments/assets/84e4eaa8-774c-4b74-ab48-19e942f9ec3c" />


**Question 10**
---
Write a SQL query to Select all patients who was admitted in hospital for more than 3 days.

```sql
SELECT first_name,
       last_name,   
       (julianday(discharge_date)-julianday(admission_date)+1) AS no_of_days
       
FROM patients
WHERE (julianday(discharge_date)-julianday(admission_date)+1) > 3
```

**Output:**

<img width="656" height="326" alt="image" src="https://github.com/user-attachments/assets/c81e78e7-2a23-45a4-8f32-3f392a7cf21e" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
