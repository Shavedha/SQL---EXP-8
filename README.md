# SQL - EXPERIMENT 8 - To Implement usage of keywords, CASE, CROSS JOIN, FULL OUTER JOIN
## AIM:
The aim of the given code snippets is to demonstrate the usage and implementation of keywords such as CASE, CROSS JOIN, and FULL OUTER JOIN in SQL.

## 1. USING CASE EXPRESSION
### ALGORITHM:
1. Create a table named "EMPLOYEE" with columns empId, firstname, lastname, and salary.
2. Insert data into the EMPLOYEE table.
3. Use a SELECT statement to retrieve the empId, firstname, lastname, salary, and a calculated column "result" using the CASE expression.
4. The CASE expression checks the value of the salary column and assigns a result based on the specified conditions.
5. If the salary is less than 3000, the result is set to "Low".
6. If the salary is between 3000 and 5000, the result is set to "Average".
7. If the salary is greater than 5000, the result is set to "High".
8. The result is displayed for each row in the EMPLOYEE table.

### PROGRAM:
```
--create
CREATE TABLE EMPLOYEE (
  empId INTEGER PRIMARY KEY,
  firstname TEXT NOT NULL,
  lastname TEXT NOT NULL,
  salary INTEGER NOT NULL
);
--insert
INSERT INTO EMPLOYEE VALUES (0001, 'Harry', 'potter',1000);
INSERT INTO EMPLOYEE VALUES (0002, 'Dave', 'John',3500);
INSERT INTO EMPLOYEE VALUES (0003, 'Ava', 'Grayson',7000);
INSERT INTO EMPLOYEE VALUES (0004, 'Eda', 'Srikar',1200);
INSERT INTO EMPLOYEE VALUES (0005, 'Robert', 'Brown',2500);
INSERT INTO EMPLOYEE VALUES (0006, 'Will', 'John',9000);

SELECT empId,firstname,lastname,salary,
CASE
WHEN salary<3000 THEN "Low"
WHEN salary>3000 AND salary<5000 THEN "Average"
ELSE "High"
END AS result
FROM EMPLOYEE;
```

### OUTPUT:
![image](https://github.com/Shavedha/SQL---EXP-8/assets/93427376/6da73681-c094-4f6c-ba7e-cd22ee3e6867)

### RESULT:
The first code snippet using the CASE expression will return a result set with columns empId, firstname, lastname, salary, and a calculated column "result" for each employee, indicating if their salary is "Low," "Average," or "High" based on the specified conditions.

## 2. CROSS JOIN KEYWORD
### ALGORITHM:
1. Create two tables named "sales_organization" and "sales_channel" with respective columns.
2. Insert data into the sales_organization and sales_channel tables.
3. Use a SELECT statement to perform a CROSS JOIN between the sales_organization and sales_channel tables.
4. A CROSS JOIN returns the Cartesian product of both tables, combining each row from the first table with each row from the second table.
5. The result is displayed, showing the sales organization and channel names for all combinations.

### PROGRAM:
```
CREATE TABLE sales_organization 
(
	sales_org_id INT PRIMARY KEY,
	sales_org VARCHAR (255)
);
CREATE TABLE sales_channel 
(
	channel_id INT PRIMARY KEY,
	channel_name VARCHAR (255)
);
INSERT INTO sales_organization (sales_org_id, sales_org)
VALUES
(1, 'Domestic'),
(2, 'Export');
INSERT INTO sales_channel (channel_id, channel_name)
VALUES
(1, 'Wholesale'),
(2, 'Retail'),
(3, 'eCommerce'),
(4, 'TV Shopping');
SELECT
sales_org,
channel_name
FROM
sales_organization
CROSS JOIN sales_channel;
```
### OUTPUT:
![image](https://github.com/Shavedha/SQL---EXP-8/assets/93427376/1740cc8b-05b6-4800-bee8-a15c51bf0037)

### RESULT:
The second code snippet using the CROSS JOIN keyword will return a result set with columns sales_org and channel_name, showing all combinations of sales organizations and sales channels.

## 3. FULL OUTER JOIN
### ALGORITHM:
1. Create two tables named "fruits" and "baskets" with respective columns.
2. Insert data into the fruits and baskets tables.
3. Use a SELECT statement to perform a FULL OUTER JOIN between the fruits and baskets tables.
4. A FULL OUTER JOIN returns all rows from both tables, matching records where available and including unmatched records from either table.
5. The join is performed based on the basket_id column in both tables.
6. The result is displayed, showing the basket name and fruit name for all matched and unmatched records.

### PROGRAM:
```
CREATE TABLE fruits (
fruit_id INTEGER PRIMARY KEY,
fruit_name VARCHAR (255) NOT NULL,
basket_id INTEGER
);
CREATE TABLE baskets (
basket_id INTEGER PRIMARY KEY,
basket_name VARCHAR (255) NOT NULL
);
INSERT INTO baskets (basket_id, basket_name)
VALUES
(1, 'A'),
(2, 'B'),
(3, 'C');
INSERT INTO fruits (fruit_id,fruit_name,basket_id)
VALUES
(1, 'Apple', 1),
(2, 'Orange', 1),
(3, 'Banana', 2),
(4, 'Strawberry', NULL);
SELECT
basket_name,
fruit_name
FROM
fruits
FULL OUTER JOIN baskets ON baskets.basket_id = fruits.basket_id;
```
### OUTPUT:
![image](https://github.com/Shavedha/SQL---EXP-8/assets/93427376/c78f3b60-0f3e-4683-b353-35c75679e63d)


### RESULT:
The third code snippet using the FULL OUTER JOIN keyword will return a result set with columns basket_name and fruit_name, displaying the basket name and fruit name for all matched and unmatched records between the fruits and baskets tables.
