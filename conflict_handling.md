### Conflict handling
* what to do if there is a conflict.
* the column inside conflict have to be a UNIQUE constrant.


- Do nothing
```
-- if there is a confilict in id(duplicate id) then we will do nothing means we will not show any error and we will not also insert it.
INSERT INTO employee(id,full_name,salary,birthday,super_id,address,branch_id) 
VALUES(33,"fahim",333,'2002-12-25',4,"BD",3)
ON CONFLICT(id) DO NOTHING;
```

- Upsert = update and insert

```
-- if there is a conflict on id then we will update the full name and address.
INSERT INTO employee(id,full_name,salary,birthday,super_id,address,branch_id) 
VALUES(33,"fahim",333,'2002-12-25',4,"BD",3)
ON CONFLICT(id) DO UPDATE 
SET full_name = EXCLUDED.full_name,
address = EXCLUDED.address;
```
