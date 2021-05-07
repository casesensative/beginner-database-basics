-- Table - person
-- Instructions
-- Create a table called person that records a person's id, name, age, height ( in cm ), city, favorite_color.
create table person (
	id serial primary key,
  name VARCHAR(50),
  age INT,
  height INT,
  city VARCHAR(50),
  favorite_color VARCHAR(50)
);
-- id should be an auto-incrementing id/primary key - Use type: SERIAL
-- Add 5 different people into the person database.
insert into person
(name, age, height, city, favorite_color)
values
('Victor', 36, 72, 'Tampa', 'blue'),
('Kyle', 33, 68, 'Austin', 'violet'),
('Easton', 3, 38, 'Tampa', 'red'),
('Debbie', 67, 59, 'Tallahassee', 'green'),
('Mark', 56, 66, 'Tallahassee', 'yellow');
-- Remember to not include the person_id because it should auto-increment.
-- List all the people in the person table by height from tallest to shortest.
select * from person
order by height desc;

-- List all the people in the person table by height from shortest to tallest.
select * from person
order by height asc;
-- List all the people in the person table by age from oldest to youngest.
select * from person
order by age desc;
-- List all the people in the person table older than age 20.
select * from person
where age > 20;
-- List all the people in the person table that are exactly 18.
select * from person
where age = 18;
-- List all the people in the person table that are less than 20 and older than 30.
select * from person
where age < 20 and age > 30;
-- List all the people in the person table that are not 27 (Use not equals).
select * from person
where not age = 27;
-- List all the people in the person table where their favorite color is not red.
select * from person
where favorite_color != 'red';
-- List all the people in the person table where their favorite color is not red and is not blue.
select * from person
where favorite_color != 'red' and favorite_color != 'blue';
-- List all the people in the person table where their favorite color is orange or green.
select * from person
where favorite_color in ('orange', 'green');
-- List all the people in the person table where their favorite color is orange, green or blue (use IN).
select * from person
where favorite_color in ('orange', 'green', 'blue');
-- List all the people in the person table where their favorite color is yellow or purple (use IN).
select * from person
where favorite_color in ('yellow', 'purple');


-- Instructions
-- Create a table called orders that records: order_id, person_id, product_name, product_price, quantity.
create table orders (
	order_id serial primary key,
  person_id int,
  product_name varchar(100),
  product_price decimal,
  quantity int
);
-- Add 5 orders to the orders table.
insert into orders
(person_id, product_name, product_price, quantity)
values
(2, 'tacos', 3.50, 3),
(2, 'margaritas', 5.75, 1),
(4, 'pad thai', 9.98, 1),
(4, 'thai tea', 4.65, 1),
(3, 'kids meal', 5.25, 1);
-- Make orders for at least two different people.
-- person_id should be different for different people.
-- Select all the records from the orders table.
select * orders;
-- Calculate the total number of products ordered.
select sum(quantity) from orders;
-- Calculate the total order price.
select sum(product_price) from orders;
-- Calculate the total order price by a single person_id.
select sum(product_price) from orders
where person_id = 2;


-- Instructions
-- Add 3 new artists to the artist table. ( It's already created )
insert into artist
(name)
values
('James Taylor'),
('Jack Johnson'),
('Jim Croce');
-- Select 10 artists in reverse alphabetical order.
select * from artist
order by name asc
limit 10;
-- Select 5 artists in alphabetical order.
select * from artist
order by name desc
limit 5;
-- Select all artists that start with the word 'Black'.
select * from artist
where name like 'Black%';
-- Select all artists that contain the word 'Black'.
select * from artist
where name like '%Black%';

-- Instructions
-- List all employee first and last names only that live in Calgary.
select (first_name, last_name) from employee
where city = 'Calgary';
-- Find the birthdate for the youngest employee.
select * from employee
order by birth_date asc
limit 1;
-- Find the birthdate for the oldest employee.
-- Find everyone that reports to Nancy Edwards (Use the ReportsTo column).
-- You will need to query the employee table to find the Id for Nancy Edwards
-- Count how many people live in Lethbridge.

-- Instructions
-- List all employee first and last names only that live in Calgary.
select (first_name, last_name) from employee
where city = 'Calgary';
-- Find the birthdate for the youngest employee.
select birth_date from employee
order by birth_date desc
limit 1;
-- Find the birthdate for the oldest employee.
select birth_date from employee
order by birth_date asc
limit 1;
-- Find everyone that reports to Nancy Edwards (Use the ReportsTo column).
select employee_id from employee
where first_name = 'Nancy' and last_name = 'Edwards';

select * from employee
where reports_to = 2;
-- You will need to query the employee table to find the Id for Nancy Edwards
-- Count how many people live in Lethbridge.
select count(*) from employee
where city = 'Lethbridge';

-- Instructions
-- Count how many orders were made from the USA.
select count(*) from invoice
where billing_country = 'USA';
-- Find the largest order total amount.
select total from invoice
order by total desc
limit 1;
-- Find the smallest order total amount.
select total from invoice
order by total asc
limit 1;
-- Find all orders bigger than $5.
select * from invoice
where total > 5;
-- Count how many orders were smaller than $5.
select count(*) from invoice
where total < 5;
-- Count how many orders were in CA, TX, or AZ (use IN).
select count(*) from invoice
where billing_state in ('CA', 'TX', 'AZ');
-- Get the average total of the orders.
select avg(total) from invoice;
-- Get the total sum of the orders.
select sum(total) from invoice;