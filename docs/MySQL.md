# MySQL

## Categories of SQL statements (e.g. DDL vs DML)

SQL commands are grouped into the following categories:

* DDL - data **definition** language - statements that change the schema. Examples: CREATE, DROP, ALTER, TRUNCATE, RENAME
* DML - data **manipulation** language - statements that change the data itself. Examples: INSERT, UPDATE, DELETE, LOCK
* DQL - data **query** language - statements that retrieve data. Examples: SELECT
* DCL - data **control** language - statements that manage access to data. Examples: GRANT, REVOKE

-- https://www.geeksforgeeks.org/sql-ddl-dql-dml-dcl-tcl-commands/

## Describe a Table's Structure

`describe <table name>` or `desc <table name`.

The output is more readable than `show create table <table name>`
