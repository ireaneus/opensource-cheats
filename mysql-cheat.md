# MySQL Cheat Sheet

## MySQL Command-Line Client Commands

```sql
-- Connect to MySQL server
mysql -u [username] -p

-- Connect to MySQL server with a specific database
mysql -u [username] -p [database]

-- Exit MySQL command-line client
exit

-- Export data using mysqldump
mysqldump -u [username] -p [database] > data_backup.sql

-- Clear the MySQL screen (Linux)
mysql> system clear;
```

## Working with Databases

```sql
-- Create a new database
CREATE DATABASE [IF NOT EXISTS] database_name;

-- Select a database
USE database_name;

-- Drop a database
DROP DATABASE [IF EXISTS] database_name;

-- Show all databases
SHOW DATABASES;
```

## Working with Tables

```sql
-- Show all tables in the current database
SHOW TABLES;

-- Create a new table
CREATE TABLE [IF NOT EXISTS] table_name (
  column_list
);

-- Add a new column to a table
ALTER TABLE table_name
ADD [COLUMN] column_name datatype;

-- Drop a column from a table
ALTER TABLE table_name
DROP [COLUMN] column_name;

-- Add an index to a table
ALTER TABLE table_name
ADD INDEX index_name (column_name, ...);

-- Add a primary key to a table
ALTER TABLE table_name
ADD PRIMARY KEY (column_name, ...);

-- Drop the primary key from a table
ALTER TABLE table_name
DROP PRIMARY KEY;

-- Drop a table
DROP TABLE [IF EXISTS] table_name;

-- Show the columns of a table
DESCRIBE table_name;

-- Show information of a specific column in a table
DESCRIBE table_name column_name;
```

## Working with Indexes

```sql
-- Create an index
CREATE INDEX index_name
ON table_name (column_name, ...);

-- Drop an index
DROP INDEX index_name ON table_name;

-- Create a unique index
CREATE UNIQUE INDEX index_name
ON table_name (column_name, ...);
```

## Working with Views

```sql
-- Create a new view
CREATE VIEW [IF NOT EXISTS] view_name AS
SELECT column1, column2, ...
FROM table_name
WHERE condition;

-- Create a new view with CHECK OPTION
CREATE VIEW [IF NOT EXISTS] view_name AS
SELECT column1, column2, ...
FROM table_name
WHERE condition
WITH CHECK OPTION;

-- Create or replace a view
CREATE OR REPLACE VIEW view_name AS
SELECT column1, column2, ...
FROM table_name
WHERE condition;

-- Drop a view
DROP VIEW [IF EXISTS] view_name;

-- Drop multiple views
DROP VIEW [IF EXISTS] view1, view2, ...;
```
