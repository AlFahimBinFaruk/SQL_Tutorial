### For pagination
1. Limit
```sql
SELECT * FROM person 
LIMIT 5;
```

2. Offset
* offset means how many rows we will skip from the start.
```sql
-- 3 is offset,2 is limit
SELECT * FROM mydb.junior_data 
LIMIT 3,2;

SELECT * FROM mydb.junior_data
LIMIT 2 OFFSET 3;
```

3. Fetch - does the same as limit but considered good practice
```
SELECT * FROM person 
OFFSET 7 FETCH FIRST 5 ROW ONLY;
```
