### Functions/Aggregation function

1. count total row of a specific col. If some col is NULL it wont be counted.

```sql
-- Find the number of employees
SELECT COUNT(super_id)
FROM employee;
```

2. Find avg of a column items

```sql
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

```sql
-- Find the sum of all employee's salaries
SELECT SUM(salary)
FROM employee;
```

4. GROUP By

```sql
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
```sql
SELECT country,COUNT(country) 
FROM person 
GROUP BY country 
HAVING COUNT(country) > 5;
```

6. Find min

```sql
SELECT MIN(salary)
FROM employee;
```

7. Find max

```sql
SELECT MAX(salary)
FROM employee;
```

8. Round keyword
```sql
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
