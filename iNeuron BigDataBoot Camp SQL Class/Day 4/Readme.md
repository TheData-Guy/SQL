

###  Create Database Command

    CREATE DATABASE class4_db;
    
### Go inside the Particular DATABASE

     use class4_db;
     
### Command To Create a TABLE

    create table orders_data
    (
     cust_id int,
     order_id int,
     country varchar(50),
     state varchar(50)
    );
    
### Synatx To Insert data into a TABLE

    insert into orders_data values(1,100,'USA','Seattle');
    insert into orders_data values(2,101,'INDIA','UP');
    insert into orders_data values(2,103,'INDIA','Bihar');
    insert into orders_data values(4,108,'USA','WDC');
    insert into orders_data values(5,109,'UK','London');
    insert into orders_data values(4,110,'USA','WDC');
    insert into orders_data values(3,120,'INDIA','AP');
    insert into orders_data values(2,121,'INDIA','Goa');
    insert into orders_data values(1,131,'USA','Seattle');
    insert into orders_data values(6,142,'USA','Seattle');
    insert into orders_data values(7,150,'USA','Seattle');
   
### Use the Select Command to Query the Data

    select * from orders_data;

###  Use of Having Clause 

#### Write a Query to Find the Country where only 1 Order was Placed.

    SELECT country from orders_data  GROUP BY country having count(*)=1;


### Where Clause and Group by Clause what is the Proper Sequence ? 
#### Where Caluse first then GROUP BY
                                                           
### How to Use GROUP_CONCAT

   #### Write a Query to Print States Present in the Dataset for Each Country 

    SELECT country, GROUP_CONCAT(state) as states_in_country from orders_data Group by Country;


### Write a Query to Print Distinct States Present in the Dataset for Each Country 

    SELECT country, GROUP_CONCAT(distinct state) as states_in_country from orders_data Group by Country;


### Write a Query to Print Distinct States  and order by states in Desc order Present in the Dataset for Each Country 

    SELECT country, GROUP_CONCAT(distinct state ORDER BY state desc) as states_in_country from orders_data Group by Country;

### Write a Query to Print Distinct States  and order by states in Desc order and use Sperator for state coulmn  Present in the Dataset for Each Country

    SELECT country, GROUP_CONCAT(distinct state ORDER BY state desc separator '->') as states_in_country from orders_data Group by Country;

### SubQueries in SQL 

    create table employee
    (
        id int,
        name varchar(50),
        salary int
    );
    
### Synatx To Insert data into a TABLE

    insert into employee values(1,'Aditya',5000),(2,'Amit',5500),(3,'Rahul',7000),(4,'Rohit',6000),(5,'Nitin',4000),(6,'Sunny',7500);

### Use the Select Command to Query the Data

SELECT * FROM employee;

### Write a Query to print all those Emplyee Records who are gETTING mORE Salary then Ranbir

    SELECT * FROM  employee where salary > (select salary from employee where name ='Rohit');


### Use of In and Not In
#### Write a Query to Print all order which where placed in 'Seattle' or 'Goa'

    select * from orders_data;

    select * from orders_data where state IN('Seattle','Goa')

### Command To Create a TABLE

    create table customer_order_data
    (
        order_id int,
        cust_id int,
        supplier_id int,
        cust_country varchar(50)
    );

### Synatx To Insert data into a TABLE

    insert into customer_order_data values(101,200,300,'USA'),(102,201,301,'INDIA'),(103,202,302,'USA'),(104,203,303,'UK');

### Use the Select Command to Query the Data

    select * from customer_order_data;

### Command To Create a TABLE

    create table supplier_data
    (
        supplier_id int,
        sup_country varchar(50)
    );

### Synatx To Insert data into a TABLE

    insert into supplier_data values(300,'USA'),(303,'UK');

### Use the Select Command to Query the Data

    select * from supplier_data

### Write a  Query to find all the customer Data Where Customer and Supplier Both Living in Same Country ADD

    select  *  from customer_order_data  where cust_country IN (SELECT DISTINCT sup_Country from supplier_data);
### Case When in SQL 

### Command To Create a TABLE

     Create table student_marks
    (
        stu_id int,
        stu_name varchar(50),
        total_marks int
    );

### Synatx To Insert data into a TABLE

    insert into student_marks values(1,'Shashank',50);
    insert into student_marks values(2,'Rahul',91);
    insert into student_marks values(3,'Amit',74);
    insert into student_marks values(4,'Nikhil',65);
    insert into student_marks values(5,'Rohit',86);
    insert into student_marks values(6,'Deepak',77);

    select * from student_marks;


### Write a query to caluclate the grades for a student by following below criteria

     marks >= 90 , grade A+
     marks < 90 and marks >=85, grade A
     marks < 85 and marks >=75, grade B+
     marks < 75 and marks >=60, grade B
     marks < 60 , grade C


###  Uber SQL Interview questions

        create table tree
        (
            node int,
            parent int
        );
        insert into tree values (5,8),(9,8),(4,5),(2,9),(1,5),(3,9),(8,null);

    SELECT * FROM tree;

### Write the Query to Print the Type of Each Node.

    select node, 
            CASE 
                when node not in (select distinct parent from tree where parent is NOT NULL) then 'LEAF'
                when parent is null then 'ROOT'
                else 'INNER'
            END as node_type 
    from tree;

### Example for Case When with Group By - Amazon SQL Questions

    create table transactions
    (
        trx_date date,
        merchant_id varchar(10),
        amount int,
        payment_mode varchar(10)
    );

    insert into transactions values('2022-04-02','m1',150,'CASH');
    insert into transactions values('2022-04-02','m1',500,'ONLINE');
    insert into transactions values('2022-04-03','m2',450,'ONLINE');
    insert into transactions values('2022-04-03','m1',100,'CASH');
    insert into transactions values('2022-04-03','m3',600,'CASH');
    insert into transactions values('2022-04-05','m5',200,'ONLINE');
    insert into transactions values('2022-04-05','m2',100,'ONLINE');


    select * from transactions;

    ## Wite a Quey to Calculate total AMOUNT RECIVED IN CASH & RECIVED ONLINE for Each Merchant ?

    select merchant_id,
           sum(case when payment_mode = 'CASH' then amount else 0 end) as cash_amount,
           sum(case when payment_mode = 'ONLINE' then amount else 0 end) as online_amount
    from transactions 
    group by merchant_id;


###  Examples for join

    create table orders
    (
        order_id int,
        cust_id int,
        order_dat date, 
        shipper_id int
    );

    create table customers
    (
        cust_id int,
        cust_name varchar(50),
        country varchar(50)
    );

    create table shippers
    (
        ship_id int,
        shipper_name varchar(50)
    );

    insert into orders values(10308, 2, '2022-09-15', 3);
    insert into orders values(10309, 30, '2022-09-16', 1);
    insert into orders values(10310, 41, '2022-09-19', 2);

    insert into customers values(1, 'Neel', 'India');
    insert into customers values(2, 'Nitin', 'USA');
    insert into customers values(3, 'Mukesh', 'UK');

    insert into shippers values(3,'abc');
    insert into shippers values(1,'xyz');

    select * from orders;
    select * from customers;
    select * from shippers

### Perform inner JOIN
#### Get the customer informations for each order order, if value of customer is present in orders TABLE

    select  o.*,c.*  from orders o INNER JOIN customers c where o.cust_id = c.cust_id;

### Left Join

    select  o.*,c.*  from orders o LEFT JOIN customers c ON o.cust_id = c.cust_id;

### RIGHT jOIN

    select  o.*,c.*  from orders o RIGHT JOIN customers c ON o.cust_id = c.cust_id;

## CROSS JOIN 

    select  o.*,c.*  from orders o CROSS JOIN customers c; 


### How to join more than 2 datasets?

     perform inner JOIN
    #get the customer informations for each order order, if value of customer is present in orders TABLE
     also get the information of shipper name
    select 
    o.*, c.*, s.*
    from orders o
    inner join customers c on o.cust_id = c.cust_id
    inner join shippers s on o.shipper_id = s.ship_id;

### Command To Create a TABLE

    create table employees_full_data
    (
        emp_id int,
        name varchar(50),
        mgr_id int
    );

### Synatx To Insert data into a TABLE

    insert into employees_full_data values(1, 'Shashank', 3);
    insert into employees_full_data values(2, 'Amit', 3);
    insert into employees_full_data values(3, 'Rajesh', 4);
    insert into employees_full_data values(4, 'Ankit', 6);
    insert into employees_full_data values(6, 'Nikhil', null);

select * from employees_full_data;

### Write a query to print the distinct names of managers??



