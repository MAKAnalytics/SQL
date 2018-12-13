# SQL
Collection of SQL scripts for reference

## DATABASES
### Create a new database

```sql
CREATE DATABASE IF NOT EXISTS database_name
```

### Remove a database

```sql
DROP DATABASE IF EXISTS database_name
```


## TABLES
### Create a new table

```sql
CREATE TABLE IF NOT EXISTS table_name (
  column_a Datatype Constraints,
  column_b Datatype Constraints,
);
```

### Drop a table

```sql
DROP TABLE IF EXISTS table_name
```


## DATATYPES

**Datatype**|**Description**
-----|-----
`INT(n)`|Integer values
`FLOAT(n, d)`| Decimal values
`VARCHAR(n)`|String with max number of characters
`TEXT`|String with without set limit (max value of 65,535)
`DATE('YYYY-MM-DD')`|Year, month, and day
`DATETIME('YYYY-MM-DD HH:MI:SS')`|Year, month, day, hour, minute, and second
`TIMESTAMP('YYYY-MM-DD HH:MI:SS')`|Datetime corresponding to UNIX epoch time


## CONSTRAINTS

**Constraint**|**Description**
-----|-----
`PRIMARY KEY`|Unique identifier
`AUTO_INCREMENT`|Integer value is automatically added and incremented
`UNIQUE`|Value must be unique
`NOT NULL`|Value cannot be NULL
`DEFAULT`|Initialized with default value
