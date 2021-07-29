# Load-PostgreSQL-Sample-Database
dvdrental

SELECT * FROM actor;

SELECT actor_id ,first_name FROM actor;

SELECT first_name,last_name,email FROM customer;

SELECT DISTINCT release_year FROM film;

SELECT email FROM customer
WHERE first_name='Nancy' AND last_name='Thomas';

SELECT description FROM film
WHERE title='Outlaw Hanky';

SELECT COUNT(DISTINCT amount) FROM payment;

SELECT * FROM customer
LIMIT 1;

SELECT first_name,last_name FROM customer
ORDER BY first_name ASC ,
last_name ASC;

SELECT customer_id,amount FROM payment
ORDER BY amount DESC
LIMIT 10;

SELECT customer_id,amount FROM payment
WHERE amount BETWEEN 7 AND 8;

SELECT customer_id,amount FROM payment
WHERE payment_date  BETWEEN '2007-02-7' AND '2007-02-15';

SELECT customer_id,amount FROM payment
WHERE amount NOT BETWEEN 7 AND 8;

SELECT customer_id,amount FROM payment
WHERE payment_date NOT BETWEEN '2007-02-7' AND '2007-02-15';

SELECT customer_id,return_date FROM rental
WHERE staff_id IN (1,2)
ORDER BY return_date ASC;

SELECT first_name ,email,customer_id FROM customer
WHERE customer_id IN (1,2,3,4);

SELECT first_name FROM customer
WHERE first_name LIKE 'Jan%';

SELECT first_name FROM customer
WHERE first_name LIKE '%er%';

SELECT first_name FROM customer
WHERE first_name LIKE '_er%';

SELECT first_name FROM customer
WHERE first_name ILIKE 'Jan%';

SELECT MIN(amount) FROM payment;
SELECT amount FROM payment 
ORDER BY amount ASC;

SELECT COUNT(amount) FROM payment 
WHERE amount =0;

SELECT AVG(amount) FROM payment;

SELECT ROUND(AVG(amount),2) FROM payment;

SELECT SUM(amount) FROM payment;

SELECT ROUND(SUM(amount),3) FROM payment;

SELECT MAX(amount) FROM payment;

GROUP BY

SELECT customer_id FROM payment
GROUP BY customer_id;

SELECT customer_id,SUM(amount) FROM payment
GROUP BY customer_id
ORDER BY SUM(amount) DESC;

SELECT * FROM film;
SELECT rating FROM film
GROUP BY rating;

SELECT rating ,COUNT(rating) FROM film 
GROUP BY rating 
ORDER BY COUNT(rating) DESC;

SELECT * FROM payment ;

SELECT staff_id , COUNT(amount) FROM payment
GROUP BY staff_id;

SELECT staff_id , SUM(amount) FROM payment
GROUP BY staff_id;

SELECT staff_id , SUM(amount), COUNT(amount) 
FROM payment 
GROUP BY staff_id;

SELECT * FROM payment;

SELECT customer_id, SUM(amount) FROM payment
GROUP BY customer_id 
ORDER BY SUM(amount) DESC
LIMIT 10;


Having 

SELECT* FROM customer;

SELECT store_id ,COUNT(customer_id) FROM customer
GROUP BY store_id
HAVING COUNT(customer_id)>300;

SELECT * FROM payment;

SELECT customer_id , SUM(amount) FROM payment
GROUP BY customer_id 
HAVING SUM(amount)>200;

SELECT * FROM film;

SELECT rating ,AVG(rental_rate) FROM film 
GROUP BY rating;

SELECT rating , AVG(rental_rate) FROM film 
WHERE rating IN ('R','PG','G')
GROUP BY rating 
HAVING AVG(rental_rate)>3;

SELECT * FROM payment;

SELECT customer_id , COUNT(amount) FROM payment 
GROUP BY customer_id
HAVING COUNT(amount)>=40;

JOIN

SELECT * FROM customer;
SELECT * FROM payment;

SELECT customer.customer_id,first_name,last_name,email,amount,payment_date
FROM customer
INNER JOIN payment ON customer.customer_id=payment.customer_id
ORDER BY customer.customer_id ASC;

SELECT * FROM inventory;
SELECT * FROM film;

SELECT store_id , title FROM film 
INNER JOIN inventory ON film.film_id=inventory.film_id
WHERE store_id =1;

SELECT title,COUNT(title) FROM film 
INNER JOIN inventory ON film.film_id=inventory.film_id
WHERE store_id =1
GROUP BY title
ORDER BY COUNT(title)DESC;

SELECT * FROM language;
SELECT * FROM film ; 

SELECT name AS movie_language, title 
FROM language 
INNER JOIN film ON language.language_id=film.language_id;

SELECT * FROM film ;

SELECT * FROM inventory;

SELECT film.film_id, title,inventory_id FROM film
LEFT OUTER JOIN inventory ON film.film_id=inventory.film_id
WHERE inventory_id IS NULL ;

SELECT * FROM payment;
SELECT payment_date FROM payment;
SELECT extract(day from payment_date) FROM payment; 

SELECT SUM(amount), extract(month from payment_date)
FROM payment 
GROUP BY extract(month from payment_date)
ORDER BY extract(month from payment_date);

Mathematical Functions

SELECT payment_id*customer_id AS new_id FROM payment;


SELECT * FROM customer;

SELECT first_name || last_name FROM customer;

SELECT first_name || ' ' || last_name AS full_name FROM customer;

SELECT* FROM customer;
SELECT first_name,char_length(first_name) FROM customer;

SELECT UPPER(first_name) FROM customer;
SELECT LOWER(first_name) FROM customer;

SUBQUERY 

SELECT * FROM film;
SELECT AVG(rental_rate) FROM film;
SELECT title ,rental_rate FROM film
WHERE rental_rate>2.98;

SELECT title , rental_rate FROM film
WHERE rental_rate > (SELECT AVG(rental_rate) FROM film);

Self Join (A very popular question)

Question: What is a Self Join?Answer: A self-join is simply a normal SQL join that joins one table to itself. Joining a table to itself can be useful when you want to compare values in a column to other values in the same column.

Question: Is Self Join Inner Join or Outer Join?Answer: A self-join can be an inner join or an outer join or even a cross join. A table is joined to itself based upon a column that have duplicate data in different rows.

Question: What is a practical use of the Self Join in the real world?Answer: The best example of self join in the real world is when we have a table with Employee data and each row contains information about employee and his/her manager. You can use self join in this scenario and retrieve relevant information. 


SELECT * FROM customer;

SELECT a.customer_id, a.first_name,a.last_name,b.customer_id, b.first_name,b.last_name
FROM customer AS a,customer AS b
WHERE a.first_name=b.last_name;

SELECT a.first_name,a.last_name,b.first_name,b.last_name
FROM customer AS a
JOIN customer AS b 
ON a.first_name=b.last_name;

CREATE TABLE 

CREATE TABLE customerd(
customer_id serial PRIMARY KEY NOT NULL ,
first_name varchar(55) NOT NULL ,
last_name varchar(55) NOT NULL ,
email varchar(250) UNIQUE NOT NULL , 
sign_up_date timestamp ,
minutes int 

);

SELECT * FROM customerd;

