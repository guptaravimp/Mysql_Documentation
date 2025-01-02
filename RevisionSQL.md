# 1. Now lets first create a Database of threee table (worker, Bonus, title) ,
# 2. Database name is revisionfirst
## see the documentation why use on delete cascade

```
create database revisionfirst;
use revisionfirst;
show databases;
CREATE TABLE Worker (
	WORKER_ID INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
	FIRST_NAME CHAR(25),
	LAST_NAME CHAR(25),
	SALARY INT(15),
	JOINING_DATE DATETIME,
	DEPARTMENT CHAR(25)
);
INSERT INTO Worker 
	(WORKER_ID, FIRST_NAME, LAST_NAME, SALARY, JOINING_DATE, DEPARTMENT) VALUES
		(001, 'Monika', 'Arora', 100000, '14-02-20 09.00.00', 'HR'),
		(002, 'Niharika', 'Verma', 80000, '14-06-11 09.00.00', 'Admin'),
		(003, 'Vishal', 'Singhal', 300000, '14-02-20 09.00.00', 'HR'),
		(004, 'Amitabh', 'Singh', 500000, '14-02-20 09.00.00', 'Admin'),
		(005, 'Vivek', 'Bhati', 500000, '14-06-11 09.00.00', 'Admin'),
		(006, 'Vipul', 'Diwan', 200000, '14-06-11 09.00.00', 'Account'),
		(007, 'Satish', 'Kumar', 75000, '14-01-20 09.00.00', 'Account'),
		(008, 'Geetika', 'Chauhan', 90000, '14-04-11 09.00.00', 'Admin');
select * from worker ;
CREATE TABLE Bonus (
	WORKER_REF_ID INT,
	BONUS_AMOUNT INT(10),
	BONUS_DATE DATETIME,
	FOREIGN KEY (WORKER_REF_ID)
		REFERENCES Worker(WORKER_ID)
        ON DELETE CASCADE
);
INSERT INTO Bonus  
(Worker_REF_ID, BONUS_AMOUNT, BONUS_DATE) VALUES  
(001, 5000, '16-02-20'),  
(002, 3000, '16-06-11'),  
(003, 4000, '16-02-20'),  
(004, 6000, '16-06-11');

select * from bonus;
create table title (
worker_ref_id INT,
worker_title char(25),
affected_from datetime,
foreign key (worker_ref_id)
references Worker(worker_id)
on delete cascade
);

INSERT INTO title (worker_ref_id, worker_title, affected_from) VALUES
(1, 'Manager', '2016-02-20 00:00:00'),
(2, 'Executive', '2016-06-11 00:00:00'),
(8, 'Executive', '2016-06-11 00:00:00'),
(5, 'Manager', '2016-06-11 00:00:00'),
(4, 'Asst. Manager', '2016-06-11 00:00:00'),
(7, 'Executive', '2016-06-11 00:00:00');
select * from title;

```
## You can see the database are created with all the tables 

![Screenshot 2025-01-02 155134](https://github.com/user-attachments/assets/e48c1163-8cea-46ec-8cc9-f3c98604e64c)


# 2. Now let see the E-R diagram of this table 
### Database---->reverse engineer----->stored connection select------> continue------>selectDB------>continue---->see the diagram 

![Screenshot 2025-01-02 155644](https://github.com/user-attachments/assets/01da1be4-29d0-488e-a3b1-7c1319d3bfb7)



![Screenshot 2025-01-02 155535](https://github.com/user-attachments/assets/215e6137-f285-4483-bb71-4fbf64b2f4d4)

![Screenshot 2025-01-02 155550](https://github.com/user-attachments/assets/aee5538b-de22-4353-9711-fdfa2b98309f)

![Screenshot 2025-01-02 155608](https://github.com/user-attachments/assets/ab1a729c-f1bc-4b00-aa63-fb9cc006967f)

# 3. Now lets do all data retrieval language
```
select first_name, salary from Worker;
 
````
## 3.1 select without using from clause 
### -- create a dummy table like 
  ```

select 44+11;
select now();   -- give the server time 
select lcase('Lakshya');    -- convert in upper case
```
## 3.2 where clause 
### -- reduce row on given condition
```
 
select * from Worker where salary>8000;
select * from Worker where department="HR";
```
## 3.3 between clause 
```
select * from Worker where salary between 8000 and 1000000;  -- 100000 and 8000  included
```
## 3.4 In 
### --  reduce or statement
```

-- Hr, admin 
select * from Worker where department="HR" or department="Admin";
-- better way using in clause 
select * from Worker where department in('HR','admin','developer');
-- if want to see that are not admin 
select * from worker where department not in("Admin");
````
## 3.5 is null
```
select * from Worker where salary is  null;
```
## 3.6 pattern searching 
### -- select the employee whose name start with a 
```
select * from Worker where first_name like "a%";
```
### -- select the employee whose name include a 
```
select * from Worker where first_name like "%a%";
```
## 3.7  sorting data from table 

### -- sorting salary wise 
```
select * from worker order by salary;
select * from Worker order by salary desc;
-- sorting by first name 
select * from Worker order by first_name;
```

## 3.8 distinct clause 
```
select distinct department from Worker ;
```

## 3.9  Data Grouping (group by)

###  find no of employee working in different department 

### -- group by ---> using aggregation function 
```
select department from worker group by department;
```
 ### -- iiiiiimmmmppp->  it act like distinct because we use group by without using aggregation function 
 
 ### -- count all the deaprtment how many worker worker in specific department 
 ```
select department, count(department) from worker group by department;
```

###  imp---> count ke ander wahi aayega jiska grouping karna hai here 

### avg salary per department 
```
select department, avg(salary) from Worker group by department ;
```

###  min slaary per department 
```
select department, MIN(salary) from Worker group by department ;
```
```
-- max salary per department 
select department, MAX(salary) from Worker group by department ;

-- per department total salary 
select department, SUM(salary) from Worker group by department ;
````

## 3.10 Having keyword  use for filtering with group by 

### jaise sleect ke sath where use hota hai filter ke liye waise hi 

### group gy ke sath having use hota hai filter ke liye 

#### department , count having more than two worker 

## groupby having 
```
select department, count(department)
from worker
group by department 
having count(department)>2;
```

