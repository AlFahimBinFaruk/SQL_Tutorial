### Join operator

- join is use to query between two or more related column in tables, the tables dosen't need to have ralation among them.

1. Normal/inner join.
* branch and employee are two different table with a relation.
```
SELECT *
FROM employee
JOIN branch;


SELECT employee.full_name,branch.branch_name
FROM employee
JOIN branch
ON employee.emp_id = branch.mgr_id;
```

2. Left join

- left join will get every full_name weather it match the condition or not.

```
-- employee(after from) = left,branch = right
SELECT employee.full_name,branch.branch_name
FROM employee
LEFT JOIN branch
ON employee.emp_id = branch.mgr_id;
```

3. Right join

```
SELECT employee.full_name,branch.branch_name
FROM employee
RIGHT JOIN branch
ON employee.emp_id = branch.mgr_id;
```
