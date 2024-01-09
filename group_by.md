```sql
--- will work
SELECT job,j_id
FROM mydb.junior_data
GROUP BY j_id;

--- wont work
SELECT job,j_id
FROM mydb.junior_data
GROUP BY job;

---will work
SELECT job
FROM mydb.junior_data
GROUP BY job;
```
