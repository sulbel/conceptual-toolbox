# Basic SQL Structure
`SELECT` table_column(s)

`FROM` table_name

`WHERE` conditional filter(s)

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