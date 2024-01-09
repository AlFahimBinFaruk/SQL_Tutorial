### SQL Triggers

- You can create trigger for INSERT,DELETE,UPDATE operations.
- create a tigger_test table to monitor changing

```sql
CREATE TABLE trigger_test (
     message VARCHAR(100)
);

```

1. Create trigger

```sql
-- change delimeter from ; to $$
DELIMITER $$

-- create trigger
CREATE
    TRIGGER my_trigger BEFORE INSERT
    ON employee
    FOR EACH ROW BEGIN
        INSERT INTO trigger_test VALUES("new employee added");
    END$$

-- change delimeter to ;
DELIMITER ;
```

- After

```sql
-- create trigger
CREATE
    TRIGGER my_trigger AFTER INSERT
    ON employee
    FOR EACH ROW BEGIN
        INSERT INTO trigger_test VALUES("new employee added");
    END$$
```

2. NEW keyword

- new will have every info of employee that we are inserting.

```
DELIMITER $$
CREATE
    TRIGGER my_trigger BEFORE INSERT
    ON employee
    FOR EACH ROW BEGIN
        INSERT INTO trigger_test VALUES(NEW.first_name);
    END$$
DELIMITER ;
```

3. Conditons

```sql
DELIMITER $$
CREATE
    TRIGGER my_trigger BEFORE INSERT
    ON employee
    FOR EACH ROW BEGIN
         IF NEW.sex = 'M' THEN
               INSERT INTO trigger_test VALUES('added male employee');
         ELSEIF NEW.sex = 'F' THEN
               INSERT INTO trigger_test VALUES('added female');
         ELSE
               INSERT INTO trigger_test VALUES('added other employee');
         END IF;
    END$$
DELIMITER ;
```

4. Delete trigger

```sql
DROP TRIGGER my_trigger;
```
