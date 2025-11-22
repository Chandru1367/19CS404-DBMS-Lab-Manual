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
Write a SQL statement to Change the category to 'Household' where product name contains 'Detergent' in the products table.

```sql
update Products 
set category = 'Household'
where product_name lIKE '%Detergent%';
```

**Output:**

<img width="1105" height="571" alt="image" src="https://github.com/user-attachments/assets/c5d1ed1f-8d73-435a-9d1d-29e0091ce1dd" />


**Question 2**
---
Write a SQL statement to Update the grade of all customers in Chennai city as  5. 

Customer table (customer_id,cust_name,city,grade,salesman_id)

```sql
update Customer
set grade = '5'
where city = 'Chennai';
```

**Output:**

<img width="1105" height="542" alt="image" src="https://github.com/user-attachments/assets/058cbab1-5bfa-4af7-be91-419639df9bf7" />


**Question 3**
---
Write a SQL statement to change the EMAIL and COMMISSION_PCT column of the following EMPLOYEES table with 'not available' and 0.55 for those employees whose DEPARTMENT_ID is 110.
```sql
update Employees
set EMAIL = "not available",COMMISSION_PCT = "0.55"
WHERE DEPARTMENT_ID = 110;
```

**Output:**

<img width="1108" height="435" alt="image" src="https://github.com/user-attachments/assets/27f12732-6ee1-4086-ac66-ff8ef63ef3f3" />


**Question 4**
---
Write a SQL statement to Increase quantity of all products by 10% to adjust for surplus stock counted



```sql
UPDATE Products
set quantity = quantity * 1.10;
```

**Output:**

<img width="1109" height="718" alt="image" src="https://github.com/user-attachments/assets/cd6c5334-3383-43de-a343-2d2c4dbf09e4" />


**Question 5**
---
Write a SQL statement to Increase the selling price by 10% for all products in the 'Bakery' category in the products table.

```sql
update Products
set sell_price = sell_price * 1.10
where category = 'Bakery';
```

**Output:**

<img width="1106" height="599" alt="image" src="https://github.com/user-attachments/assets/6c761c23-c739-4bde-8fe5-080deb7e6de1" />


**Question 6**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is less than 2.



```sql
delete from customer
where GRADE < 2;
```

**Output:**

<img width="903" height="636" alt="image" src="https://github.com/user-attachments/assets/d845782a-0575-4a38-bb74-d3ca8b0a6c95" />


**Question 7**
---
Write a SQL query to Delete a Specific Surgery which was made on 28th Feb 2024.

```sql
delete from Surgeries
where surgery_date = '2024-02-28';
```

**Output:**

<img width="1105" height="442" alt="image" src="https://github.com/user-attachments/assets/5d42b430-b058-4dc8-8793-406f9651be65" />


**Question 8**
---
Write a SQL query to delete a doctor from Doctors table whose Specialization is 'Pediatrics' and First name is 'Michael'.

```sql
delete from Doctors
where specialization = 'Pediatrics' and first_name = 'Michael';
```

**Output:**

<img width="1112" height="437" alt="image" src="https://github.com/user-attachments/assets/e8188a61-7ad2-4dff-8cd0-90fae4238031" />


**Question 9**
---
Write a SQL query to Delete customers from 'customer' table where 'CUST_COUNTRY' is neither 'India' nor 'USA'.

```sql
delete from Customer
where CUST_COUNTRY NOT IN  ('India' , 'USA');
```

**Output:**

<img width="1118" height="632" alt="image" src="https://github.com/user-attachments/assets/a1452704-322b-45e2-949d-534c0e42a062" />


**Question 10**
---
Write a SQL query to remove rows from the table 'customer' with the following condition -

```sql
DELETE FROM Customer 
where CUST_COUNTRY = 'India' and CUST_CITY != 'Chennai';
```

**Output:**

<img width="1245" height="705" alt="image" src="https://github.com/user-attachments/assets/950c0dba-e770-417a-9c70-b1215ebd4906" />

## COMPLETION GRADE :

<img width="1395" height="254" alt="image" src="https://github.com/user-attachments/assets/6347e81f-02ce-4a4e-8094-5e30f5ddee57" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
