### Date and Time.

- Basic commands

```
-- gives all
SELECT NOW();

-- gives date
SELECT NOW()::DATE;

-- gives time
SELECT NOW()::TIME;

```

- Interval keyword - to abstrack a amount of time from present.

```
SELECT NOW() - INTERVAL '1 YEAR';

SELECT NOW() - INTERVAL '1 MONTHS/MONTH';

SELECT NOW() - INTERVAL '1 DAY/DAYS';

SELECT (NOW() - INTERVAL '1 YEAR')::DATE;
```

- Extract function

```
SELECT EXTRACT(YEAR FROM NOW());

SELECT EXTRACT(MONTH FROM NOW());

SELECT EXTRACT(DAY FROM NOW());

-- DOW = day of week (sat,sun,mon)
SELECT EXTRACT(DOW FROM NOW());

SELECT EXTRACT(CENTURY FROM NOW());
```

- Age function - to calculate age.

```
SELECT email,AGE(NOW()::DATE,date_of_birth) AS age FROM person;
```
