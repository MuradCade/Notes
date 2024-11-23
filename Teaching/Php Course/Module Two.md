# Welcome To Module Two

module two contains everythig related to database

Table of content :- 

- lesson 1: database introduction theory

- lesson 2: ui database

- lesson 3  : sql explained

- lesson 4 : Relationship in Database

- lesson 5 : How to build database for bussiness

# What is data?

Data is a collection of facts, numbers, words, or other information that can be used for analysis or decision making.

# What is Database?

A database is *an organized collection of structured information, or data*, typically stored electronically in a computer system.

in this course we will learn about relational database , its database that uses sql(structured query language ) as intruction to do to something.

# UI of the mysql databse in xampp

we will do the following :-

- create database

- create table (primary key,not null) , but before creating table we need to understand data types in sql(nocyada xogta ay noqonayso)
  
  - primary key : primary key is not data type , its responsible to reduce redunance of data inside the database.
  
  - numeric : this data type represent everything related to numbers as integer , double,float.
  
  - String : this data type represent every thing related to text such as character(hal xaraf kaliya tusale 'A') or varchar(qoral dhamaystiran , tusale mustafe)
  
  - Date : this data type represent date  (qaabka date loo qoro aya ah  manlinta/bisha/sanadka = 01/23/2024)
  
  - Time : this data type represent time (10:00),
  
  - Time Stamp : is date and time combined , usually database create thier own date and time.

- insert data into table

- display all data

- update table data

- delete table data 

- add new column to your table

- delete column from your table

## Structure Query Language (SQL)

1- create database using sql

```sql
create database name_of_the_database;
```

2- create table using sql and understanding data type

```sql
create table name_of_the_table(studentid int(4) primary key , 
studentname varchar(50)not null ,marks character(2) not null , dob date);
```

3- insert data into table

```sql
insert into table_name(studentid,studentname,marks,dob)values(1001,
'mustafe kaahin','A', '2024/11/23');
```

4- select and where clause

```sql
// query 1
select * from table_name;

//query 2
select * from table_name where condition ;
```

5- update data inside table

```sql
update table table_name set studentname = 'abdi warfaa' 
where studentid = 1001
```

6- delete data inside the table

```sql
delete from table_name where studentid = 1001;
```

7- count function in sql

```sql
select count(*) from table_name;
```

8- sum function in sql (gets total of added number)

```sql
select sum(attribute) from table_name;
```

9-  trunicate : allows you to delete all table content at once

```sql
trunicate table table_name;
```

10- add new column in the table

```sql
alter table table_name add column parentname varchar(50);
```

11- drop column from table

```sql
alter table drop column parentname;
```

12- drop table (allows us to delete entire table using sql)

```sql
drop table table_name;
```

## Relationship in database

relationship are important when it comes to mysql database also known as relational database , relation are the way it descripes relation between two or more tables.

relational types are:-

**1- One To One**

one to one relationship describes two table that passes information to eac other and neither one of them have the redundant data.

**Example**

image we have two tables , one is table called studentinformation and the other is table called class.

- studentinformation table contains the following:-
  
  - studentid
  
  - studentname
  
  - age
    
    ```sql
    // create table
    create table studentinformation(studentid int(4) primary key,
    studentname varchar(50),age int(3));
    
    // insert data below inside the table
    insert into studentinformation(studentid,studentname,age)values(
        1001,'mustafe',19);
    ```
  
  | studentid | studentname | age |
  | --------- | ----------- | --- |
  | 1001      | mustafe     | 18  |
  | 1002      | ahmed       | 19  |

- class table contain the following:-
  
  - classid
  
  - classname
  
  - studentid
    
    ```sql
    // create class table and assign the relationship
    create table class(classid int(2) primary key, 
    classname varchar(50) , studentid int(4) , foreign key(studentid)
    references studentinformation(studentid));
    
    // insert data below to class table
    insert into class(classid,classname,studentid)values(1,'junior',
    1002);
    ```

| classid | classname | studentid |
| ------- | --------- | --------- |
| 1       | junior    | 1001      |
| 2       | senior    | 1002      |

- **Joint Table studentinformation and class**
  
  sql code below:-
  
  ```sql
  select studentniformation.studentid , studentinformation.studentname,
  studentinformation.age, class.classname from studentinformation
  inner join class on studentinformation.studentid = class.studentid;
  ```

| studentid | studentname | age | classname |
| --------- | ----------- | --- | --------- |
| 1001      | mustafe     | 18  | junior    |
| 1002      | ahmed       | 19  | senior    |

**2- One To Many**

one to many relationship descripes when data in one of the tables are redandent.

image we have 2 tables  , table one is called customer and table two orders

- **Customer**
  
  - customerid
  
  - customername
  
  - customerphone
  
  ```sql
  // create customer table
  create table customer(customerid int(4) primary key , 
  customername varchar(50) , customerphone varchar(50));
  
  // insert data below to the customer table 
  insert into customer(customerid,customername,customerphone)values(
      1001,'mustafe','06338988585');
  ```

| customerid | customername | customerphone |
| ---------- | ------------ | ------------- |
| 2001       | mustafe      | 06338988585   |
| 2002       | mumin        | 06335334335   |

- Orders Table
  
  - orderid
  
  - productname
  
  - price
  
  - customerid
  
  ```sql
  create table orders(orderid int(4) primary key , 
  productname varchar(50) , price varchar(50), customerid int(4),
  foreign key (customerid) references customer(customerid));
  
  // insert data below to orders class
  insert into orders(orderid,productname,price,customerid)values(
      101,'mobile','$100', 201);
  ```

| orderid | productname | price | customerid |
| ------- | ----------- | ----- | ---------- |
| 101     | mobile      | 100   | 201        |
| 102     | watch       | 50    | 201        |
| 103     | TV          | 20    | 201        |

- **Join two tables : (joining two table help to organise data)**

sql code below

```sql
select customer.customerid,customer.customername,customer.customerphone,
orders.productname , orders.price from customer inner join orders on
customer.customerid = orders.customerid;
```

| customerid | customername | customerphone | productname | price |
| ---------- | ------------ | ------------- | ----------- | ----- |
| 201        | mustafe      | 06338988585   | mobile      | 100   |
| 201        | mustafe      | 06338988585   | watch       | 50    |
| 201        | mustafe      | 06338988585   | TV          | 20    |

**3- Many To Many**

many to many relationship is represent 3 table that share information.

image we have 3 tables , table one is students , table two is present , table three is absent, we need to create attendance database that enables us to mark attended student. if student is present the present table will contain 1(which means student attended the lecture) , if student is not present then absent class will contain 1 and if not it will contain 0.

- **Student Tabel**
  
  - studentid
  
  - studentname
  
  - coursename
    
    ```sql
    // create table called student
    create table student(stuedntid int(4) primary key , 
    studentname varchar(50) , coursename varchar(50));
    
    // insert below data into student table
    ```
    
    insert into student(studentid,studentname,coursename)values(
    
        101,'mustafe','database');
    
    ```
    
    ```

| studentid | studentname | coursename |
| --------- | ----------- | ---------- |
| 101       | mustafe     | database   |

- **Present Table**
  
  - id
  
  - presentcolumn
  
  - studentid

```sql
// create table called present table and connect to student table
create table present(id int(4) primary key , presentcolumn varchar(50),
studentid int(4) , foreign key (studentid) references student(studentid));

// insert data below to present table
insert into present(id,presentcolumn,studentid)values(
    1,'yes',101);
```

| id  | presentcolumn | studentid |
| --- | ------------- | --------- |
| 1   | yes           | 101       |

- **Absent Table**
  
  - id
  
  - absentcolumn
  
  - studentid
  
  ```sql
  // create table called present table and connect to student table
  create table absent(id int(4) primary key , absentcolumn varchar(50),
  studentid int(4) , foreign key (studentid) references student(studentid));
  
  // insert data below to present table
  insert into absent(id,absentcolumn,studentid)values(
      1,'no',101);
  ```

| id  | absentcolumn | studentid |
| --- | ------------ | --------- |
| 1   | no           | 101       |

- now joint all the data inside the 3 tables  and display it like below

```sql
// generate result below
select student.studentid, student.studentname,student.coursename,
present.presentcolumn,absent.absentcolumn from student inner join present
on student.studentid = present.presentcolumn inner join absent on
student.studentid = absent.absentcolumn;
```

| studentid | studentname | coursename | present | absent |
| --------- | ----------- | ---------- | ------- | ------ |
| 101       | mustafe     | database   | yes     | no     |

# How to build database to Bussiness

**1- Conceptual Data Model**: in this step we are gathering information about the bussiness such as:-

- why bussiness needs database?

- what kind of database does the bussiness needs?

- what is the important area that database should store.

**2- Representational Data Model**: in this step we sketch how the database will look like , structure of the tables its called schema, we present what we designed to make change if the bussiness request it.

**2- Physical Data Model** : in this step we build the database using sql and we make it usable.
