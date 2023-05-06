# SQL-Project
Project overview:- This project is based on Store database and i have been executed it with some deep queries for enhance my sql skill to jump into Data Analyst Role.
                   Become a Data Analyst not a only goal of mine .  I want to achieve ML, AI, NLP , DL and many more. Its just a beginning.

Data Model:- I used here Customer details table, employee table, any some of more too and make Relationships between them to execute my project properly,

SQL CODE:- 

WITH best_selling_artist AS (
	SELECT artist.artist_id AS artist_id, artist.name AS artist_name, SUM(invoice_line.unit_price*invoice_line.quantity) AS total_sales
	FROM invoice_line
	JOIN track ON track.track_id = invoice_line.track_id
	JOIN album ON album.album_id = track.album_id
	JOIN artist ON artist.artist_id = album.artist_id
	GROUP BY 1
	ORDER BY 3 DESC
	LIMIT 1
)
SELECT c.customer_id, c.first_name, c.last_name, bsa.artist_name, SUM(il.unit_price*il.quantity) AS amount_spent
FROM invoice i
JOIN customer c ON c.customer_id = i.customer_id
JOIN invoice_line il ON il.invoice_id = i.invoice_id
JOIN track t ON t.track_id = il.track_id
JOIN album alb ON alb.album_id = t.album_id
JOIN best_selling_artist bsa ON bsa.artist_id = alb.artist_id
GROUP BY 1,2,3,4
ORDER BY 5 DESC;

Tools and Technologies:- PostgreSQL, Pgadmin4, windows 10

Project Outcome:- I AM ABLE TO SOLVE THIS TYPE OF QUERIES BY THIS PROJECT.

Q1. We want to find out the most popular music Genre for each country. We determine the 
most popular genre as the genre with the highest amount of purchases. Write a query 
that returns each country along with the top Genre. For countries where the maximum 
number of purchases is shared return all Genres

 Q2. Return all the track names that have a song length longer than the average song length. 
Return the Name and Milliseconds for each track. Order by the song length with the 
longest songs listed first

Q3. Which countries have the most Invoices?

Q4. Who is the best customer? The customer who has spent the most money will be 
declared the best customer. Write a query that returns the person who has spent the 
most money


THANK YOU!
