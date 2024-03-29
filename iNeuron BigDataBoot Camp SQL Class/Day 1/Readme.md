### Create Database Command 

      CREATE DATABASE BigDataBootCamp;
      
      CREATE DATABASE Test;

### To List Down all the DATABASE

      Show Databases;

### Command to Drop the DATABASE

      Drop DATABASE Test;

### Go inside the Particular DATABASE   

     USE BigDataBootCamp;

### Command to Create a Table inside DATABASE

      CREATE TABLE IF NOT EXISTS Employee
      (
          id int,
          name VARCHAR(50)
      );

### Command to List the Schema of the Particular Table in the Database.

     SHOW CREATE TABLE Employee;

### Command to Delete the TABLE

      DROP Table Employee;

### Command To Create a TABLE

      CREATE TABLE IF NOT EXISTS Employee
      (
          id int,
          name VARCHAR(50),
          salary DOUBLE,
          hiring_date DATE

      );

###  Synatx To  Insert data into a TABLE

        INSERT INTO Employee values(1,'TheDataGuy',100000,'2022-10-15');

###  Synatax to Insert at Particular Column

        INSERT INTO Employee(salary,name,id) values(2000,'Ayush',2);

###  Insert Into Multiple Rows Using Single Insert Statement

        INSERT INTO Employee values(3,'Saurabh',100000,'2022-10-18'),(4,'Mukesh',10002,'2022-10-14');

###  Use the Select Command to Query the Data 

        Select * FROM Employee;
        
###  Example for Integrity Constraints

      Create table if not exists employee_with_constraints
      (
          id int NOT NULL,
          name VARCHAR(50) NOT NULL,
          salary DOUBLE,
          hiring_date DATE DEFAULT '2021-01-01',
          UNIQUE (id),
          CHECK (salary > 1000)
      );


### Example 1 for Integrity Constraint failure

 Exception will be thrown -> Column 'id' cannot be null
 
          insert into employee_with_constraints values(null,'Amit',3000,'2021-09-15');

### Example 2 for Integrity Constraint failure

Exception will be thrown -> Column 'name' cannot be null

          insert into employee_with_constraints values(3,null,3000,'2021-09-15');


### Example 3 for Integrity Constraint failure

--- Exception will be thrown -> Check constraint 'employee_with_constraints_chk_1' is violated.

          insert into employee_with_constraints values(1,'Shashank',500,'2021-09-15');

###  Insert corect data

          insert into employee_with_constraints values(1,'Shashank',1200,'2021-09-15');

###  Example 4 for Integrity Constraint failure

--- Exception will be thrown -> Duplicate entry '1' for key 'employee_with_constraints.id'

          insert into employee_with_constraints values(1,'Amit',1300,'2021-09-28');

### Example 5 for Integrity Constraint

            insert into employee_with_constraints values(2,'Amit',1300,null);
      
            insert into employee_with_constraints(id,name,salary) values(3,'Mukesh',2400);
            
###  Use the Select Command to Query the Data 

      select * from employee_with_constraints;

### Add alias name for constraints

            Create table if not exists employee_with_constraints_tmp
            (
                id int NOT NULL,
                name VARCHAR(50) NOT NULL,
                salary DOUBLE,
                hiring_date DATE DEFAULT '2021-01-01',
                CONSTRAINT unique_id UNIQUE (id),
                CONSTRAINT salary_check CHECK (salary > 1000)
            );

### Example for Integrity Constraint failure with alias name of constraint

 Exception will be thrown -> Check constraint 'salary_check' is violated.

           insert into employee_with_constraints_tmp values(1,'Shashank',500,'2021-09-15');
