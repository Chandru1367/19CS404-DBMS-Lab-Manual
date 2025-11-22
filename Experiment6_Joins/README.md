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
Write a SQL statement to join the tables salesman, customer and orders so that the same column of each table appears once and only the relational rows are returned. 

```sql
SELECT 
  o.ord_no, 
  o.purch_amt, 
  o.ord_date, 
  c.cust_name, 
  c.city AS customer_city, 
  c.grade, 
  s.name AS salesman_name, 
  s.city AS salesman_city, 
  s.commission
FROM orders o
INNER JOIN customer c ON o.customer_id = c.customer_id
INNER JOIN salesman s ON o.salesman_id = s.salesman_id;
```

**Output:**

<img width="1232" height="741" alt="image" src="https://github.com/user-attachments/assets/89164418-eb53-4a5c-825b-7346fcc0160b" />


**Question 2**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name"), with an inner join on the "patient_id" column and a condition filtering for test results with the test name 'Blood Pressure'.

```sql
SELECT 
    p.first_name AS patient_name
FROM 
    patients AS p
INNER JOIN 
    test_results AS t
ON 
    p.patient_id = t.patient_id
WHERE 
    t.test_name = 'Blood Pressure';

```

**Output:**

<img width="654" height="361" alt="image" src="https://github.com/user-attachments/assets/a8d72a6b-8fcd-43b1-a058-21b06dfba263" />


**Question 3**
---
 From the following tables write a SQL query to find the salesperson(s) and the customer(s) he represents. Return Customer Name, city, Salesman, commission.

```sql
SELECT c.cust_name AS "Customer Name", c.city,
       s.name AS "Salesman", s.commission
FROM customer c
JOIN salesman s ON c.salesman_id = s.salesman_id;
```

**Output:**

<img width="1216" height="804" alt="image" src="https://github.com/user-attachments/assets/253d0e8b-50e8-49eb-a2ed-36e9c781ec6c" />


**Question 4**
---
From the following tables write a SQL query to locate those salespeople who do not live in the same city where their customers live and have received a commission of more than 12% from the company. Return Customer Name, customer city, Salesman, salesman city, commission.  



```sql
SELECT 
  c.cust_name AS 'Customer Name', 
  c.city AS city, 
  s.name AS Salesman, 
  s.city AS city, 
  s.commission
FROM customer c
JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE c.city <> s.city 
  AND s.commission > 0.12;
```

**Output:**

<img width="1257" height="560" alt="image" src="https://github.com/user-attachments/assets/a81cc24a-870c-4276-b3f2-1291117c3636" />


**Question 5**
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
INNER JOIN 
    customer c
ON 
    o.customer_id = c.customer_id
INNER JOIN 
    salesman s
ON 
    o.salesman_id = s.salesman_id;
```

**Output:**

<img width="1223" height="719" alt="image" src="https://github.com/user-attachments/assets/9702bfff-5001-4458-88ec-9bc831d9f568" />


**Question 6**
---
Write the SQL query that achieves the selection of all columns from the "patients" table and the specialization from the "doctors" table (aliased as "doctor_specialization"), with an inner join on the "doctor_id" column.


```sql
SELECT 
    p.*,
    d.specialization AS doctor_specialization
FROM 
    patients AS p
INNER JOIN 
    doctors AS d
ON 
    p.doctor_id = d.doctor_id;

```

**Output:**

<img width="1288" height="443" alt="image" src="https://github.com/user-attachments/assets/56fd7aef-d7dc-4ffb-9705-fec3c0f7fecc" />


**Question 7**
---
From the following tables write a SQL query to display the customer name, customer city, grade, salesman, salesman city. The results should be sorted by ascending customer_id.  



```sql
SELECT 
    c.cust_name,
    c.city AS city,
    c.grade,
    s.name AS Salesman,
    s.city AS city
FROM 
    customer AS c
INNER JOIN 
    salesman AS s
ON 
    c.salesman_id = s.salesman_id
ORDER BY 
    c.customer_id ASC;

```

**Output:**

<img width="1275" height="711" alt="image" src="https://github.com/user-attachments/assets/f64af113-92c0-455f-a50b-a93b186b27f5" />


**Question 8**
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
    customer AS c
LEFT JOIN 
    orders AS o
ON 
    c.customer_id = o.customer_id
WHERE 
    c.city = 'London';

```

**Output:**

<img width="1253" height="357" alt="image" src="https://github.com/user-attachments/assets/5a94e986-4c84-4b5a-83e2-a74414365695" />


**Question 9**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name"), with an inner join on the "doctor_id" column and conditions filtering for patients whose doctor has the first name 'Emily', last name 'Johnson', and a non-null discharge date.


```sql
SELECT 
    p.first_name AS patient_name
FROM 
    patients AS p
INNER JOIN 
    doctors AS d
ON 
    p.doctor_id = d.doctor_id
WHERE 
    d.first_name = 'Emily'
    AND d.last_name = 'Johnson'
    AND p.discharge_date IS NOT NULL;

```

**Output:**

<img width="596" height="362" alt="image" src="https://github.com/user-attachments/assets/d8d2cc3d-2a25-4bed-aed7-bb79cb7d47fc" />


**Question 10**
---
Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column and a condition filtering for orders with a purchase amount greater than 1000.



```sql
SELECT 
    c.cust_name,
    o.ord_no,
    o.ord_date,
    o.purch_amt
FROM 
    customer AS c
LEFT JOIN 
    orders AS o
ON 
    c.customer_id = o.customer_id
WHERE 
    o.purch_amt > 1000;

```

**Output:**

<img width="1235" height="663" alt="image" src="https://github.com/user-attachments/assets/0d1f38f8-1ea6-46c7-8398-ad3a284c3129" />


## RESULT

Thus, the SQL queries to implement different types of joins have been executed successfully.
