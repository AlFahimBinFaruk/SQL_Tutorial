### Arithmetic operators in SQL.
* +,-,*,/,% etc.
  
```sql
SELECT name,price,ROUND(price * .10) AS discount, ROUND(price-(price*.10),2) AS new_price FROM car;
```
