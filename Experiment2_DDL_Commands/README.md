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
Write a SQL query to add a column named Date_of_birth as Date in the Student_details table.

```sql
ALTER TABLE Student_details 
ADD COLUMN Date_of_birth Date;
```

**Output:**

<img width="1106" height="411" alt="image" src="https://github.com/user-attachments/assets/7fad06e1-a495-42d6-b81a-a0c86ecbed7c" />


**Question 2**
---
Insert all books from Out_of_print_books into Books

Table attributes are ISBN, Title, Author, Publisher, YearPublished

```sql
INSERT INTO Books (ISBN, Title, Author, Publisher, YearPublished)
SELECT ISBN, Title, Author, Publisher, YearPublished FROM Out_of_print_books;

```

**Output:**

<img width="1106" height="322" alt="image" src="https://github.com/user-attachments/assets/47ce747c-63d3-425e-8ee9-51df814f488e" />


**Question 3**
---
Create a table named Invoices with the following constraints:

InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
DueDate as DATE should be greater than the InvoiceDate.
Amount as REAL should be greater than 0.

```sql
CREATE TABLE Invoices(
    InvoiceID INTEGER PRIMARY KEY,
    InvoiceDate Date,
    DueDate Date,
    Amount REAL,
    CHECK(DueDate > InvoiceDate),
    CHECK(Amount > 0)
);
```

**Output:**

<img width="1108" height="308" alt="image" src="https://github.com/user-attachments/assets/49c662e3-2a10-4259-93a1-34f3ae6d74f5" />


**Question 4**
---
Write a SQL query to modify the Student_details table by adding a new column Email of type VARCHAR(50) and updating the column MARKS to have a default value of 0.
```sql
ALTER TABLE Student_details ADD COLUMN Email VARCHAR(50);
ALTER TABLE Student_details ADD COLUMN MARKS INTEGER DEFAULT 0; 


```

**Output:**

<img width="1111" height="266" alt="image" src="https://github.com/user-attachments/assets/f7f121fd-0463-4222-9f8f-c3caf5820df8" />


**Question 5**
---
Create a table named Employees with the following constraints:

EmployeeID should be the primary key.
FirstName and LastName should be NOT NULL.
Email should be unique.
Salary should be greater than 0.
DepartmentID should be a foreign key referencing the Departments table.

```sql
CREATE TABLE Employees(
    EmployeeID INTEGER PRIMARY KEY,
    FirstName TEXT NOT NULL,
    LastName TEXT NOT NULL,
    Email TEXT Unique,
    Salary REAL CHECK(Salary > 0),
    DepartmentID INTEGER,
    FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID)
);
```

**Output:**

<img width="1105" height="476" alt="image" src="https://github.com/user-attachments/assets/6a83e0c2-e8bd-48ac-a38d-709bf0bca590" />


**Question 6**
---
Insert a product with ProductID 104, Name Tablet, and Category Electronics into the Products table, where Price and Stock should use default values

```sql
INSERT INTO Products (ProductID, Name, Category)
values (104,'Tablet','Electronics');
```

**Output:**

<img width="1108" height="263" alt="image" src="https://github.com/user-attachments/assets/c4df983a-f7ae-4a39-9e47-8ff5740ef74a" />


**Question 7**
---
Insert the following customers into the Customers table:

CustomerID  Name         Address     City        ZipCode
----------  -----------  ----------  ----------  ----------
302         Laura Croft  456 Elm St  Seattle     98101
303         Bruce Wayne  789 Oak St  Gotham      10001

```sql
INSERT INTO Customers (CustomerID,Name,Address,City,ZipCode)
values (302,'Laura Croft','456 Elm St','Seattle',98101),
    (303,'Bruce Wayne','789 Oak St','Gotham',10001);
```

**Output:**

<img width="1106" height="420" alt="image" src="https://github.com/user-attachments/assets/d2086438-768d-47de-bb7f-7d146f344a2e" />


**Question 8**
---
Create a table named Bonuses with the following constraints:
BonusID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
BonusAmount as REAL should be greater than 0.
BonusDate as DATE.
Reason as TEXT should not be NULL.

```sql
CREATE TABLE Bonuses(
    BonusID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    BonusAmount Real Check(BonusAmount > 0),
    BonusDate DATE,
    Reason TEXT NOT NULL,
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID)
);
```

**Output:**

<img width="1150" height="274" alt="image" src="https://github.com/user-attachments/assets/91534685-23de-4ae4-9e37-fe6e66611b9e" />


**Question 9**
---
Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should cascade updates and deletes.
item_desc and rate should not accept NULL.

```sql
CREATE TABLE item(
    item_id TEXT PRIMARY KEY,
    item_desc TEXT NOT NULL,
    rate INTEGER NOT NULL,
    icom_id TEXT CHECK(LENGTH(icom_id) = 4),
    FOREIGN KEY (icom_id) REFERENCES company(com_id)
        ON UPDATE CASCADE
        ON DELETE CASCADE
    
)
```

**Output:**

<img width="1147" height="359" alt="image" src="https://github.com/user-attachments/assets/11431605-1cb1-4cbc-91f0-fb30a38a1cc3" />


**Question 10**
---
Create a table named Events with the following columns:

EventID as INTEGER
EventName as TEXT
EventDate as DATE

```sql
CREATE TABLE Events(
    EventID INTEGER,
    EventName TEXT,
    EventDate DATE
);
```

**Output:**

<img width="1150" height="374" alt="image" src="https://github.com/user-attachments/assets/9d9b707e-8c10-42c2-a7db-f787e97413b4" />

## COMPLETION GRADE

<img width="1408" height="222" alt="image" src="https://github.com/user-attachments/assets/378a6136-eb5a-4f6c-8bad-a0e735009b69" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
