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


