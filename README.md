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







