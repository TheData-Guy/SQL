## DAY 3:

### Create Database Command

	CREATE DATABASE class3_db;
	
### Go inside the Particular DATABASE

	Use class3_db;
	
### Command To Create a TABLE

	create table if not exists employee(
	    id int,
	    name VARCHAR(50),
	    age int,
	    hiring_date date,
	    salary int,
	    city varchar(50)
	);

### Synatx To Insert data into a TABLE

	insert into employee values(1,'Aditya', 23, '2021-08-10', 10000, 'Pune');
	insert into employee values(2,'Rahul', 25, '2021-08-10', 20000, 'Khajuraho');
	insert into employee values(3,'Sunny', 22, '2021-08-11', 11000, 'Banaglore');
	insert into employee values(5,'Amit', 25, '2021-08-11', 12000, 'Noida');
	insert into employee values(1,'Puneet', 26, '2021-08-12', 50000, 'Gurgaon');

### Use the Select Command to Query the Data

	select * from employee;

### How to perform multi updates

	update employee set age=20,salary=25000 where hiring_date = '2021-08-10';
	
### Use the Select Command to Query the Data

	select * from employee;

###  How to apply auto increment

	create table auto_inc_exmp
	(
	  id int auto_increment,
	  name varchar(20),
	  primary key (id)
	);
### Use the Insert Command to Insert the Data

	insert into auto_inc_exmp(name) values('Aditya');
	insert into auto_inc_exmp(name) values('Rahul');

### Use the Select Command to Query the Data

	select * from auto_inc_exmp;

###  Use of limit Command

	select * from employee;
	select * from employee limit 2;


### Sorting data in mysql by using 'Order By'

       select * from employee;


### Arrage data in ascending order

	select * from employee order by name;

### Arrage data in descending order

	select * from employee order by name desc;

### Display employee data in desc order of salary and if salaries are same for more than one employees arrange their data in ascedinding order of name

	select * from employee order by salary desc, name asc;

### when we ignore multilevel ordering

	select * from employee order by salary desc;

###  Write a query to find the employee who is getting maximum salary?

	select * from employee order by salary desc limit 1;


### Write a query to find the employee who is getting minium salary?

	select * from employee order by salary limit 1;

### Use the Select Command to Query the Data

	select * from employee;
### Operators and Between Commands

### List all employees who are getting salary more than 20000

	select * from employee where salary>20000;

### List all employees who are getting salary more than or equal to 20000

	select * from employee where salary>=20000;

### List all employees who are getting less than 20000

	select * from employee where salary<20000;

### List all employees who are getting salary less than or equal to 20000

	select * from employee where salary<=20000;


### Filter the record where age of employees is equal to 20

	select * from employee where age=20;

### Filter the record where age of employees is not equal to 20

#### we can use != or we can use <>

	select * from employee where age != 20;
	select * from employee where age <> 20;

### Find those employees who joined the company on 2021-08-11 and their salary is less than 11500

	select * from employee where hiring_date = '2021-08-11' and salary<11500;

### Find those employees who joined the company after 2021-08-11 or  their salary is less than 20000

	select * from employee where hiring_date > '2021-08-11' or salary<20000;

### How to use Between operation in where clause
#### Get all employees data who joined the company between hiring_date 2021-08-05 to 2021-08-11

	select * from employee where hiring_date between '2021-08-05' and '2021-08-11';
	
###  get all employees data who are getting salary in the range of 10000 to 28000

	select * from employee where salary between 10000 and 28000;

### Like Operators 

### Get all those employees whose name starts with 'S'

	select * from employee where name like 'S%';

### Get all those employees whose name starts with 'Sh'

	select * from employee where name like 'Sh%';

### get all those employees whose name ends with 'l'

	select * from employee where name like '%l';
	
### get all those employees whose name starts with 'S' and ends with 'k'

	select * from employee where name like 'S%k';

### Get all those employees whose name will have exact 5 characters

	select * from employee where name like '_____';
	
### Return all those employees whose name contains atleast 5 characters

	select * from employee where name like '%_____%';

### How to use IS NULL or IS NOT NULL in the where clause

	insert into employee values(10,'Kapil', null, '2021-08-10', 10000, 'Assam');
	insert into employee values(11,'Nikhil', 30, '2021-08-10', null, 'Assam');
	
### Use the Select Command to Query the Data

	select * from employee;
	
### IS NULL & NOT NULL Operator.

### get all those employees whos age value is null

	select * from employee where age is null;
	
### Use the Select Command to Query the Data

	select * from employee;

### Get all those employees whos salary value is not null

	select * from employee where salary is not null;

### Group By Clause

###  Table and Data for Group By

	create table orders_data
	(
	 cust_id int,
	 order_id int,
	 country varchar(50),
	 state varchar(50)
	);
	
### Use the Insert Command to Insert the Data

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

### Calculate total order placed country wise

	select country, count(*) as order_count_by_each_country from orders_data group by country;

### Write a query to find the total salary by each age group 

	
 	select age, sum(salary) as total_salary_by_each_age_group from employee group by age;

### Calculate different aggregated metrices for salary

	select age, 
		   sum(salary) as total_salary_by_each_age_group,
	       max(salary) as max_salary_by_each_age_group,
	       min(salary) as min_salary_by_each_age_group,
	       avg(salary) as avg_salary_by_each_age_group,
	       count(*) as total_employees_by_each_age_group
	from employee group by age;
