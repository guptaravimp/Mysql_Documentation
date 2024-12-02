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
create database finaljointable;
use finaljointable;
CREATE TABLE Project(
    id INT PRIMARY KEY,
    empID INT,
    name  VARCHAR(20),
    startdate DATE,
    clientId INT,
    FOREIGN KEY (empID) REFERENCES Project(id) -- If self-referencing is needed
);
INSERT INTO Project (id, empID, name, startdate, clientID) VALUES
(1, 1, 'A', '2021-04-21', 3),
(2, 2, 'B', '2021-03-12', 1),
(3, 3, 'C', '2021-01-16', 5),
(4, 3, 'D', '2021-04-27', 2),
(5, 5, 'E', '2021-05-01', 4);

CREATE TABLE EMPLOYEE (
    id INT PRIMARY KEY,
    fname VARCHAR(50),
    lname VARCHAR(50),
    Age INT,
    emailID VARCHAR(100),
    PhoneNo VARCHAR(20),
    City VARCHAR(50),
    FOREIGN KEY (id) REFERENCES Project(id)
);

-- Insert data into EMPLOYEE table
INSERT INTO EMPLOYEE (id, fname, lname, Age, emailID, PhoneNo, City) VALUES
(1, 'Aman', 'Proto', 32, 'aman@gmail.com', '898', 'Delhi'),
(2, 'Yagya', 'Narayan', 44, 'yagya@gmail.com', '222', 'Palam'),
(3, 'Rahul', 'BD', 22, 'rahul@gmail.com', '444', 'Kolkata'),
(4, 'Jatin', 'Hermit', 31, 'jatin@gmail.com', '666', 'Raipur'),
(5, 'PK', 'Pandey', 21, 'pk@gmail.com', '555', 'Jaipur');



CREATE TABLE CLIENT (
    id INT PRIMARY KEY,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    age INT,
    emailID VARCHAR(100),
    PhoneNo VARCHAR(20),
    City VARCHAR(50),
    empID INT,
    FOREIGN KEY (empID) REFERENCES Project(id)
);

-- Insert data into CLIENT table
INSERT INTO CLIENT (id, first_name, last_name, age, emailID, PhoneNo, City, empID) VALUES
(1, 'Mac', 'Rogers', 47, 'mac@hotmail.com', '333', 'Kolkata', 3),
(2, 'Max', 'Poirier', 27, 'max@gmail.com', '222', 'Kolkata', 3),
(3, 'Peter', 'Jain', 24, 'peter@abc.com', '111', 'Delhi', 1),
(4, 'Sushant', 'Aggarwal', 23, 'sushant@yahoo.com', '45454', 'Hyderabad', 5),
(5, 'Pratap', 'Singh', 36, 'p@xyz.com', '77777', 'Mumbai', 2);
```
Here we created a finaljointable named database and create all three table and inserted table data into it 
## Now see all the joins 

# 1- INNER JOIN 
```
-- INNER JOiN
-- Enlist all the employee id's name along with the project allocated to them 
select e.id , e.fname, e.lname, p.id, p.name from employee as e 
INNER JOIN Project as p on e.id=p.empID ;
```
### table screenshot->
![Screenshot 2024-12-02 210239](https://github.com/user-attachments/assets/4dfe751c-79ea-4876-840e-9ef6cf1e0279)
## Problem 2->
-- Fetch out all the employee id's and their contact detail who have been
-- working from jaipur with the clients name working in hyderabad 
 ```
 select e.id ,e.PhoneNo, e.emailID , c.first_name, c.last_name from employee as e
 INNER JOIN client as c on e.id=c.empID where e.City='Jaipur' and c.City='Hyderabad';
 ```
## SEE the output table ->
![Screenshot 2024-12-02 211320](https://github.com/user-attachments/assets/6e0efafe-df26-470a-891a-a024b37b4648)

# 1- LEFT  JOIN 
-- Problem state- -- fetch out all each project allocated to each employee
```
 select * from employee as e
 LEFT JOIN Project as p ON e.id=p.empID
```
## SEE this table
![Screenshot 2024-12-02 211728](https://github.com/user-attachments/assets/3f28c53d-32a3-45ee-9b45-b204334e50bb) 
