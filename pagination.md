### For pagination
1. Limit
```
SELECT * FROM person 
LIMIT 5;
```

2. Offset
* offset means how many rows we will skip from the start.
```
-- select from 8th row.
SELECT * FROM person 
OFFSET 7 LIMIT 5;
```

3. Fetch - does the same as limit but considered good practice
```
SELECT * FROM person 
OFFSET 7 FETCH FIRST 5 ROW ONLY;
```