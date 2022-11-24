### Common data-types
* INT = whole number
* DECIMAL(M,N) = decimal number - exact value
* VARCHAR(l) = string of text length l
* BLOB = Binary large object,stores large data
* DATE = 'YYYY-MM-DD'
* TIMESTAMP = 'YYYY-MM-DD HH:MM:SS' - used for recording actions.

* Note : in most cases data-types are same but depending of different DBMS they can be different.

### Common Commands
1. Create new DB
```
CREATE DATABASE testdb;
```

2. DROP/delete DB,table
```
-- drop db
DROP DATABASE testdb;

-- drop table
DROP TABLE employee;
```

3. Create new table in DB
```
- basic
CREATE TABLE employee (
    emp_id INT PRIMARY KEY,
    full_name VARCHAR(40),
    salary INT,
    birthday DATE,
    super_id INT,
    branch_id INT 
);

- in-details
CREATE TABLE employee (
    emp_id INT PRIMARY KEY AUTO_INCREMENT,
    full_name VARCHAR(40) NOT NULL,
    salary INT,
    birthday DATE,
    super_id INT UNIQUE,
    address VARCHAR(40) DEFAULT 'not-given',
    branch_id INT
);
```

* See db structure(popSQL)
```
DESCRIBE employee;
```

4. Create a new table which has relation with other table
```
CREATE TABLE branch (
    branch_id INT PRIMARY KEY,
    branch_name VARCHAR(40),
    mgr_id INT,
    mgr_start_date DATE,
    FOREIGN KEY(mgr_id) REFERENCES employee(emp_id) ON DELETE SET NULL 
);
```

5. Change table column data-type and make it foreign key
```
-- two different table
ALTER TABLE employee 
ADD FOREIGN KEY(branch_id)
REFERENCES branch(branch_id)
ON DELETE SET NULL;

-- same table
ALTER TABLE employee 
ADD FOREIGN KEY(super_id)
REFERENCES employee(emp_id)
ON DELETE SET NULL;

-- add a new column to the table
ALTER TABLE employee ADD sex VARCHAR(1);
```

6. Create table with 2 primary and foreign key
```
CREATE TABLE works_with (
    emp_id INT,
    client_id INT,
    sales INT,
    PRIMARY KEY(emp_id,client_id),
    FOREIGN KEY(emp_id) REFERENCES employee(emp_id) ON DELETE CASCADE,
    FOREIGN KEY(client_id) REFERENCES client(client_id) ON DELETE CASCADE
);
```

7. Insert new data into table
```
INSERT INTO employee(full_name,salary,birthday,super_id,address,branch_id) VALUES("fahim",333,'2002-12-25',4,"BD",3);
```

8. Update table - column info
```
-- update specefic-row info
UPDATE employee
SET salary = 5000
WHERE emp_id = 1;

-- update all row info of that column
UPDATE employee
SET address = "IN";

```

9. Find/Search Info
```
-- Normal
SELECT * 
FROM employee;

-- Limit
SELECT * 
FROM employee
LIMIT 3;

-- find by order(default ASC)

SELECT * 
FROM employee
ORDER BY branch_id;

SELECT * 
FROM employee
ORDER BY branch_id DESC;

-- Find all employees ordered by sex then name
SELECT *
from employee
ORDER BY sex, name;

-- Find the first and last names of all employees
SELECT first_name, employee.last_name
FROM employee;

-- AS keyword
SELECT first_name AS forename, employee.last_name AS surname
FROM employee;

-- Find all employee's id's and names who were born after 1969
SELECT emp_id, first_name, last_name
FROM employee
WHERE birth_day >= 1970-01-01;

-- Find all employees born between 1970 and 1975
SELECT *
FROM employee
WHERE birth_day BETWEEN '1970-01-01' AND '1975-01-01';

-- Find all employees named Jim, Michael, Johnny or David
SELECT *
FROM employee
WHERE full_name IN ('Jim', 'Michael', 'Johnny', 'David');

```

10. DISTINCT keyword(unique values)
```
-- Find out all the different genders
SELECT DISCINCT sex
FROM employee;
```

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

### Wildcards
1. % = any number of character/word including space.
```
SELECT * 
FROM employee
WHERE full_name LIKE '%im%';
```

2. _ = one character.
```
SELECT * 
FROM employee
WHERE birthday LIKE '____-12%';
```

### Union operator
* union means merging two or more(any number) queries(select query)
* some rules in union operator
  * number of columns in both query have to be same.
  * they have to have similar data types.

```
SELECT full_name AS info_name,emp_id AS info_id
FROM employee
UNION
SELECT branch_name,branch_id
FROM branch;
```
