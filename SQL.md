# Basic SQL Structure
`SELECT` table_column(s)

`FROM` table_name

`WHERE` conditional filter(s)

## Creating and Deleting
* To create a database/table: `CREATE DATABASE dbName` or `CREATE TABLE tableName`
* To delete a database/table: `DROP DATABASE dbName` or `DROP TABLE tableName`
* Delete all data inside a table: `TRUNCATE TABLE tableName`
* Add a column to table: `ALTER TABLE tableName ADD Birthday DATE;`
* Delete column from table: `ALTER TABLE tableName DROP COLUMN Birthday;`


## Keys
* A **primary key** uniquely identifies each record in a given table
  * e.g. a customer_id column within the customers table
* A **foreign key** is a value in the current table which uniquely identifies records in another table
  * e.g. a customer_id column within the orders table

## `SELECT` Features
* `SELECT *` can be used to select all columns within a given table
  * Can cause performance issues in very large databases, generally a bad practice
* *Alias* may be used to display column name in a more human readable format
  * `SELECT` arbitrary_column_name `AS` my_name


## `FROM`
* The table that the query should run against
* `JOIN`s are used to run the query against multiple tables
  * `INNER JOIN` - the commonalities between tables; like the intersection of a venn diagram
  * `LEFT JOIN` - all rows from the left table, and the common rows from the right table; like the entire left circle and cross-section of a venn diagram
  * `RIGHT JOIN` - opposite of left join; like the entire right circle and the cross-section of a venn diagram

## `WHERE`
* A conditional clause that is used to filter resulting rows in a query

    Operator | Meaning
    ---------|--------
    = | Equal to
    <> | Not equal to
    < | Less than
    \> | Greater than
    <= | Less than or equal to
    \>= | Greater than or equal to

```
`SELECT`
   first_name,
   last_name
`FROM`
  employees
`WHERE`
  department_id = 3;
```

