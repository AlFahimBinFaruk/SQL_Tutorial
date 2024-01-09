1. With View
* if you execure same query multiple times make it a view so you don't have to write it all the time.
```sql
CREATE VIEW mydb.salView AS 
SELECT * FROM mydb.junior_data WHERE salary=45;

SELECT * FROM mydb.salView;
```

2. With Index = to increase search speed.
```sql
CREATE INDEX customer_lastname_index ON customers (contactLastName);

---This index will speed up queries like:
SELECT * FROM customers WHERE contactLastName="Lee";
```
