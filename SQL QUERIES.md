**SQL QUERIES:-**



**A.Use SELECT, WHERE, ORDER BY, GROUP BY:**



*SELECT customer\_id, customer\_name, city*

*FROM customers*

*WHERE city = 'New York'*

*ORDER BY customer\_name ASC;*

<b>-----------</b>

*SELECT customer\_id, SUM(order\_amount) AS total\_spent*

*FROM orders*

*GROUP BY customer\_id*

*ORDER BY total\_spent DESC;*



<b>B.Use JOINS (INNER, LEFT, RIGHT):</b>



<b>INNER JOIN-</b>

*SELECT c.customer\_name, o.order\_id, o.order\_amount*

*FROM customers c*

*INNER JOIN orders o*

*ON c.customer\_id = o.customer\_id;*


<b>LEFT JOIN-</b>

*SELECT c.customer\_name, o.order\_id*

*FROM customers c*

*LEFT JOIN orders o*

*ON c.customer\_id = o.customer\_id;*



<b>RIGHT JOIN-</b>

*SELECT c.customer\_name, o.order\_id*

*FROM customers c*

*RIGHT JOIN orders o*

*ON c.customer\_id = o.customer\_id;*



<b>C.Subqueries:</b>

*SELECT customer\_name*

*FROM customers*

*WHERE customer\_id IN (*

    *SELECT customer\_id*

    *FROM orders*

    *GROUP BY customer\_id*

    *HAVING SUM(order\_amount) > (*

        *SELECT AVG(order\_amount) FROM orders*

    *)*

*);*



<b>D.Aggregate functions (SUM, AVG):</b>

*SELECT AVG(order\_amount) AS avg\_order\_value*

*FROM orders;*



<b>E.View:</b>

*CREATE VIEW customer\_order\_summary AS*

*SELECT* 

    *c.customer\_id,*

    *c.customer\_name,*

    *COUNT(o.order\_id) AS total\_orders,*

    *SUM(o.order\_amount) AS total\_spent,*

    *AVG(o.order\_amount) AS avg\_order\_value*

*FROM customers c*

*LEFT JOIN orders o*

*ON c.customer\_id = o.customer\_id*

*GROUP BY c.customer\_id, c.customer\_name;*

*--------------*

*SELECT \* FROM customer\_order\_summary;*



<b>F.Query Optimization:</b>

*CREATE INDEX idx\_orders\_customer\_id*

*ON orders(customer\_id);*



*CREATE INDEX idx\_customers\_city*

*ON customers(city);*





