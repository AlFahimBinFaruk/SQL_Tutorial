### Alter table

- There are two ways to update a table structure

  - while creating it
  - using alter

- Alter table is used to update the column of a table,add column,drop constraint,add constraint etc.

- custom way to add constraint

```
ALTER TABLE person
ADD CONSTRAINT unique_email UNIQUE(email);
```

- normal way to add constraint

```
ALTER TABLE person
ADD UNIQUE(email);
```

- Change table column data-type and make it foreign key

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

- Working with constraints

```
-- Drop constraint
ALTER TABLE car
DROP CONSTRAINT "car_pkey";

-- Adding it again
ALTER TABLE car
ADD PRIMARY KEY(id);

```

- check constraint
```
ALTER TABLE person 
ADD CONSTRAINT unique_gender CHECK(gender = 'male' OR gender = 'female');
```

- Alter sequence
```
ALTER SEQUENCE car_id_seq RESTART WITH 10;
```