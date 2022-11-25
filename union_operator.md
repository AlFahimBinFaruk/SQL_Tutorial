### Union operator

- union means merging two or more(any number) queries(select query)
- some rules in union operator
  - number of columns in both query have to be same.
  - they have to have similar data types.

```
SELECT full_name AS info_name,emp_id AS info_id
FROM employee
UNION
SELECT branch_name,branch_id
FROM branch;
```
