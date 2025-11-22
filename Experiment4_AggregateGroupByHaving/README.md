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
How many patients are covered by each insurance company?

```sql
SELECT InsuranceCompany,count(*) as TotalPatients from Insurance
group by InsuranceCompany;
```

**Output:**

<img width="866" height="712" alt="image" src="https://github.com/user-attachments/assets/392fa5e7-aaef-4d9c-a55f-a8e9af3fcab4" />


**Question 2**
---
Write a SQL Query to find how many medications are prescribed for each patient?


```sql
select PatientID,count(*) as AvgMedications
from MedicalRecords
group by PatientID;
```

**Output:**

<img width="804" height="623" alt="image" src="https://github.com/user-attachments/assets/299ef27f-9428-4e64-9bcb-2602fc966fb3" />


**Question 3**
---
What is the count of male and female patients?

```sql
select Gender,count(*) as TotalPatients from Patients
group by gender;
```

**Output:**

<img width="694" height="363" alt="image" src="https://github.com/user-attachments/assets/3f2b57b1-b905-4a32-87c1-685d04be662a" />


**Question 4**
---
Write a SQL query to return the total number of rows in the 'customer' table where the city is not Noida.



```sql
select count(*) as COUNT
FROM customer
where city != 'Noida';
```

**Output:**

<img width="572" height="312" alt="image" src="https://github.com/user-attachments/assets/1a3861d1-0512-4941-997d-9859279a3224" />


**Question 5**
---
Write a SQL query to return the total number of rows in the 'customer' table where the city is Noida.



```sql
select count(*) as COUNT FROM customer
where city = 'Noida';
```

**Output:**

<img width="627" height="311" alt="image" src="https://github.com/user-attachments/assets/b4456c51-e123-4a9f-b4f8-d2cbbe9f3742" />


**Question 6**
---
Write a SQL query to calculate total purchase amount of all orders. Return total purchase amount.



```sql
select sum(purch_amt) as TOTAL from orders;
```

**Output:**

<img width="622" height="310" alt="image" src="https://github.com/user-attachments/assets/3a63370a-8d74-43a2-9de7-a35fd46aeec9" />


**Question 7**
---

Write a SQL query to find the Fruit with the lowest available quantity.



```sql
select name as fruit_name,inventory as lowest_quantity from fruits
order by inventory ASC
LIMIT 1;
```

**Output:**

<img width="775" height="307" alt="image" src="https://github.com/user-attachments/assets/e2eee3d4-2f9b-4c7a-bf51-aa3899325655" />

**Question 8**
---
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the average work hours for each date, and excludes dates where the average work hour is not less than 10.

```sql
select jdate,AVG(workhour) from employee1
group by jdate
having AVG(workhour) < 10; 
```

**Output:**

<img width="817" height="337" alt="image" src="https://github.com/user-attachments/assets/e3d718c7-f1ed-454e-a30b-cf79abc12d21" />


**Question 9**
---
Write the SQL query that accomplishes the selection of product which has lowest price in each category from the "products" table and includes only those products where the minimum price is less than 10.

```sql
select category_id,min(price) as Price from products
group by category_id
having Price < 10;
```

**Output:**

<img width="745" height="362" alt="image" src="https://github.com/user-attachments/assets/8a5b1e4f-227c-4d3b-a830-fb6dec7b4d19" />


**Question 10**
---
Write the SQL query that achieves the grouping of data by city, calculates the total income for each city, and includes only those cities where the total income sum is greater than 200,000.

```sql
select city,sum(income) as Income from employee
group by city
having Income > 200000;
```

**Output:**

<img width="730" height="557" alt="image" src="https://github.com/user-attachments/assets/d4312e22-12a4-46b8-87f5-411e6052b89d" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
