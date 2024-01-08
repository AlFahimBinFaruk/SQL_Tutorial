### Common data-types

- INT = whole number
- DECIMAL(M,N) = decimal number - exact value
- VARCHAR(l) = string of text length l
- BLOB = Binary large object,stores large data
- DATE = 'YYYY-MM-DD'
- TIMESTAMP = 'YYYY-MM-DD HH:MM:SS' - used for recording actions.

- Note : in most cases data-types are same but depending of different DBMS they can be different.

### Common Commands

1. Create new DB

```sql
CREATE DATABASE testdb;
```

2. DROP/delete DB,table


```sql
-- drop db
DROP DATABASE testdb;

-- drop table
DROP TABLE employee;

```

3. Create new table in DB

```sql
CREATE TABLE table_name (
    (column name) (data type) (constraints if any)
)

CREATE TABLE db_name.table_name (
    (column name) (data type) (constraints if any)
)
```


```sql
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
    salary INT CHECK(salary > 0),
    birthday DATE,
    super_id INT UNIQUE,
    address VARCHAR(40) DEFAULT 'not-given',
    branch_id INT
);
```

- See db structure(popSQL)

```sql
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


5. Create table with 2 primary and foreign key

```
-- MYSQL
CREATE TABLE works_with (
    emp_id INT,
    client_id INT,
    sales INT,
    PRIMARY KEY(emp_id,client_id),
    FOREIGN KEY(emp_id) REFERENCES employee(emp_id) ON DELETE CASCADE,
    FOREIGN KEY(client_id) REFERENCES client(client_id) ON DELETE CASCADE
);

-- POSTGRE sql = postgresql add foreign key itself.
CREATE TABLE works_with (
    emp_id INT,
    client_id INT,
    sales INT,
    PRIMARY KEY(emp_id,client_id),
    emp_id REFERENCES employee(emp_id) ON DELETE CASCADE,
    client_id REFERENCES client(client_id) ON DELETE CASCADE
);
```

6. Insert new data into table

```sql
INSERT INTO employee(full_name,salary,birthday,super_id,address,branch_id) 
VALUES("fahim",333,'2002-12-25',4,"BD",3);
```

7. Update table - column info

```sql
-- update specefic-row info
UPDATE employee
SET name="xyx",salary = 5000
WHERE emp_id = 1;

-- update all row info of that column
UPDATE employee
SET address = "IN";

```

8. Find/Search Info

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


-- Find all employee's id's and names who were born after 1969 and female
SELECT emp_id, first_name, last_name
FROM employee
WHERE birth_day >= 1970-01-01
AND sex = 'F';


-- Find all employee's id's and names who were born after 1979 or male
SELECT emp_id, first_name, last_name
FROM employee
WHERE birth_day >= 1979-01-01
OR sex = 'M';

-- Find all employees born between 1970 and 1975
SELECT *
FROM employee
WHERE birth_day BETWEEN '1970-01-01' AND '1975-01-01';

-- Find all employees named Jim, Michael, Johnny or David
SELECT *
FROM employee
WHERE full_name IN ('Jim', 'Michael', 'Johnny', 'David');

-- NOT IN
SELECT *
FROM employee
WHERE full_name NOT IN ('Jim', 'Michael', 'Johnny', 'David');

-- != in sql is <>
SELECT * FROM person 
WHERE gender <> 'Male' 
and gender <> 'Female';

```

9. DISTINCT keyword(unique values)

```
-- Find out all the different genders
SELECT DISCINCT sex
FROM employee;
```

10. Delete records
```
-- deletes everything
DELETE FROM person;

-- deletes which match the condition
DELETE FROM person 
WHERE id = 3;
```

11. Between keyword - select within a range.
```
SELECT * FROM person 
WHERE date_of_birth 
BETWEEN '2021-08-12' AND '2022-05-26';
```
