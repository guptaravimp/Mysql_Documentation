# Introduction to JOIN in MySQL
## A JOIN clause is used in SQL to combine rows from two or more tables based on a related column between them. MySQL supports different types of JOINs to retrieve and analyze relational data effectively.

# Types of MySQL JOINs
### 1. INNER JOIN
### 2. LEFT JOIN (or LEFT OUTER JOIN)
### 3. RIGHT JOIN (or RIGHT OUTER JOIN)
### 4. FULL OUTER JOIN (Not directly supported in MySQL but can be achieved with a UNION)
### 5. CROSS JOIN
### 6. SELF JOIN
## #7. NATURAL JOIN
# lets take a table and apply these on this database 
# screenshot of table 
![Screenshot 2024-12-02 201215](https://github.com/user-attachments/assets/5030c4d2-a982-4d14-8dba-2d0357747275)
## Now lets create a all table then apply the all join 
```
create database if not exists joindb;
use joindb;
create table Project(
id INT primary key,
empId INT ,
name varchar(255),
startdate DATE,
clientid INT,
FOREIGN KEY (empID) REFERENCES Project(id)
);
insert into Project (id,empId,name,startdate,clientid) values
(1, 1, 'A', '2021-04-21', 3),
(2, 2, 'B', '2021-03-12', 1),
(3, 3, 'C', '2021-01-16', 5),
(4, 3, 'D', '2021-04-27', 2),
(5, 5, 'E', '2021-05-01', 4);


CREATE TABLE Employee (
    id INT PRIMARY KEY,
    fname VARCHAR(50),
    lname VARCHAR(50),
    Age INT,
    emailID VARCHAR(100),
    PhoneNo VARCHAR(15),
    City VARCHAR(50)
);

INSERT INTO Employee (id, fname, lname, Age, emailID, PhoneNo, City)
VALUES
(1, 'Aman', 'Proto', 32, 'aman@gmail.com', '898', 'Delhi'),
(2, 'Yagya', 'Narayan', 44, 'yagya@gmail.com', '222', 'Palam'),
(3, 'Rahul', 'BD', 22, 'rahul@gmail.com', '444', 'Kolkata'),
(4, 'Jatin', 'Hermit', 31, 'jatin@gmail.com', '666', 'Raipur'),
(5, 'PK', 'Pandey', 21, 'pk@gmail.com', '555', 'Jaipur');


CREATE TABLE Client (
    id INT PRIMARY KEY,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    age INT,
    emailID VARCHAR(100),
    PhoneNo VARCHAR(20),
    City VARCHAR(50),
    empID INT
);

-- Insert data into CLIENT table
INSERT INTO Client (id, first_name, last_name, age, emailID, PhoneNo, City, empID) VALUES
(1, 'Mac', 'Rogers', 47, 'mac@hotmail.com', '333', 'Kolkata', 3),
(2, 'Max', 'Poirier', 27, 'max@gmail.com', '222', 'Kolkata', 3),
(3, 'Peter', 'Jain', 24, 'peter@abc.com', '111', 'Delhi', 1),
(4, 'Sushant', 'Aggarwal', 23, 'sushant@yahoo.com', '45454', 'Hyderabad', 5),
(5, 'Pratap', 'Singh', 36, 'p@xyz.com', '77777', 'Mumbai', 2);
```
Here we created a joindb named database and create all three table and inserted table data into it 
## Now see all the joins 
