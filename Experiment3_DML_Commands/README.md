# Experiment 3: DML Commands

### Name: Aravind Kumar SS
### Reg No: 212223110004

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
For products with a profit % less than 30% of selling price, update the selling price to provide a profit margin of 35% over cost price of the product in the products table.

PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT

```sql
update products
set sell_price= cast(cost_price*1.35 as integer)
where (sell_price-cost_price)/sell_price <0.3;
```

**Output:**

<img width="1230" height="564" alt="image" src="https://github.com/user-attachments/assets/31226bf5-d8d1-4ca5-8809-48a0d6d5f097" />


**Question 2**
---
Write a SQL statement to Double the salary for employees in department 20 who have a job_id ending with 'MAN'

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id

```sql
update employees 
set salary = salary*2 where job_id like '%MAN%';
```

**Output:**

<img width="1230" height="445" alt="image" src="https://github.com/user-attachments/assets/4a3ebfeb-32bb-428a-afdd-35b4821f9294" />


**Question 3**
---
Write a SQL statement to Change the category to 'Household' where product name contains 'Detergent' in the products table.

Products Table 

name          type       
----------    ---------- 
product_id     INT PRIMARY KEY        
product_name   VARCHAR(10) 
category       VARCHAR(50) 
cost_price     DECIMAL(10) 
sell_price     DECIMAL(10) 
reorder_lvl    INT        
quantity       INT        
supplier_id    INT   

```sql
update products
set category='Household' where product_name like '%Detergent%';
```

**Output:**

<img width="1220" height="602" alt="image" src="https://github.com/user-attachments/assets/67d8e125-5c5e-4fb7-a279-1b93e5a84c5f" />


**Question 4**
---
Increase the reorder level by 30% for products from 'Food' category having quantity in stock less than 50% of existing reorder level in the products table
name               type
--------------  ----------
product_id         INT
product_name       VARCHAR(10)
category           VARCHAR(50)
cost_price         DECIMAL(10)
sell_price         DECIMAL(10)
reorder_lvl        INT
quantity              INT
supplier_id           INT
```sql
update products
set reorder_lvl= reorder_lvl *1.30 where category='Food' and reorder_lvl > quantity*0.5;
```

**Output:**

<img width="1230" height="503" alt="image" src="https://github.com/user-attachments/assets/80d024a9-9653-4628-aee0-c9ba2eee2da5" />


**Question 5**
---
Write a SQL statement to Increase quantity of all products by 10% to adjust for surplus stock counted

Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id

```sql
update products
set   quantity=quantity*1.1
```

**Output:**

<img width="1227" height="711" alt="image" src="https://github.com/user-attachments/assets/8ec35df1-bf73-4bb3-ab67-7c31ef2f3825" />


**Question 6**
---
Write a SQL query to Delete customers with 'GRADE' 3 or 'AGENT_CODE' 'A008' whose 'OUTSTANDING_AMT' is less than 5000

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSB

```sql
delete from customer where (grade=3 or agent_code='A008') and OUTSTANDING_AMT<5000;
```

**Output:**

<img width="1226" height="486" alt="image" src="https://github.com/user-attachments/assets/d1c9cf0b-e909-4ff9-8571-d4ddc92c6f76" />


**Question 7**
---
Write a SQL query to Delete a Specific Surgery whose ID is 3 or surgeon ID is 4.

Sample table: Surgeries


```sql
delete from Surgeries where surgery_id=3 or surgeon_id=4;
```

**Output:**

<img width="1237" height="966" alt="image" src="https://github.com/user-attachments/assets/d3b45f6f-71f9-4630-9724-e0976496d6a4" />


**Question 8**
---
Write a SQL query to Delete customers from 'customer' table where 'CUST_NAME' has exactly 6 characters.

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.

```sql
delete from customer where length(cust_name)=6;
```

**Output:**

<img width="1226" height="827" alt="image" src="https://github.com/user-attachments/assets/5db741d0-d6ac-46ff-afec-a2a11c9e3755" />


**Question 9**
---
Write a SQL query to Delete customers from 'customer' table where 'CUST_NAME' contains the substring 'Holmes'.

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSB

```sql
delete from customer where cust_name like '%Holmes%';
```

**Output:**

<img width="1244" height="601" alt="image" src="https://github.com/user-attachments/assets/ee98dec2-fb3a-42a4-8edf-7e1131355468" />


**Question 10**
---
Write a SQL query to remove rows from the table 'customer' with the following condition -

1. 'cust_country' must be 'India',

2. 'cus_city' must not be 'Chennai',

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSB

```sql
delete from customer where cust_country='India' and cust_city!='Chennai';
```

**Output:**

<img width="1229" height="963" alt="image" src="https://github.com/user-attachments/assets/6f3a088d-f964-46f2-810b-25b8d24d2b1a" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
