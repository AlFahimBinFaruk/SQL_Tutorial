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

-- Round
SELECT ROUND(AVG(salary))
FROM employee;

-- Round
SELECT ROUND(AVG(salary),2)
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
SELECT sex,COUNT(sex)
FROM employee
GROUP BY sex;

-- ex 02
SELECT country,COUNT(country) 
FROM person 
GROUP BY country;
```

5. Having keyword - adds extra filter to group by
```
SELECT country,COUNT(country) 
FROM person 
GROUP BY country 
HAVING COUNT(country) > 5;
```

6. Find min

```
SELECT MIN(salary)
FROM employee;
```

7. Find max

```
SELECT MAX(salary)
FROM employee;
```

8. Round keyword
```
SELECT ROUND(MAX(salary))
FROM employee;
```

9. STATISTIC keyword
```
SELECT email AS Email
FROM (
    SELECT email,COUNT(email) AS emailCount
    FROM person
    GROUP BY email
) AS STATISTIC
WHERE emailCount > 1;
```