### Join operator

- join is use to query between two or more related column in tables, the tables dosen't need to have ralation among them.

1. Normal/inner join.
- branch and employee are two different table with a relation.
```sql
SELECT *
FROM employee
JOIN branch;


SELECT employee.full_name,branch.branch_name
FROM employee
JOIN branch
ON employee.emp_id = branch.mgr_id;
```

2. Left join

- left join will get every full_name of left table(employee) wheather it match the conditon or not, but it case of right table(branch) only the info that match conditon will be shown.

```sql
-- employee(after from) = left,branch = right
SELECT employee.full_name,branch.branch_name
FROM employee
LEFT JOIN branch
ON employee.emp_id = branch.mgr_id;
```

3. Right join
- opposite of left join

```sql
SELECT employee.full_name,branch.branch_name
FROM employee
RIGHT JOIN branch
ON employee.emp_id = branch.mgr_id;
```

4. FULL OUTER JOIN =  Returns all records from both tables
```sql
SELECT j_name,emp_id,p_name
FROM mydb.junior_data
CROSS JOIN mydb.emp_data
ON junior_data.emp_id=emp_data.p_id;
```
