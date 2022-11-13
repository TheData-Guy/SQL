
CREATE DATABASE class2_db;

Use class2_db;


create table if not exists employee (
    id int,
    name VARCHAR(50),
    address VARCHAR(50),
    city VARCHAR(50)
);

insert into employee values (1,'Aditya','hinjwadi','Pune');

SELECT *from employee;

-- Asdd New Column Named DOB in the TABLE 

Alter Table employee add DOB DATE;


sELECT * From employee;

-- Modify Existing Column in a Table or Change DataType of Name Column or Increase Length of Name COLUMN

Alter Table employee modify column name varchar(100);

-- Delete Existing Column from Given TABLE or Remove City Column from Employee Table 

Alter Table  employee drop column city;


SELECT * From employee;

-- RENAME THE  COLUMN NAME TO FULL_NAME

ALTER Table employee rename column name to full_name;

-- Add Unique Integrity Constarint on id Column

Alter Table employee add CONSTRAINT id_Unique UNIQUE(id);

-- Checking the Integrity Constarint
insert into employee values (1,'Aditya','hinjwadi','Pune');

-- Drop Constraint from Existing Table

Alter Table employee Drop   constraint id_unique;
-- Checking the Integrity Constarint
insert into employee values (1,'Aditya','hinjwadi','2022-10-22');

Select * from employee;

--- create table with Primary_Key


Create table persons
(
    id int, 
    name varchar(50), 
    age int,
    ---Primary Key (id) 
    constraint pk Primary Key (id) 
);

insert Into persons Values (1,'Aditya',23)

-- Try to insert duplicate value for primary key COLUMN 

insert into persons values(1,'Rahul',28);

--- Try to insert null value for primary key COLUMN
insert into persons values(null,'Rahul',28);

--- To check difference between Primary Key and Unique
alter table persons add constraint age_unq UNIQUE(age); 

select * from persons;

insert into persons values(2,'Rahul',28);


insert into persons values(3,'Amit',28);

insert into persons values(3,'Amit',null);

select * from persons;

insert into persons values(4,'Charan',null);

insert into persons values(5,'Deepak',null);

select * from persons;

create table customer
(
    cust_id int,
    name VARCHAR(50), 
    age int,
    constraint pk Primary Key (cust_id) 
);

create table orders
(
    order_id int,
    order_num int,
    customer_id int,
    constraint pk Primary Key (order_id),
    constraint fk Foreign Key (customer_id) REFERENCES customer(cust_id)
);


--- Differen between Drop & Truncate Command

select * from persons;
truncate table persons;

select * from persons;

drop table persons;

--- Operations with Select Command

select * from employee;


create table if not exists employee(
    id int,
    name VARCHAR(50),
    age int,
    hiring_date date,
    salary int,
    city varchar(50)
);

insert into employee values(1,'Aditya', 23, '2021-08-10', 10000, 'Pune');

insert into employee values(2,'Rahul', 25, '2021-08-10', 20000, 'Khajuraho');

insert into employee values(3,'Sunny', 22, '2021-08-11', 11000, 'Banaglore');

insert into employee values(5,'Amit', 25, '2021-08-11', 12000, 'Noida');

insert into employee values(1,'Puneet', 26, '2021-08-12', 50000, 'Gurgaon');

select * from employee;

--- how to count total records
select count(*) from employee;


--- alias declaration
select count(*) as total_row_count from employee;


--- display all columns in the final result
select * from employee;


--- display specific columns in the final result
select name, salary from employee;


--- aliases for mutiple columns
select name as employee_name, salary as employee_salary from employee;


select * from employee;

--- print unique hiring_dates from the employee table when employees joined it
select Distinct(hiring_date) as distinct_hiring_dates from employee;


select * from employee;

--- How many unique age values in the table??

select  count(distinct(age)) as total_unique_ages from employee;

--- Increment salary of each employee by 20% and display final result with new salary
SELECT  id,
        name,
        salary as old_salary, 
        (salary + salary * 0.2) as new_salary
FROM employee;


-- Syntax for update command
select * from employee;

--- Upadtes will be made for all rows
UPDATE employee SET age = 20;

select * from employee;

--- update the salary of employee after giving 20% increment
UPDATE employee SET salary = salary + salary * 0.2;

select * from employee;


--- How to filter data using WHERE Clauses
select * from employee where hiring_date = '2021-08-10';


select * from employee;

--- Update the salary of employees who joined the company on 2021-08-10 to 80000
update employee SET salary = 80000 where hiring_date = '2021-08-10';

select * from employee;


--- how to delete specific records from table using delete command
--- delete records of those employess who joined company on 2021-08-10

delete from employee where hiring_date = '2021-08-10';


select * from employee;

