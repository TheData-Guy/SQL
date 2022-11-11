# SQL : From Basic to Advanced Level!
![](/images/sql1.png)


## SQL 

SQL is a standard language for accessing and manipulating databases.
- SQL stands for Structured Query Language
- SQL lets you access and manipulate databases
- SQL became a standard of the American National Standards Institute (ANSI) in 1986, and of the International Organization for Standardization (ISO) in 1987.

## What Can SQL do ?

- SQL can execute queries against a database
- SQL can retrieve data from a database
- SQL can insert records in a database
- SQL can update records in a database
- SQL can delete records from a database
- SQL can create new databases
- SQL can create new tables in a database
- SQL can create stored procedures in a database
- SQL can create views in a database
- SQL can set permissions on tables, procedures, and views.

## What is Database ?

- Database is the collection of organized data which is structured and is stored electronically on a computer system. Databases can store data in the form of tables depending upon the type of database. The database's primary goal is to store a huge amount of data.

- Databases are used to store a large number of dynamic websites on the Internet today. Data can then be accessed, managed, updated, regulated, and organized efficiently. For writing and retrieving data, most databases utilize structured query language (SQL).

## What is DBMS ( Database Management System ) ?

 - Database Management System (DBMS) is a software used for the storage, access and manipulation of data. Along with this, DBMS helps in securing data and getting useful insights from it. Common DBMS software are MySQL, PostgreSQL, Microsoft Access, MariaDB, SQLite and Microsoft SQL Server.

## What is RDBMS ( Relational Database Management System ) ?

  - An RDBMS is a type of database management system (DBMS) that stores data in a row-based table structure which connects related data elements. An RDBMS includes functions that maintain the security, accuracy, integrity and consistency of the data. 

## NoSQL Database 

 - NoSQL databases (aka "not only SQL") are non-tabular databases and store data differently than relational tables. NoSQL databases come in a variety of types based on their data model. The main types are document, key-value, wide-column, and graph. They provide flexible schemas and scale easily with large amounts of data and high user loads.

### NoSQL Database Feature 
 
- Flexible schemas
- Horizontal scaling
- Fast queries due to the data model
- Ease of use for developers

### Type of NoSQL Database 

![](/images/sql2.png)

 
- __Document databases__ store data in documents similar to JSON (JavaScript Object Notation) objects. Each document contains pairs of fields and values. The values can typically be a variety of types including things like strings, numbers, booleans, arrays, or objects.
- __Key-value databases__ are a simpler type of database where each item contains keys and values.
- __Wide-column__ stores store data in tables, rows, and dynamic columns.
- __Graph databases__ store data in nodes and edges. Nodes typically store information about people, places, and things, while edges store information about the relationships between the nodes.

### SQL Vs NoSQL 

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-c3ow{border-color:inherit;text-align:center;vertical-align:top}
.tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:top}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-c3ow">SQL Databases</th>
    <th class="tg-c3ow">NoSQL Databases</th>
    <th class="tg-0pky"></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0pky">Data Storage Model</td>
    <td class="tg-0pky">Tables with fixed rows and columns</td>
    <td class="tg-0pky">Document: JSON documents, Key-value: key-value pairs, Wide-column: tables with rows and dynamic columns, Graph: nodes and edges</td>
  </tr>
  <tr>
    <td class="tg-0pky">Development History</td>
    <td class="tg-0pky">Developed in the 1970s with a focus on reducing data duplication</td>
    <td class="tg-0pky">Developed in the late 2000s with a focus on scaling and allowing for rapid application change driven by agile and DevOps practices.</td>
  </tr>
  <tr>
    <td class="tg-0pky">Examples</td>
    <td class="tg-0pky">Oracle, MySQL, Microsoft SQL Server, and PostgreSQL</td>
    <td class="tg-0pky">Document: MongoDB and CouchDB, Key-value: Redis and DynamoDB, Wide-column: Cassandra and HBase, Graph: Neo4j and Amazon Neptune</td>
  </tr>
  <tr>
    <td class="tg-0pky">Primary Purpose</td>
    <td class="tg-0pky">General purpose</td>
    <td class="tg-0pky">Document: general purpose, Key-value: large amounts of data with simple lookup queries, Wide-column: large amounts of data with predictable query patterns, Graph: analyzing and traversing relationships between connected data</td>
  </tr>
  <tr>
    <td class="tg-0pky">Schemas</td>
    <td class="tg-0pky">Rigid</td>
    <td class="tg-0pky">Flexible</td>
  </tr>
  <tr>
    <td class="tg-0pky">Scaling</td>
    <td class="tg-0pky">Vertical (scale-up with a larger server)</td>
    <td class="tg-0pky">Horizontal (scale-out across commodity servers)</td>
  </tr>
  <tr>
    <td class="tg-0pky">Multi-Record ACID Transactions</td>
    <td class="tg-0pky">Supported</td>
    <td class="tg-0pky">Most do not support multi-record ACID transactions. However, some — like MongoDB — do.</td>
  </tr>
  <tr>
    <td class="tg-0pky">Joins</td>
    <td class="tg-0pky">Typically required</td>
    <td class="tg-0pky">Typically not required</td>
  </tr>
  <tr>
    <td class="tg-0pky">Data to Object Mapping</td>
    <td class="tg-0pky">Requires ORM (object-relational mapping)</td>
    <td class="tg-0pky">Many do not require ORMs. MongoDB documents map directly to data structures in most popular programming languages.</td>
  </tr>
</tbody>
</table>



 

  



  
