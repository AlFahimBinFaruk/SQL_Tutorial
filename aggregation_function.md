### Functions/Aggregation function

1. count total row

```
-- Find the number of employees
SELECT COUNT(super_id)
FROM employee;
```

2. Find avg of a column items

```
-- Find the average of all employee's salaries
SELECT AVG(salary)
FROM employee;
```

3. Find sum/total of a column items

```
-- Find the sum of all employee's salaries
SELECT SUM(salary)
FROM employee;
```

4. GROUP By

```
-- Find out how many males and females there are
SELECT COUNT(sex),sex
FROM employee
GROUP BY sex;
```

5. Find min

```
SELECT MIN(salary)
FROM employee;
```

6. Find max

```
SELECT MAX(salary)
FROM employee;
```
