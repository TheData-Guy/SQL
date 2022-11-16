### Creating the Database 

      CREATE DATABASE class5_db;
      
### Go inside the Particular DATABASE

      USE  class5_db;
### Command To Create a TABLE

      create table customers
      (
          id int,
          name varchar(50)
      );

      create table orders
      (
          order_id int,
          amount int,
          cust_id int
      );

### Synatx To Insert data into a TABLE

            insert into customers values(1,'John');

            insert into customers values(2,'David');

            insert into customers values(3,'Ronn');

            insert into customers values(4,'Betty');

-----------------------------------------------------------------

            insert into orders values(1,100,10);

            insert into orders values(2,500,3);

            insert into orders values(3,300,6);

            insert into orders values(4,800,2);

            insert into orders values(5,350,1);
            
### Use the Select Command to Query the Data

      select  *from customers;

      select * from orders;

###  Get the orders information along with customers full details if order amount were greater than 400

### Fast Query Execution 

      select c.*,o.* 
      from orders o
      inner join customers c on o.cust_id=c.id
      where o.amount >400

####  Slow Query Execution 

      select c.*,o.* 
      from orders o
      inner join customers c on o.cust_id=c.id and o.amount >400;


###  Window Functions

      create table shop_sales_data
      (
      sales_date date,
      shop_id varchar(5),
      sales_amount int
      );

      insert into shop_sales_data values('2022-02-14','S1',200);
      insert into shop_sales_data values('2022-02-15','S1',300);
      insert into shop_sales_data values('2022-02-14','S2',600);
      insert into shop_sales_data values('2022-02-15','S3',500);
      insert into shop_sales_data values('2022-02-18','S1',400);
      insert into shop_sales_data values('2022-02-17','S2',250);
      insert into shop_sales_data values('2022-02-20','S3',300);

      SELECT * from shop_sales_data;

#### Total count of sales for each shop using window function

  #### Working functions - SUM(), MIN(), MAX(), COUNT(), AVG()

### If we Only use partition by In Over Clause with count

      SELECT *,
             count(*)  over(partition by shop_id) as total_sales_count_by_shops
       FROM shop_sales_data;      
      

### If we  use Partition by &  Order by both In Over Clause with count

      SELECT *,
             count(*)  over(partition by shop_id order by sales_amount DESC) as total_sales_count_by_shops
       FROM shop_sales_data;

### If we Only use Order by In Over Clause

      SELECT* ,
             sum(sales_amount)  over( order by sales_amount DESC) as total_sum_of_sales
       FROM shop_sales_data;

 ### If we Only use partition by In Over Clause

      SELECT *,
            sum(sales_amount) over(partition by shop_id) as total_sales_count_by_shops
       FROM shop_sales_data; 

### If we  use Partition by &  Order by both In Over Clause 

      SELECT *,
             sum(sales_amount)  over(partition by shop_id order by sales_amount DESC) as total_sales_count_by_shops
       FROM shop_sales_data;

### Simple Group by 

 Select shop_id, count(*) as total_sale_count_by_shops from shop_sales_data group by shop_id;

### Rolling Average Amazon Sales Question 

       create table amazon_sales_data
      (
          sales_data date,
          sales_amount int
      );

      insert into amazon_sales_data values('2022-08-21',500);
      insert into amazon_sales_data values('2022-08-22',600);
      insert into amazon_sales_data values('2022-08-19',300);
      insert into amazon_sales_data values('2022-08-18',200);
      insert into amazon_sales_data values('2022-08-25',800);

      select * from amazon_sales_data;

### Query - Calculate the date wise rolling average of amazon sales


      select *,
          AVG(sales_amount) OVER(order by sales_data) as Average_of_Amazon_Sales 
      from amazon_sales_data;

---------------------------------------------------------------------------------------------------

      select *,
             avg(sales_amount) over(order by sales_data) as rolling_avg,
             sum(sales_amount) over(order by sales_data) as rolling_sum
      from amazon_sales_data;



### Rank(), Row_Number(), Dense_Rank()  in Window functions.

      insert into shop_sales_data values('2022-02-19','S1',400);
      insert into shop_sales_data values('2022-02-20','S1',400);
      insert into shop_sales_data values('2022-02-22','S1',300);
      insert into shop_sales_data values('2022-02-25','S1',200);
      insert into shop_sales_data values('2022-02-15','S2',600);
      insert into shop_sales_data values('2022-02-16','S2',600);
      insert into shop_sales_data values('2022-02-16','S3',500);
      insert into shop_sales_data values('2022-02-18','S3',500);
      insert into shop_sales_data values('2022-02-19','S3',300);

      Select  * from shop_sales_data;

### Rank(), Row_Number(), Dense_Rank() Query Execution 

      select *,
             row_number() over(partition by shop_id order by sales_amount desc) as row_num,
             rank() over(partition by shop_id order by sales_amount desc) as rank_val,
             dense_rank() over(partition by shop_id order by sales_amount desc) as dense_rank_val
      from shop_sales_data;

### Practice Quesion on Rank(), Row_Number(), Dense_Rank()

      create table employees
      (
          emp_id int,
          salary int,
          dept_name VARCHAR(30)

      );

      insert into employees values(1,10000,'Software');
      insert into employees values(2,11000,'Software');
      insert into employees values(3,11000,'Software');
      insert into employees values(4,11000,'Software');
      insert into employees values(5,15000,'Finance');
      insert into employees values(6,15000,'Finance');
      insert into employees values(7,15000,'IT');
      insert into employees values(8,12000,'HR');
      insert into employees values(9,12000,'HR');
      insert into employees values(10,11000,'HR');

      select * from employees;

###  Query - get one employee from each department who is getting maximum salary (employee can be random if salary is same)    

      select 
          tmp.*
      from (select *,
              row_number() over(partition by dept_name order by salary desc) as row_num
          from employees) tmp
      where tmp.row_num = 1;



### Query - get all employees from each department who are getting maximum salary

      select 
          tmp.*
      from (select *,
              rank() over(partition by dept_name order by salary desc) as rank_num
          from employees) tmp
      where tmp.rank_num = 1;
  
### Query - get all top 2 ranked employees from each department who are getting maximum salary

      select 
          tmp.*
      from (select *,
              dense_rank() over(partition by dept_name order by salary desc) as dense_rank_num
          from employees) tmp
      where tmp.dense_rank_num <= 2;



### Example for Lag and Lead

      create table daily_sales
      (
      sales_date date,
      sales_amount int
      );


      insert into daily_sales values('2022-03-11',400);
      insert into daily_sales values('2022-03-12',500);
      insert into daily_sales values('2022-03-13',300);
      insert into daily_sales values('2022-03-14',600);
      insert into daily_sales values('2022-03-15',500);
      insert into daily_sales values('2022-03-16',200);

      select * from daily_sales;


      select *,
            lag(sales_amount, 1) over(order by sales_date) as pre_day_sales
      from daily_sales;

### Query - Calculate the differnce of sales with previous day sales

   #### Here null will be derived
   
      select sales_date,
             sales_amount as curr_day_sales,
             lag(sales_amount, 1) over(order by sales_date) as prev_day_sales,
             sales_amount - lag(sales_amount, 1) over(order by sales_date) as sales_diff
      from daily_sales;

 ####  Here we can replace null with 0

      select sales_date,
             sales_amount as curr_day_sales,
             lag(sales_amount, 1, 0) over(order by sales_date) as prev_day_sales,
             sales_amount - lag(sales_amount, 1, 0) over(order by sales_date) as sales_diff
      from daily_sales;


### Diff between Lead and Lag

####  Lag Query 

      select *,
            lag(sales_amount, 1) over(order by sales_date) as pre_day_sales
      from daily_sales;
      
#### Lead Query 

      select *,
            lead(sales_amount, 1) over(order by sales_date) as next_day_sales
      from daily_sales;


### How to use Frame Clause - Rows BETWEEN

      select * from daily_sales;

      select *,
            sum(sales_amount) over(order by sales_date rows between 1 preceding and 1 following) as prev_plus_next_sales_sum
      from daily_sales;

------------------------------------------------------------------------------------------------------------------------------------------------------------
      select *,
            sum(sales_amount) over(order by sales_date rows between 1 preceding and current row) as prev_plus_next_sales_sum
      from daily_sales;

------------------------------------------------------------------------------------------------------------------------------------------------------------
      select *,
            sum(sales_amount) over(order by sales_date rows between current row and 1 following) as prev_plus_next_sales_sum
      from daily_sales;

------------------------------------------------------------------------------------------------------------------------------------------------------------
      select *,
            sum(sales_amount) over(order by sales_date rows between 2 preceding and 1 following) as prev_plus_next_sales_sum
      from daily_sales;

------------------------------------------------------------------------------------------------------------------------------------------------------------
      select *,
            sum(sales_amount) over(order by sales_date rows between unbounded preceding and current row) as prev_plus_next_sales_sum
      from daily_sales;

------------------------------------------------------------------------------------------------------------------------------------------------------------
      select *,
            sum(sales_amount) over(order by sales_date rows between current row and unbounded following) as prev_plus_next_sales_sum
      from daily_sales;

------------------------------------------------------------------------------------------------------------------------------------------------------------
      select *,
            sum(sales_amount) over(order by sales_date rows between unbounded preceding and unbounded following) as prev_plus_next_sales_sum
      from daily_sales;

------------------------------------------------------------------------------------------------------------------------------------------------------------
      # Alternate way to esclude computation of current row
      select *,
            sum(sales_amount) over(order by sales_date rows between unbounded preceding and unbounded following) - sales_amount as prev_plus_next_sales_sum
      from daily_sales;
      
------------------------------------------------------------------------------------------------------------------------------------------------------------

### How to work with Range Between

      select *,
            sum(sales_amount) over(order by sales_amount range between 100 preceding and 200 following) as prev_plus_next_sales_sum
      from daily_sales;

### Calculate the running sum for a week
### Calculate the running sum for a month

      insert into daily_sales values('2022-03-20',900);
      insert into daily_sales values('2022-03-23',200);
      insert into daily_sales values('2022-03-25',300);
      insert into daily_sales values('2022-03-29',250);


      select * from daily_sales;

      select *,
             sum(sales_amount) over(order by sales_date range between interval '6' day preceding and current row) as running_weekly_sum
      from daily_sales;