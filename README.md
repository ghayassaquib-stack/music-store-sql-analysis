# music-store-sql-analysis
This is my first Git Repository
<br>
Author - Saquib Gheyas

-- 1. Top 5 Customers by Spend
SELECT c.first_name, c.last_name, SUM(i.total) AS lifetime_value
FROM customer c
JOIN invoice i ON c.customer_id = i.customer_id
GROUP BY c.customer_id
ORDER BY lifetime_value DESC
LIMIT 5;

-- 2. Most Popular Genre
SELECT g.name AS genre, COUNT(il.invoice_line_id) AS sales
FROM invoice_line il
JOIN track t ON il.track_id = t.track_id
JOIN genre g ON t.genre_id = g.genre_id
GROUP BY g.genre_id
ORDER BY sales DESC
LIMIT 1;

-- 3. Top Employee by Supported Sales
SELECT e.first_name, e.last_name, SUM(i.total) AS supported_sales
FROM employee e
JOIN customer c ON e.employee_id = c.support_rep_id
JOIN invoice i ON c.customer_id = i.customer_id
GROUP BY e.employee_id
ORDER BY supported_sales DESC
LIMIT 1;

