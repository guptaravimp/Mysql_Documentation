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



