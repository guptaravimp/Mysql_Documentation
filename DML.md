# Data Manipulation language 

## Now lets first create a dataabase 
```
create database revisionsecond;
use revisionsecond;
```
```
create table Customer (
id integer primary key,
cname varchar(255),
Address varchar(255),
gender char(2),
city varchar(255),
Pincode integer
);
```
# 1 Insert 
```
INSERT INTO Customer (id, cname, Address, gender, city, Pincode) VALUES 
(1, 'John Doe', '123 Elm Street', 'M', 'New York', 10001),
(2, 'Jane Smith', '456 Oak Avenue', 'F', 'Los Angeles', 90001),
(3, 'Robert Brown', '789 Pine Lane', 'M', 'Chicago', 60601),
(4, 'Emily Davis', '321 Birch Road', 'F', 'Houston', 77001),
(5, 'Michael Wilson', '654 Cedar Blvd', 'M', 'Phoenix', 85001),
(6, 'Sophia Taylor', '987 Maple Drive', 'F', 'Philadelphia', 19101),
(7, 'William Johnson', '111 Walnut Ave', 'M', 'San Antonio', 78201),
(8, 'Olivia Martinez', '222 Chestnut Circle', 'F', 'San Diego', 92101),
(9, 'James Anderson', '333 Redwood Trail', 'M', 'Dallas', 75201),
(10, 'Isabella Thomas', '444 Cypress Park', 'F', 'San Jose', 95101);
```

# 2 Update 
```
--- update 
update customer set address='Mumbai' where id=1;
select * from customer ;
```

![Screenshot 2025-01-03 141442](https://github.com/user-attachments/assets/5d4918b3-ded2-4db4-981b-e3113fa4744b)

# let we want to update all the row 
## sql provide a security to do this so we have to use some extra safety 
```
set SQL_SAFE_UPDATES=0;
update customer set pincode=111000
```

![Screenshot 2025-01-03 141814](https://github.com/user-attachments/assets/a699c932-e9c0-4dee-9317-24b7c57e7695)

# On delete cascade 
### Imp-> When we are trying to delete some data from parent table then we are unable to delete this because corresponfing nto this there is data in child table so 
### we use (on delete cascase) inside the child table so that parent data deleted after delete and inside the child it will become null
## 1 see this 
```
create table Customer (
id integer primary key,
cname varchar(255),
Address varchar(255),
gender char(2),
city varchar(255),
Pincode integer
);
drop table customer;
INSERT INTO Customer (id, cname, Address, gender, city, Pincode) VALUES 
(1, 'John Doe', '123 Elm Street', 'M', 'New York', 10001),
(2, 'Jane Smith', '456 Oak Avenue', 'F', 'Los Angeles', 90001),
(3, 'Robert Brown', '789 Pine Lane', 'M', 'Chicago', 60601),
(4, 'Emily Davis', '321 Birch Road', 'F', 'Houston', 77001),
(5, 'Michael Wilson', '654 Cedar Blvd', 'M', 'Phoenix', 85001),
(6, 'Sophia Taylor', '987 Maple Drive', 'F', 'Philadelphia', 19101),
(7, 'William Johnson', '111 Walnut Ave', 'M', 'San Antonio', 78201),
(8, 'Olivia Martinez', '222 Chestnut Circle', 'F', 'San Diego', 92101),
(9, 'James Anderson', '333 Redwood Trail', 'M', 'Dallas', 75201),
(10, 'Isabella Thomas', '444 Cypress Park', 'F', 'San Jose', 95101);


create table Order_detail(
order_id integer,
delivery_date date,
cust_id int, foreign key(cust_id) references Customer(id)

);

INSERT INTO Order_detail (order_id, delivery_date, cust_id) VALUES 
(101, '2025-01-05', 1),
(102, '2025-01-06', 2),
(103, '2025-01-07', 3),
(104, '2025-01-08', 4),
(105, '2025-01-09', 5),
(106, '2025-01-10', 6),
(107, '2025-01-11', 7),
(108, '2025-01-12', 8),
(109, '2025-01-13', 9),
(110, '2025-01-14', 10);

```
### Now if we are trying to delete from parent table Customer 
```
--- delete 
delete from customer where id=2;
```
## It give error so wer use on cascade delete in child table like this 
## Correcty way 
```
create table Customer (
id integer primary key,
cname varchar(255),
Address varchar(255),
gender char(2),
city varchar(255),
Pincode integer
);
drop table customer;
INSERT INTO Customer (id, cname, Address, gender, city, Pincode) VALUES 
(1, 'John Doe', '123 Elm Street', 'M', 'New York', 10001),
(2, 'Jane Smith', '456 Oak Avenue', 'F', 'Los Angeles', 90001),
(3, 'Robert Brown', '789 Pine Lane', 'M', 'Chicago', 60601),
(4, 'Emily Davis', '321 Birch Road', 'F', 'Houston', 77001),
(5, 'Michael Wilson', '654 Cedar Blvd', 'M', 'Phoenix', 85001),
(6, 'Sophia Taylor', '987 Maple Drive', 'F', 'Philadelphia', 19101),
(7, 'William Johnson', '111 Walnut Ave', 'M', 'San Antonio', 78201),
(8, 'Olivia Martinez', '222 Chestnut Circle', 'F', 'San Diego', 92101),
(9, 'James Anderson', '333 Redwood Trail', 'M', 'Dallas', 75201),
(10, 'Isabella Thomas', '444 Cypress Park', 'F', 'San Jose', 95101);

--child table 
create table Order_detail(
order_id integer,
delivery_date date,
cust_id int, foreign key(cust_id) references Customer(id)
on delete cascade
);

INSERT INTO Order_detail (order_id, delivery_date, cust_id) VALUES 
(101, '2025-01-05', 1),
(102, '2025-01-06', 2),
(103, '2025-01-07', 3),
(104, '2025-01-08', 4),
(105, '2025-01-09', 5),
(106, '2025-01-10', 6),
(107, '2025-01-11', 7),
(108, '2025-01-12', 8),
(109, '2025-01-13', 9),
(110, '2025-01-14', 10);
```
### Now if we are trying to delete from parent table Customer  successfully delted 
```
--- delete 
delete from customer where id=2;
```

# replace 
## if data is alreday presnt  then it replace the data and 
## if data is not alreday presnt it insert the data 
```
replace into customer (id,city) values(1251,'colony');
select *from customer;
```

![Screenshot 2025-01-03 143709](https://github.com/user-attachments/assets/1b6948f3-fe74-49f7-8aa2-949a3ff67ca8)

