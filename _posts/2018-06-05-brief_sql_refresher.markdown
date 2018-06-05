---
layout: post
title:      "Brief SQL Refresher"
date:       2018-06-05 21:12:40 +0000
permalink:  brief_sql_refresher
---


I wanted to do a brief overview on SQL since I have not utilized it in a while.

SQL (Structured Query Language) is a language for managing data in a relational database. In a relational database, each table contains one or more data categories in columns. Each table has a unique primary key, which identifies the information in a table. The relationship between tables can be set with foreign keys. 

#### Three Operators Used to Manipulate Database Schema

`CREATE TABLE` is used to create table in the database. It consists of the names of the columns and the data type the column will be accepting.

```
CREATE TABLE movies (
    id INTEGER PRIMARY KEY, 
    name TEXT
);
```

`ALTER TABLE` is used to modify the table.

```
ALTER TABLE movies 
    ADD rating INTEGER
    AFTER name;
```

`DROP TABLE` is used to delete a table.

#### Four Main Data Manipulation

`SELECT`
- Retrieve values from one or more rows

If we want to select all the names from the movies table:

```
SELECT name
FROM movies
```

If we want to retrieve all the columns of data from the table, we use * in place of listing all the column names individually.

```
SELECT * 
FROM movies
```

`INSERT`
- Insert a row into the table

```
INSERT INTO movies 
VALUES  (1, “Up”, 98);
```

`UPDATE`
- Update values in one or more existing rows

```
UPDATE movies
SET rating = 91
WHERE ID = 1;
```

`DELETE`
- Delete one or more rows

```
DELETE FROM movies
WHERE ID = 1;
```

A `JOIN` is used to combine rows from two or more tables. There are different types of `JOINs`:

<img src="https://www.codeproject.com/KB/database/Visual_SQL_Joins/Visual_SQL_JOINS_orig.jpg" width="600">

`LEFT JOIN` aka `LEFT OUTER JOIN`
- Returns all records from the left table and matched records from right table
- Result is NULL from right side if there is no match

`RIGHT JOIN` aka `RIGHT OUTER JOIN`
- Returns all records from the right table and matched records from left table
- Result is NULL from left side when there is no match

`FULL OUTER JOIN`
- Return all records there is a match in either left or right table records

`INNER JOIN`
- Return records that have matching values in both tables

To learn further about SQL, here are some links:

- [Codecademy SQL](https://www.codecademy.com/learn/learn-sql)
- [SQLBolt](https://sqlbolt.com/)
- [w3schools](https://www.w3schools.com/sql/sql_intro.asp)






