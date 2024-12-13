# create a DB based on these data given in image 
###  Screenshot

![Screenshot 2024-12-14 005255](https://github.com/user-attachments/assets/8b8d3ec9-cce8-4eee-bc22-70fe0607ed2e)

## created db sql code 
```
drop database orgg;
create database orgg;
show databases;
use orgg;
CREATE TABLE Worker (
    Worker_id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    first_name VARCHAR(25),
    last_name VARCHAR(25),
    salary INT,
    joining_date DATETIME,
    department VARCHAR(25)
);
-- no need to write the small character it take already 
INSERT INTO Worker (FIRST_NAME, LAST_NAME, SALARY, JOINING_DATE, DEPARTMENT) VALUES  
('Monika', 'Arora', 100000, '2020-02-14 09:00:00', 'HR'),  
('Niharika', 'Verma', 30000, '2011-06-14 09:00:00', 'Admin'),  
('Vishal', 'Singhal', 30000, '2020-02-14 09:00:00', 'HR'),  
('Amitabh', 'Singh', 50000, '2020-02-14 09:00:00', 'Admin'),  
('Vivek', 'Bhat', 50000, '2011-06-14 09:00:00', 'Admin'),  
('Vipul', 'Diwan', 20000, '2011-06-14 09:00:00', 'Account'),  
('Satish', 'Kumar', 75000, '1928-01-14 09:00:00', 'Account'),  
('Geetika', 'Chauhan', 90000, '2011-04-14 09:00:00', 'Admin');
select * from Worker;
create table Bonus(
worker_ref_id int,
bonus_amount int,
bonus_date datetime,
foreign key (worker_ref_id)
  references Worker(worker_id)
  on delete cascade
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

## 1-> Now let do a work on this db and do some 50 questions 


