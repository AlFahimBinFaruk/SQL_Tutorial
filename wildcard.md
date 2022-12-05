### Wildcards

1. % = any number of character/word including space.

```
SELECT *
FROM employee
WHERE full_name LIKE '%im%';
```

2. \_ = one character.

```
SELECT *
FROM employee
WHERE birthday LIKE '____-12%';
```

* Note = LIKE is case sensitive(p and P are different) to avoid it use ILIKE keyword.