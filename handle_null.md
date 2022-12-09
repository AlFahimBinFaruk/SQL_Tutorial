### How to handle NULL and Division by 0

1. Coalesce keyword - to handle null value in DB table.
* if a value is null then default value will be provided.
```
SELECT COALESCE(email,'Email not provided') FROM person;
```

2. NULLIF - handle division by 0
* if the first arg and the second arg is same then it will return null otherwise it will return first arg.
```
-- this gives error
SELECT 10 / 0

-- this returns null
SELECT 10 / NULLIF(1,0)
```