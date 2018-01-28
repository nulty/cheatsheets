# <a name="top"></a>MySQL



### Data Definition Language 
#### Inspect Database
```sql
SHOW DATABASES;
```
```sql
SHOW FIELDS FROM tablename;
```
```sql
USE DATABASE database;
```

#### Manage Database

```sql
CREATE DATABASE database;
```

```sql
DROP DATABASE database;
```

---
#### Manage Tables
##### Create Table
```sql
CREATE TABLE people (
  id int(4) AUTO_INCREMENT, 
  first_name varchar(20) NOT NULL,
  salary int(20) NOT NULL DEFAULT=2,
  PRIMARY KEY(id) 
);
```

##### Drop Table

```sql
DROP TABLE people;
```


##### Truncate Table

```sql
TRUNCATE TABLE people;
```

##### Add column


```sql
ALTER TABLE people ADD last_name varchar(20);
``` 

##### Change column type / name

```sql
ALTER TABLE people CHANGE COLUMN first_name forname varchar(30);
```



[<< Top](#top)

---
### Indexes 


##### Create Index
```sql
CREATE INDEX idx_first_name ON people (first_name);
```

##### Drop Index
```sql
ALTER TABLE people DROP INDEX idx_first_name;
```

[<< Top](#top)

---
## Data Manipulation Language

##### Insert into
```sql
INSERT INTO people (first_name) VALUES ('Iain');
```

##### Delete
```sql
DELETE FROM people WHERE salary > 15000;
```

##### Update
```sql
UPDATE people SET salary = 999999 WHERE name = 'Iain';
```

##### Select
```sql
SELECT first_name FROM people;
```

##### Count

```sql
SELECT COUNT(*) FROM first_name;
```

```sql
SELECT COUNT(DISTINCT first_name) FROM people;
```

##### Average Sum

```sql
SELECT AVG(salary) FROM people;
```

```sql
SELECT SUM(salary) FROM people;
``` 

[<< Top](#top)

---
#### Where

##### Equal
```sql
SELECT first_name FROM people WHERE first_name='Iain';
```


#### Not equal
```sql
SELECT first_name FROM people WHERE first_name!='Iain';
```

```sql
SELECT first_name FROM people WHERE first_name<>'Iain';
```

#### Like
```sql
SELECT first_name FROM people WHERE first_name LIKE '%ain';
```
```sql
SELECT first_name FROM people WHERE first_name LIKE 'Iai%';
```
```sql
SELECT first_name FROM people WHERE first_name LIKE '%ai%';
```

[<< Top](#top)

---
#### Order

##### Descending

```sql
SELECT first_name from people order by first_name desc;
```

##### Ascending
```sql
SELECT first_name FROM people ORDER BY first_name asc;
```

##### Limiting results

```sql 
SELECT first_name FROM people ORDER BY first_name LIMIT 1;
```


##### Delete rows
```sql
DELETE FROM people WHERE first_name = 'Iain';
```


[<< Top](#top)

---

#### Views

##### Create View

```sql
CREATE VIEW avg_salary_by_name AS SELECT first_name, AVG(salary) AS avg_salary from people GROUP BY first_name;
```

##### Drop View

```sql
DROP VIEW avg_salary;
```

[<< Top](#top)

---

#### Join

##### Inner Join

```sql
SELECT first_name, pet_name FROM people INNER JOIN pets ON pets.person_id = people.id;
```

##### Left Join

> Select the records from the left table (people) that have joined records on the right table
> And if people don't have pets, then still select them with null values in the pets_name column.

```sql
SELECT first_name, pet_name FROM people LEFT JOIN pets ON pets.person_id = people.id;
```

##### Right Join
> Select the records from the left table (people) that have joined records on the right table
> And if there are pets that don't have people, then still select them with null values
> in the first_name column.


```sql
SELECT first_name, pet_name FROM people LEFT JOIN pets ON pets.person_id = people.id;
```

##### Full Join

*Not possible in MySQL, see UNION*
 
#### Union (Full Outer Join)
> To achieve a FULL OUTER JOIN in MySQL we need to UNION a LEFT JOIN and a RIGHT JOIN
> using the same target table and same target columns.

```sql
SELECT * FROM people LEFT JOIN animals ON people.id = animals.owner_id
UNION
SELECT * from people RIGHT JOIN animals ON people.id = animals.owner_id;
```

[<< Top](#top)











 
