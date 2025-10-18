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
---
Write a SQL Query  to change the name of attribute "name" to "first_name"  and add mobilenumber as number ,DOB as Date in the table Companies. 


```sql
ALTER TABLE Companies
RENAME COLUMN name TO first_name;

ALTER TABLE Companies
ADD mobilenumber number;

ALTER TABLE Companies
ADD DOB Date;
```

**Output:**

<img width="1165" height="301" alt="image" src="https://github.com/user-attachments/assets/2b3fcca5-a329-45e7-b6b7-3f1087a85129" />


**Question 2**
---
Create a table named Shipments with the following constraints:
ShipmentID as INTEGER should be the primary key.
ShipmentDate as DATE.
SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID).
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```sql
CREATE TABLE Shipments (
    ShipmentID INT PRIMARY KEY,
    ShipmentDate DATE,
    SupplierID INT ,
    OrderID INT ,
    FOREIGN KEY (SupplierID) REFERENCES Suppliers(SupplierID),
    FOREIGN KEY (OrderID) REFERENCES Orders(OrderID)
);

```

**Output:**

<img width="1182" height="197" alt="image" src="https://github.com/user-attachments/assets/6d911304-529d-4915-9af0-5f38d3561b82" />


**Question 3**
---
Insert the below data into the Employee table, allowing the Department and Salary columns to take their default values.

```
EmployeeID  Name         Position
----------  -----------  ----------
4           Emily White  Analyst

Note: The Department and Salary columns will use their default values.
```

```sql
INSERT INTO Employee(EmployeeID,Name, Position)
VALUES (4,'Emily White','Analyst')
```

**Output:**

<img width="782" height="257" alt="image" src="https://github.com/user-attachments/assets/1448cde1-db89-470b-b2ab-d31c0b73de3a" />


**Question 4**
---
Write a SQL Query  to Rename attribute "name" to "first_name"  and add mobilenumber as number ,DOB as Date,State as varchar(30) in the table Companies.

```sql
ALTER TABLE Companies
RENAME COLUMN name TO first_name;

ALTER TABLE Companies
ADD mobilenumber number;

ALTER TABLE Companies
ADD DOB Date;

ALTER TABLE Companies
ADD State varchar(30);
```

**Output:**

<img width="1187" height="307" alt="image" src="https://github.com/user-attachments/assets/6f9d7571-a5e3-4b1a-bfc6-5b6cf8ecf51c" />


**Question 5**
---
Create a table named Orders with the following constraints:
OrderID as INTEGER should be the primary key.
OrderDate as DATE should be not NULL.
CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).

```sql
CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    OrderDate DATE NOT NULL,
    CustomerID INT,
    FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
);
```

**Output:**

<img width="1323" height="223" alt="image" src="https://github.com/user-attachments/assets/deda3f59-cf6d-4179-9b68-eda0f74bb923" />


**Question 6**
---
Insert the below data into the Customers table, allowing the City and ZipCode columns to take their default values.
```
CustomerID  Name          Address
----------  ------------  ----------
304         Peter Parker  Spider St      

Note: The City and ZipCode columns will use their default values.
```

```sql
INSERT INTO Customers(CustomerID,Name,Address)
VALUES(304,'Peter Parker','Spider St')
```

**Output:**

<img width="772" height="258" alt="image" src="https://github.com/user-attachments/assets/9ec9a429-ff2b-4567-9eb6-506fb8561742" />


**Question 7**
---
Create a table named Products with the following columns:

ProductID as INTEGER
ProductName as TEXT
Price as REAL
Stock as INTEGER

```sql
CREATE TABLE Products(
    ProductID INTEGER,
    ProductName TEXT,
    Price REAL,
    Stock INTEGER
);
```

**Output:**

<img width="1091" height="247" alt="image" src="https://github.com/user-attachments/assets/478dd613-d42d-48c7-9909-d88bc18c589d" />


**Question 8**
---
Create a table named Customers with the following columns:

CustomerID as INTEGER
Name as TEXT
Email as TEXT
JoinDate as DATETIME

```sql
CREATE TABLE Customers(
    CustomerID INTEGER,
    Name TEXT,
    Email TEXT,
    JoinDate DATETIME
);
```

**Output:**

<img width="1082" height="237" alt="image" src="https://github.com/user-attachments/assets/a17d86f6-7f96-42ea-b809-90cb333775f7" />


**Question 9**
---
Write a SQL Query for inserting the below values in the table Customers
```
ID               NAME             AGE  ADDRESS     SALARY      
---------------  ---------------  ---  ----------  ----------  
1                Ramesh           32   Ahmedabad   2000
2                Khilan           25   Delhi       1500
3                Kaushik          23   Kota        2000
```
```sql
INSERT INTO Customers(ID,Name,AGE,ADDRESS,SALARY)
VALUES
(1,'Ramesh',32,'Ahmedabad',2000),
(2,'Khilan',25,'Delhi',1500),
(3,'Kaushik',23,'Kota',2000);

```


**Output:**

<img width="986" height="232" alt="image" src="https://github.com/user-attachments/assets/dd34ffc6-457b-4dc7-8b04-5ecf291dc638" />


**Question 10**
---
Create a table named Orders with the following columns:

OrderID as INTEGER
OrderDate as TEXT
CustomerID as INTEGER

```sql
CREATE TABLE Orders (
    OrderID INTEGER,
    OrderDate TEXT,
    CustomerID INTEGER
);
```

**Output:**

<img width="1222" height="292" alt="image" src="https://github.com/user-attachments/assets/f79b3df4-3f27-4add-aedd-5b2b364711d0" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
