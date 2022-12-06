### Alter table
* Alter table is used to update the column of a table,add column,drop constraint,add constraint etc.

* Change table column data-type and make it foreign key
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