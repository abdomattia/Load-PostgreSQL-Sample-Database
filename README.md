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






