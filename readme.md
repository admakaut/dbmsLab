## a1

### SQL Commands for `student` Table

```sql
-- Create student table
CREATE TABLE student (
    roll int,
    name varchar(30),
    age int,
    course varchar(30),
    math decimal(6, 2),
    physics decimal(6, 2),
    computer decimal(6, 2),
    dob date
);

-- Alter table to change column names
ALTER TABLE student 
CHANGE COLUMN course department varchar(10);

ALTER TABLE student 
CHANGE COLUMN name first_name varchar(50);

-- Insert data into the student table
INSERT INTO student (roll, first_name, age, department, math, physics, computer, dob) 
VALUES 
    (1, 'Rahul', 19, 'CSE', 79.5, 67, 89, '1993-06-15'),
    (2, 'Kunal', 21, 'CS', 68, 76, 59.5, '1991-08-16'),
    (3, 'Aditi', 20, 'DS', 90, 73, 56, '1992-09-20'),
    (4, 'Sumit', 20, 'AIML', 57.5, 78, 81, '1991-12-07'),
    (5, 'Anirban', 22, 'CS', 80, 68, 63, '1994-09-15'),
    (6, 'Kumkum', 21, 'CS', 72, 54.5, 60, '1995-02-08'),
    (7, 'Suman', 21, 'ECE', 91.5, 32, 61, '1994-03-10'),
    (8, 'Rohit', 22, 'CS', 85, 76, 92, '1992-04-19');

-- Select all records from student
SELECT * FROM student;

-- Select record where roll = 5
SELECT * FROM student WHERE roll = 5;

-- Select specific columns from student
SELECT roll, first_name, math, physics, computer FROM student;

-- Select records where department is 'CS'
SELECT * FROM student WHERE department = 'CS';

-- Update math score for roll 7
UPDATE student SET math = 95 WHERE roll = 7;

-- Update first name for roll 4
UPDATE student SET first_name = 'sumitava' WHERE roll = 4;

-- Select all records after updates
SELECT * FROM student;

-- Delete record where roll = 2
DELETE FROM student WHERE roll = 2;

-- Select all records after deletion
SELECT * FROM student;

-- Delete all records from student
DELETE FROM student;

-- Select all records after deletion
SELECT * FROM student;

-- Drop the student table
DROP TABLE student;
```
## a2
```sql
create table emp1(
   id int,
    name varchar(10),
    basic decimal(6,2),
    designation varchar(20),
    age int
);

-- desc emp1;

alter table emp1 modify basic int;

-- desc emp1;

alter table emp1 modify name varchar(15);
-- desc emp1;

create table emp_trainee(
   id int,
    name varchar(15),
    basic int,
    designation varchar(20),
    age int
);

insert into emp1(id, name, basic, designation, age) values
 (1, 'Rohit', 6700, 'Manager', 24),
    (2, 'Sunil', 6200, 'Engineer', 27),
    (3, 'Payal', 6300, 'Engineer', 25),
    (4, 'Kunal', 6700, 'Trainee', 28),
    (5, 'Sunita', 6230, 'Trainee', 26),
    (6, 'Bimal', 7000, 'Trainee', 25);

insert into emp_trainee(id, name, basic, designation, age) 
select * from emp1 where designation="trainee";

update emp_trainee set designation = 'programmer_trainee' where designation = 'trainee';
-- select * from emp_trainee;

alter table emp1 add skills varchar(10), add dob date;
-- select * from emp1;

update emp1 set skills='c', dob='2021-06-01' where id = 1;
-- select * from emp1;

delete from emp1 where designation = 'trainee';

alter table emp_trainee drop column age;

alter table emp_trainee drop column name, drop column basic;
-- desc emp_trainee;

alter table emp1 rename emp_mgr_eng;

drop table emp_trainee;

truncate table emp_mgr_eng;

```

## a3

```sql
CREATE TABLE employee (
    employee_id NUMBER(6),
    last_name VARCHAR2(25),
    job_id VARCHAR2(10),
    salary NUMBER(8,2),
    comm_pct NUMBER(4,2),
    mgr_id NUMBER(6),
    department_id NUMBER(4)
);

INSERT INTO employee (employee_id, last_name, job_id, salary, comm_pct, mgr_id, department_id) VALUES 
(198, 'Connell', 'SH_CLERK', 2600, 2.5, 124, 50),
(199, 'Grant', 'SH_CLERK', 2600, 2.2, 124, 50),
(200, 'Whalen', 'AD_ASST', 4400, 1.3, 101, 10),
(201, 'Hartstein', 'IT_PROG', 6000, NULL, 100, 20),
(202, 'Fay', 'AC_MGR', 6500, NULL, 210, 20),
(203, 'Mavris', 'AD_VP', 7500, NULL, 101, 40),
(204, 'Baer', 'AD_PRES', 3500, 1.5, 101, 90),
(205, 'Higgins', 'AC_MGR', 2300, NULL, 101, 60),
(206, 'Gitz', 'IT_PROG', 5000, NULL, 103, 60),
(100, 'King', 'AD_ASST', 8956, 0.3, 108, 100),
(101, 'Kochar', 'SH_CLERK', 3400, 1.3, 118, 30);

describe table employee;
select * from employee;

select employee_id, last_name, job_id from employee;

select * from employee where department_id=60;

select * from employee where last_name= "King";

select distinct job_id as job_title from employee;

select last_name, salary, (salary+300) as increased_salary from employee;

select last_name, salary, (salary*12 + 100) as "annual_compensation" from employee;

select * from employee where comm_pct is not null;

select * from employee where comm_pct is null;

select employee_id, department_id, salary from employee where salary > 5000;

select last_name, salary from employee where salary between 4000 and 7000;

select last_name, salary from employee where salary in (6000, 6500, 7000);

select last_name, salary from employee where department_id in (10, 20, 30, 50);

select * from employee where salary <> 5000;

select * from employee where  job_id like '%CLERK%';

update employee set job_id = "grade_A" where salary>5000;
select * from employee;

select * from employee where job_id in ("SH_CLERK", "IT_PROG", "AD_ASST");

SELECT * 
FROM employee 
WHERE department_id = "SH_CLERK" 
AND salary < 3000;

select last_name, mgr_id from employee where salary > 3000 and mgr_id = 101;

```

## a4

```sql

-- Step 1: Create Customer table
CREATE TABLE Customer (
    Cust_id VARCHAR(4) PRIMARY KEY,
    Fname VARCHAR(20) NOT NULL,
    Lname VARCHAR(20) NOT NULL,
    Area VARCHAR(20) NOT NULL,
    Phone VARCHAR(15)
);


-- Step 1: Create Movie table
CREATE TABLE Movie (
    Mv_no INT PRIMARY KEY,
    Cust_id VARCHAR(4),
    Title VARCHAR(50) NOT NULL,
    Star VARCHAR(2),
    Price INT CHECK (Price BETWEEN 100 AND 250),
    FOREIGN KEY (Cust_id) REFERENCES Customer(Cust_id)
);


-- Step 2: Insert data into Customer table
INSERT INTO Customer (Cust_id, Fname, Lname, Area, Phone) VALUES
('A01', 'Ivan', 'Ross', 'SA', '6125467'),
('A02', 'Vandana', 'Ray', 'MU', '5560379'),
('A03', 'Pramada', 'Jauguste', 'DA', '4560389'),
('A04', 'Basu', 'Navindi', 'BA', '6125401'),
('A05', 'Ravi', 'Shridhar', 'NA', NULL),
('A06', 'Rukmini', 'Aiyer', 'GH', '5125274');


-- Step 2: Insert data into Movie table
INSERT INTO Movie (Mv_no, Cust_id, Title, Star, Price) VALUES
(1, 'A02', 'Bloody', 'JC', 181),
(2, 'A04', 'The Firm', 'TC', 200),
(3, 'A01', 'Pretty Woman', 'RG', 151),
(4, 'A06', 'Home Alone', 'MC', 150),
(5, 'A05', 'The Fugitive', 'MF', 200),
(6, 'A03', 'Coma', 'MD', 100),
(7, 'A02', 'Dracula', 'GO', 150),
(8, 'A06', 'Quick Change', 'BM', 100),
(9, 'A03', 'Gone with the Wind', 'CB', 200),
(10, 'A05', 'Carry on Doctor', 'LP', 100);


-- Step 3: Prove entity integrity constraint
-- Check for nulls in primary keys
SELECT Cust_id FROM Customer WHERE Cust_id IS NULL;

SELECT Mv_no FROM Movie WHERE Mv_no IS NULL;


-- Step 4: Prove referential integrity constraint
-- Check that all Cust_id values in Movie exist in Customer
SELECT Movie.Cust_id
FROM Movie
LEFT JOIN Customer ON Movie.Cust_id = Customer.Cust_id
WHERE Customer.Cust_id IS NULL;


-- Step 5: Prove domain integrity constraint
-- Check Price values
SELECT * FROM Movie WHERE Price < 100 OR Price > 250;


-- Step 6: Display movie titles with price > 100 and < 200
SELECT Title FROM Movie WHERE Price > 100 AND Price < 200;


-- Step 7: Display Cust_id who have seen movies with stars JC, TC, or MC
SELECT DISTINCT Cust_id FROM Movie WHERE Star IN ('JC', 'TC', 'MC');


-- Step 8: Display details of customers with 'A' in their area name
SELECT * FROM Customer WHERE Area LIKE '%A%';


-- Step 9: Display movie titles with price 180 and titles exactly 6 characters
SELECT Title FROM Movie WHERE Price = 180 AND LENGTH(Title) = 6;


-- Step 10: Display movie name, original prices, and prices after 10% increment
SELECT Title, Price, Price * 1.10 AS Incremented_Price FROM Movie;


-- Step 11: Display all customer details in the specific format
SELECT CONCAT(Fname, ' ', Lname, ' stays in ', Area, ' and his phone number is ', Phone) AS Customer_Details FROM Customer;


-- Step 12: Add a not null constraint to the Lname field in Customer
ALTER TABLE Customer MODIFY Lname VARCHAR(20) NOT NULL;


-- Step 13: Display customer names whose phone number is not recorded
SELECT Fname, Lname FROM Customer WHERE Phone IS NULL;


-- Step 14: Add the phone number for the customer mentioned in step 7 (example for Cust_id 'A05')
UPDATE Customer SET Phone = '9999999' WHERE Cust_id = 'A05';


-- Step 15: Display unique customer ids from the Movie table
SELECT DISTINCT Cust_id FROM Movie;


-- Step 16: Remove the not null constraint from the Star column in Movie table
ALTER TABLE Movie MODIFY Star VARCHAR(2) NULL;


-- Step 17: Delete any row from the Customer table (example for Cust_id 'A01')
-- DELETE FROM Customer WHERE Cust_id = 'A01';


-- Step 18: Delete any row from the Movie table (example for Mv_no 1)
-- DELETE FROM Movie WHERE Mv_no = 1;


-- Step 19: Drop the Customer table
-- DROP TABLE Customer;


-- Step 20: Drop the Movie table
-- DROP TABLE Movie;


```

## a5

```sql

-- Step 1: Creating Tables and Inserting Data

-- Client_Master table
CREATE TABLE Client_Master (
    Client_no VARCHAR2(5) CONSTRAINT PK_ClientNo PRIMARY KEY CONSTRAINT CHK_ClientNO CHECK (Client_no LIKE 'C%'),
    Name VARCHAR2(20) CONSTRAINT nnull_Name NOT NULL CONSTRAINT unq_name UNIQUE,
    Address1 VARCHAR2(30),
    State VARCHAR2(30),
    City VARCHAR2(15) CONSTRAINT CHK_City CHECK (City IN ('Delhi', 'Mumbai', 'Chennai'))
);

-- Inserting data into Client_Master
INSERT INTO Client_Master (Client_no, Name, Address1, State, City) VALUES
('C01', 'Ivaan', 'Church Rd', 'Maharashtra', 'Mumbai'),
('C02', 'Vandana', 'St.Mary Rd', 'Tamil Nadu', 'Chennai'),
('C03', 'Pramada', 'Mall Rd', 'Maharashtra', 'Mumbai'),
('C04', 'Basu', 'Church Rd', 'Maharashtra', 'Mumbai'),
('C05', 'Ravi', 'Chandni', null, 'Delhi'),
('C06', 'Rukmini', 'Mall Rd', 'Maharashtra', 'Mumbai');

-- Products_Master table
CREATE TABLE Products_Master (
    Product_no VARCHAR2(10) CONSTRAINT PK_Productno PRIMARY KEY CONSTRAINT CHK_Productno CHECK (Product_no LIKE 'P%'),
    Description VARCHAR2(20) CONSTRAINT nnull_Description NOT NULL CONSTRAINT unq_Description UNIQUE,
    Qty_on_hand NUMBER(8) CONSTRAINT CHK_QtyOnHand CHECK (Qty_on_hand > 10),
    Sell_price NUMBER(8,2) CONSTRAINT nnull_SellPrice NOT NULL,
    Cost_price NUMBER(8,2) CONSTRAINT nnull_CostPrice NOT NULL
);

-- Inserting data into Products_Master
INSERT INTO Products_Master (Product_no, Description, Qty_on_hand, Sell_price, Cost_price) VALUES
('P01', '1.44 Floppies', 100, 525, 500),
('P02', 'Monitors', 25, 12000, 11280),
('P03', 'Mouse', 20, 1050, 1000),
('P04', '1.22 floppies', 100, 525, 500),
('P05', 'Keyboards', 15, 3150, 3050),
('P06', 'Cd drive', 14, 5250, 5100);

-- Sales_Order table
CREATE TABLE Sales_Order (
    S_order_no VARCHAR2(10) CONSTRAINT PK_SOrderNo PRIMARY KEY CONSTRAINT CHK_SOrderNo CHECK (S_order_no LIKE 'O%'),
    S_order_date DATE,
    Client_no VARCHAR2(5) CONSTRAINT FK_Client_No REFERENCES Client_Master(Client_no),
    Salesman_no VARCHAR2(10) CONSTRAINT CHK_SalesmanNo CHECK (Salesman_no LIKE 'S%'),
    Product_no VARCHAR2(10) CONSTRAINT FK_Product_no REFERENCES Products_Master(Product_no)
);

-- Inserting data into Sales_Order
INSERT INTO Sales_Order (S_order_no, S_order_date, Client_no, Salesman_no, Product_no) VALUES
('O19001', TO_DATE('12-jan-96', 'dd-mon-yy'), 'C01', 'S01', 'P01'),
('O19002', TO_DATE('25-jan-96', 'dd-mon-yy'), 'C02', 'S02', 'P02'),
('O19003', TO_DATE('18-feb-96', 'dd-mon-yy'), 'C03', 'S03', 'P03'),
('O19004', TO_DATE('03-apr-96', 'dd-mon-yy'), 'C01', 'S01', 'P04'),
('O19005', TO_DATE('20-may-96', 'dd-mon-yy'), 'C04', 'S02', 'P05'),
('O19006', TO_DATE('24-may-96', 'dd-mon-yy'), 'C05', 'S04', 'P06');

-- Step 2: Adding a Not Null Constraint on Address1 in Client_Master
ALTER TABLE Client_Master MODIFY Address1 VARCHAR2(30) CONSTRAINT nnul_Address1 NOT NULL;

-- Step 3: Checking Entity Integrity Constraints

-- Primary keys and unique constraints are enforced in all tables.
-- Primary keys: Client_Master(Client_no), Products_Master(Product_no), Sales_Order(S_order_no)
-- Unique constraints: Client_Master(Name), Products_Master(Description)

-- Step 4: Checking Referential Integrity Constraints

-- Sales_Order.Client_no REFERENCES Client_Master(Client_no)
-- Sales_Order.Product_no REFERENCES Products_Master(Product_no)

-- Step 5: Checking Domain Integrity Constraints

-- Client_Master: CHK_ClientNO, nnull_Name, CHK_City
-- Products_Master: CHK_Productno, nnull_Description, CHK_QtyOnHand, nnull_SellPrice, nnull_CostPrice

-- Step 6: Calculating Profit in Products_Master
SELECT *, (Sell_price - Cost_price) AS Profit
FROM Products_Master;

-- Step 7: Calculating Total Cost Price of Stock in Products_Master
SELECT *, (Qty_on_hand * Cost_price) AS Total_Cost
FROM Products_Master;

-- Step 8: Displaying Client Details for Names Starting with 'I'
SELECT *
FROM Client_Master
WHERE Name LIKE 'I%';

-- Step 9: Displaying Client Details for Names Starting with 'R' and Ending with 'i'
SELECT *
FROM Client_Master
WHERE Name LIKE 'R%i';

-- Step 10: Displaying Client Details for Names Containing 'a' in the Third and Fifth Position
SELECT *
FROM Client_Master
WHERE SUBSTR(Name, 3, 1) = 'a' AND SUBSTR(Name, 5, 1) = 'a';

-- Step 11: Displaying Client Details for Names Containing 'aa'
SELECT *
FROM Client_Master
WHERE Name LIKE '%aa%';

-- Step 12: Displaying Client Details for Names Containing Exactly Four Characters
SELECT *
FROM Client_Master
WHERE LENGTH(Name) = 4;

-- Step 13: Displaying Client Details for Clients Who Have Not Mentioned State in Address
SELECT *
FROM Client_Master
WHERE State IS NULL;

-- Step 14: Displaying Order Details Placed after January 1996
SELECT *
FROM Sales_Order
WHERE S_order_date > TO_DATE('01-jan-96', 'dd-mon-yy');

-- Step 15: Updating Sales_Order Record
UPDATE Sales_Order
SET S_order_date = TO_DATE('24/07/96', 'dd/mm/yy'), Product_no = 'P06', Salesman_no = 'S04'
WHERE Client_no = 'C01' AND S_order_no = 'O19001';

-- Step 16: Changing City for Client C05
UPDATE Client_Master
SET City = 'Kolkata'
WHERE Client_no = 'C05';

-- Step 17: Changing Field Size of Client_no in All Tables
ALTER TABLE Client_Master MODIFY Client_no VARCHAR2(15);
ALTER TABLE Sales_Order MODIFY Client_no VARCHAR2(15);
-- Similarly for other tables if Client_no is present

-- Step 18: Changing Client_no for S_order_no O19001 in Sales_Order
UPDATE Sales_Order
SET Client_no = 'C08'
WHERE S_order_no = 'O19001';
-- Error would occur if 'C08' does not exist in Client_Master or violates constraints

-- Step 19: Removing Foreign Key Constraint on Product_no in Sales_Order
ALTER TABLE Sales_Order DROP CONSTRAINT FK_Product_no;

-- Step 20: Removing Foreign Key Constraint on Client_no in Sales_Order
ALTER TABLE Sales_Order DROP CONSTRAINT FK_Client_No;

-- Step 21: Removing Check Constraint on Product_no in Products_Master
ALTER TABLE Products_Master DROP CONSTRAINT CHK_Productno;

-- Step 22: Removing Record for Client_no C02 from Client_Master
DELETE FROM Client_Master
WHERE Client_no = 'C02';

-- Step 23: Removing Records from Product_Master Based on Sell Price Range
DELETE FROM Products_Master
WHERE Sell_price BETWEEN 1000 AND 10000;


```

## a6

```sql

-- Step 1: Creating the EMP table and inserting data

CREATE TABLE EMP (
    E_ID INT PRIMARY KEY,
    FNAME VARCHAR2(50) NOT NULL,
    LNAME VARCHAR2(50) NOT NULL,
    HIRE_DATE DATE NOT NULL,
    JOB_ID VARCHAR2(50) NOT NULL,
    SAL NUMBER(8, 2) NOT NULL,
    DEPT_ID INT CHECK (DEPT_ID >= 10)
);

-- Inserting sample data into EMP table
INSERT INTO EMP (E_ID, FNAME, LNAME, HIRE_DATE, JOB_ID, SAL, DEPT_ID) VALUES
(198, 'Donald', 'Connell', TO_DATE('21-Jun-99', 'DD-MON-YY'), 'SH_CLERK', 2600, 50),
(199, 'Douglas', 'Grant', TO_DATE('13-Jan-98', 'DD-MON-YY'), 'SH_CLERK', 3000, 50),
(200, 'Jennifer', 'Whalen', TO_DATE('17-Sep-87', 'DD-MON-YY'), 'AD_ASST', 4400, 10),
(201, 'Michael', 'Hartstein', TO_DATE('19-Jan-99', 'DD-MON-YY'), 'IT_PROG', 6000, 20),
(202, 'Pat', 'Fay', TO_DATE('25-Oct-89', 'DD-MON-YY'), 'AC_MGR', 6500, 20),
(203, 'Susan', 'Mavris', TO_DATE('26-Nov-76', 'DD-MON-YY'), 'AD_VP', 7500, 40),
(204, 'Hermann', 'Baer', TO_DATE('23-Aug-95', 'DD-MON-YY'), 'AD_PRES', 9500, 90),
(205, 'Shelley', 'Higgins', TO_DATE('24-Feb-98', 'DD-MON-YY'), 'AC_MGR', 2300, 60),
(206, 'William', 'Gitz', TO_DATE('12-Mar-01', 'DD-MON-YY'), 'IT_PROG', 5000, 60),
(100, 'Steven', 'King', TO_DATE('15-Jun-02', 'DD-MON-YY'), 'AD_ASST', 8956, 100),
(101, 'Neena', 'Kochar', TO_DATE('10-Jul-03', 'DD-MON-YY'), 'SH_CLERK', 3400, 30);

-- Step 2: Display the fname of all employees in ascending order. Give appropriate alias name to the column.
SELECT FNAME AS Employee_First_Name
FROM EMP
ORDER BY FNAME ASC;

-- Step 3: Display the fname of all employees in descending order. Give appropriate alias name to the column.
SELECT FNAME AS Employee_First_Name
FROM EMP
ORDER BY FNAME DESC;

-- Step 4: Display the hire date of all employees in ascending order.
SELECT HIRE_DATE
FROM EMP
ORDER BY HIRE_DATE ASC;

-- Step 5: Display the employee details whose fname starts with either J or M. Sort the result by employee lname.
SELECT *
FROM EMP
WHERE FNAME LIKE 'J%' OR FNAME LIKE 'M%'
ORDER BY LNAME;

-- Step 6: Find the highest, lowest, average and sum of salary of all employees. Give alias names to all the columns as ‘Max’, ‘Min’, ‘Avg’, ‘Sum’ respectively.
SELECT 
    MAX(SAL) AS Max,
    MIN(SAL) AS Min,
    AVG(SAL) AS Avg,
    SUM(SAL) AS Sum
FROM EMP;

-- Step 7: Find the highest, lowest, average and sum of salary of all employees of each individual job type.
SELECT 
    JOB_ID,
    MAX(SAL) AS Max,
    MIN(SAL) AS Min,
    AVG(SAL) AS Avg,
    SUM(SAL) AS Sum
FROM EMP
GROUP BY JOB_ID;

-- Step 8: Display the number of people under each job.
SELECT 
    JOB_ID,
    COUNT(*) AS Num_Employees
FROM EMP
GROUP BY JOB_ID;

-- Step 9: Display the number of managers in the company without listing their emp_id or names.
SELECT 
    COUNT(*) AS Num_Managers
FROM EMP
WHERE JOB_ID LIKE '%MANAGER%';

-- Step 10: Find the difference between the highest and the lowest salaries.
SELECT MAX(SAL) - MIN(SAL) AS Salary_Difference
FROM EMP;

-- Step 11: Display the maximum and average salary of the engineers.
SELECT 
    MAX(SAL) AS Max_Engineer_Salary,
    AVG(SAL) AS Avg_Engineer_Salary
FROM EMP
WHERE JOB_ID = 'ENGINEER';

-- Step 12: Display the employee fname that is first and the employee fname that is last in the alphabetized list of all employees.
SELECT 
    MIN(FNAME) AS First_Alphabetically,
    MAX(FNAME) AS Last_Alphabetically
FROM EMP;

-- Step 13: Display the date when the first employee was hired and last date of hiring the employees. Rename the column as ‘First Hire_Date’ and ‘Last Hire_Date’.
SELECT 
    MIN(HIRE_DATE) AS First_Hire_Date,
    MAX(HIRE_DATE) AS Last_Hire_Date
FROM EMP;

-- Step 14: Display the maximum and average salary of the clerks.
SELECT 
    MAX(SAL) AS Max_Clerk_Salary,
    AVG(SAL) AS Avg_Clerk_Salary
FROM EMP
WHERE JOB_ID = 'CLERK';

-- Step 15: Display the dept no. and the salary of the lowest paid employee for each department. Give an alias name to the minimum salary column.
SELECT 
    DEPT_ID,
    MIN(SAL) AS Lowest_Salary
FROM EMP
GROUP BY DEPT_ID;

-- Step 16: Display the dept no. and the salary of the lowest paid employee for each department. Exclude any groups where the minimum salary is 3000 or less. Sort the output in descending order of salary.
SELECT 
    DEPT_ID,
    MIN(SAL) AS Lowest_Salary
FROM EMP
GROUP BY DEPT_ID
HAVING MIN(SAL) > 3000
ORDER BY Lowest_Salary DESC;

-- Step 17: Display a formatted message for all rows of the table: <First_name > whose designation is <job_id> gets <Salary> but wants to earn <3*Salary>.
SELECT 
    FNAME || ' whose designation is ' || JOB_ID || ' gets ' || SAL || ' but wants to earn ' || (3 * SAL) AS Salary_Wish
FROM EMP;

-- Step 18: Display today’s date. Rename the column as TODAY.
SELECT SYSDATE AS Today
FROM DUAL;

-- Step 19: Display the Employee id, the day and the year in which the employees were hired.
SELECT 
    E_ID AS Employee_ID,
    TO_CHAR(HIRE_DATE, 'DD') AS Hired_Day,
    TO_CHAR(HIRE_DATE, 'YYYY') AS Hired_Year
FROM EMP;

-- Step 20: Display the employee name and the hire date of all employees in the format ‘dd-month-yy’.
SELECT 
    FNAME || ' ' || LNAME AS Employee_Name,
    TO_CHAR(HIRE_DATE, 'DD-MON-YY') AS Hire_Date_Formatted
FROM EMP;

-- Step 21: Display the system year in full spelling (Ex: Nineteen Ninety-Nine for 1999).
SELECT TO_CHAR(SYSDATE, 'YYYY') AS Full_Spelling_Year
FROM DUAL;

-- Step 22: Find date, 15 days after today’s date, 15 days before today’s date.
SELECT 
    SYSDATE AS Today,
    SYSDATE + 15 AS Fifteen_Days_After,
    SYSDATE - 15 AS Fifteen_Days_Before
FROM DUAL;

-- Step 23: Ensure the domain constraint and entity integrity constraint from the above table.
-- Assumes constraints are already defined during table creation.

-- Step 24: Drop the domain constraint from the table.
-- Example: ALTER TABLE EMP DROP CONSTRAINT <constraint_name>;

-- Step 25: Drop the primary key from the table.
-- Example: ALTER TABLE EMP DROP CONSTRAINT PK_EMP;

-- Step 26: Drop the created table.
-- Example: DROP TABLE EMP;


```

## a7

```sql
-- Step 1: Create the Employee_Details table with specified structure
CREATE TABLE Employee_Details (
    Employee_id INT PRIMARY KEY,
    First_Name VARCHAR2(50),
    Last_Name VARCHAR2(50),
    Department_id INT,
    Job_id VARCHAR2(50),
    Salary NUMBER(10, 2),
    Hire_Date DATE
);

-- Step 2: Display the First Name of all employees in LOWER CASE, those who work in department no 20 or 50 or 80
SELECT LOWER(First_Name) AS Lowercase_First_Name
FROM Employee_Details
WHERE Department_id IN (20, 50, 80);

-- Step 3: Display the Last Name of all employees in UPPER CASE, those who work in department no 10 or 110 or 60
SELECT UPPER(Last_Name) AS Uppercase_Last_Name
FROM Employee_Details
WHERE Department_id IN (10, 110, 60);

-- Step 4: Display all job_id in the format ‘ Sa_Rep’
SELECT CONCAT(' Sa_', UPPER(SUBSTR(Job_id, -3))) AS Formatted_Job_id
FROM Employee_Details;

-- Step 5: Display the Name (Both First name and Last Name concatenated together) of all employees using function
SELECT CONCAT(First_Name, ' ', Last_Name) AS Full_Name
FROM Employee_Details;

-- Step 6: Find the length of the last names of the employees getting commission
SELECT LENGTH(Last_Name) AS Last_Name_Length
FROM Employee_Details
WHERE Job_id LIKE '%COMMISSION%';

-- Step 7: Find out the numeric position of the letter ‘a ‘ in the First Name of all employees
SELECT INSTR(First_Name, 'a') AS Position_of_A_in_First_Name
FROM Employee_Details;

-- Step 8: Displays employee first names and last names joined together, the length of the employee last name, and the numeric position of the letter a in the employee last name for all employees who have the string CLERK contained in the job ID
SELECT 
    First_Name || ' ' || Last_Name AS Full_Name,
    LENGTH(Last_Name) AS Last_Name_Length,
    INSTR(Last_Name, 'a') AS Position_of_A_in_Last_Name
FROM Employee_Details
WHERE Job_id LIKE '%CLERK%';

-- Step 9: Display the salary of all employees in 10 digits. Pad the extra digits with ‘$’ on the left hand side
SELECT LPAD(TO_CHAR(Salary), 10, '$') AS Padded_Salary
FROM Employee_Details;

-- Step 10: Trim ‘e’ from all employees first name who has an ‘e’ in their first name and display with the column renamed as ‘Trimmed’
SELECT REPLACE(First_Name, 'e', '') AS Trimmed
FROM Employee_Details
WHERE INSTR(First_Name, 'e') > 0;

-- Step 11: Display the department_id, Salary and hire_date of those employees whose first name contains exactly 6 characters. Use function to display the result
SELECT Department_id,
       Salary,
       Hire_Date
FROM Employee_Details
WHERE LENGTH(First_Name) = 6;

-- Step 12: Display the job_id of those employees whose first name contains ‘e’. Display the position of ‘e’ in their first name
SELECT 
    Job_id,
    INSTR(First_Name, 'e') AS Position_of_E_in_First_Name
FROM Employee_Details
WHERE INSTR(First_Name, 'e') > 0;

-- Step 13: Display the employee last name for all employees who have the string REP contained in the job ID starting at the fourth position of the job ID
SELECT Last_Name
FROM Employee_Details
WHERE SUBSTR(Job_id, 4) = 'REP';

-- Step 14: Calculate the remainder of the salaries after it is divided by 3000 for all employees whose job title is sales representative
SELECT MOD(Salary, 3000) AS Salary_Remainder
FROM Employee_Details
WHERE Job_id LIKE '%SALES REPRESENTATIVE%';

-- Step 15: Display the salary of all employees in the format ‘ $7,000.00’
SELECT TO_CHAR(Salary, '$99,999.99') AS Formatted_Salary
FROM Employee_Details;

-- Step 16: Find the no. of days elapsed between today’s date and the hire date. Round off the no. of days
SELECT ROUND(SYSDATE - Hire_Date) AS Days_Elapsed
FROM Employee_Details;

-- Step 17: Find the no. of weeks elapsed between today’s date and the hire date of all employees
SELECT TRUNC((SYSDATE - Hire_Date) / 7) AS Weeks_Elapsed
FROM Employee_Details;

-- Step 18: Find the no. of years elapsed between today’s date and the hire date. Round off the no. of years
SELECT ROUND(MONTHS_BETWEEN(SYSDATE, Hire_Date) / 12) AS Years_Elapsed
FROM Employee_Details;

```

## a8
```sql
-- Create IT_Students table
CREATE TABLE IT_Students (
    Roll VARCHAR2(10) PRIMARY KEY,
    Name VARCHAR2(50) UNIQUE,
    Dept VARCHAR2(2) CHECK (Dept IN ('IT', 'CS')),
    Sports_Fee NUMBER(10, 2) CHECK (Sports_Fee >= 1000),
    Cultural_Stud NUMBER(10, 2) CHECK (Cultural_Stud >= 600),
    birthday DATE
);

-- Create CS_Students table
CREATE TABLE CS_Students (
    Roll VARCHAR2(10) PRIMARY KEY,
    Name VARCHAR2(50) UNIQUE,
    Dept VARCHAR2(2) CHECK (Dept IN ('IT', 'CS')),
    Sports_Fee NUMBER(10, 2) CHECK (Sports_Fee >= 1000),
    Cultural_Stud NUMBER(10, 2) CHECK (Cultural_Stud >= 600),
    birthday DATE
);

-- Insert sample data into IT_Students
INSERT INTO IT_Students (Roll, Name, Dept, Sports_Fee, Cultural_Stud, birthday)
VALUES ('IT001', 'John Doe', 'IT', 1200, 800, TO_DATE('1995-05-15', 'YYYY-MM-DD'));

-- Insert sample data into CS_Students
INSERT INTO CS_Students (Roll, Name, Dept, Sports_Fee, Cultural_Stud, birthday)
VALUES ('CS001', 'Jane Smith', 'CS', 1500, 700, TO_DATE('1994-08-20', 'YYYY-MM-DD'));

-- Task 2: Display all distinct students studying in the organization including both the departments
SELECT Name
FROM (
    SELECT Name FROM IT_Students
    UNION
    SELECT Name FROM CS_Students
) Distinct_Students;

-- Task 3: Display all students studying in the organization including both the departments
SELECT Name
FROM IT_Students
UNION ALL
SELECT Name
FROM CS_Students;

-- Task 4: Display those students working in both cultural and sports group
SELECT Name
FROM IT_Students
WHERE Cultural_Stud >= 600
INTERSECT
SELECT Name
FROM IT_Students
WHERE Sports_Fee >= 1000;

-- Task 5: Display those students working in only sports group
SELECT Name
FROM IT_Students
WHERE Sports_Fee >= 1000
MINUS
SELECT Name
FROM IT_Students
WHERE Cultural_Stud >= 600;

-- Task 6: Display those students working in only cultural group
SELECT Name
FROM IT_Students
WHERE Cultural_Stud >= 600
MINUS
SELECT Name
FROM IT_Students
WHERE Sports_Fee >= 1000;

-- Task 7: Add a new field birthday to both the tables for all students
-- Already added during table creation and sample data insertion

-- Task 8: Display the student name, age, and month of birth of all the distinct students of the organization
SELECT Name,
       MONTHS_BETWEEN(SYSDATE, birthday) / 12 AS Age,
       TO_CHAR(birthday, 'Month') AS Birth_Month
FROM (
    SELECT Name, birthday FROM IT_Students
    UNION ALL
    SELECT Name, birthday FROM CS_Students
) All_Students;

-- Task 9: Display the details of students from sports_stud table in the following format: <Name> who studies in <Dept> dept pays Rs<sports_fee> for sports
SELECT Name || ' who studies in ' || Dept || ' dept pays Rs' || Sports_Fee || ' for sports.' AS Details
FROM (
    SELECT Name, Dept, Sports_Fee FROM IT_Students
    UNION ALL
    SELECT Name, Dept, Sports_Fee FROM CS_Students
) Sports_Students;

-- Task 10: Display the details of all students from IT department
SELECT *
FROM IT_Students;

-- Task 11: Display the total money earned by the organization from the sports department as well as from the cultural department
SELECT 'Total Sports Earnings:', SUM(Sports_Fee) AS Total_Sports_Earnings
FROM (
    SELECT Sports_Fee FROM IT_Students
    UNION ALL
    SELECT Sports_Fee FROM CS_Students
) Sports_Earnings
UNION ALL
SELECT 'Total Cultural Earnings:', SUM(Cultural_Stud) AS Total_Cultural_Earnings
FROM (
    SELECT Cultural_Stud FROM IT_Students
    UNION ALL
    SELECT Cultural_Stud FROM CS_Students
) Cultural_Earnings;

-- Task 12: Display the name of all the students in descending order
SELECT Name
FROM (
    SELECT Name FROM IT_Students
    UNION ALL
    SELECT Name FROM CS_Students
) All_Students
ORDER BY Name DESC;

-- Task 13: Drop all domain constraints from both the tables
-- Example syntax to drop constraints (replace with actual constraint names)
-- ALTER TABLE IT_Students DROP CONSTRAINT <constraint_name>;
-- ALTER TABLE CS_Students DROP CONSTRAINT <constraint_name>;

-- Task 14: Display the maximum, minimum, and average sports_fee taken by the organization
SELECT MAX(Sports_Fee) AS Max_Sports_Fee,
       MIN(Sports_Fee) AS Min_Sports_Fee,
       AVG(Sports_Fee) AS Avg_Sports_Fee
FROM (
    SELECT Sports_Fee FROM IT_Students
    UNION ALL
    SELECT Sports_Fee FROM CS_Students
) Sports_Fees;


```