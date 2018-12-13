# SQL
Collection of SQL scripts for reference

## DATABASES
> ### Create a new database

> ```sql
> CREATE DATABASE IF NOT EXISTS database_name
> ```

> ### Remove a database

> ```sql
> DROP DATABASE IF EXISTS database_name
> ```


## TABLES
> ### Create a new table

> ```sql
> CREATE TABLE IF NOT EXISTS table_name (
>   column_a Datatype Constraints,
>   column_b Datatype Constraints,
> );
> ```

> ### Drop a table

> ```sql
> DROP TABLE IF EXISTS table_name
> ```


## DATATYPES
> ### Numeric

> **Datatype**|**Range**
> -----|-----
> `BIT`|0 or 1
> `TINYINT`|0 to 255
> `SMALLINT`|-32,768 to 32,767
> `INT`|-2,147,483,648 to 2,147,483,647
> `BIGINT`|-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807
> `DECIMAL`|-10^38 +1 to 10^38 -1
> `FLOAT`|-1.79E+308 to 1.79E+308
> `REAL`|-3.40E+38 to 3.40E+38

> ### Date and time

> **Datatype**|**Description**
> -----|-----
> `DATE`|Format is YYYY-MM-DD
> `TIME`|Format is HH:MI:SS
> `DATETIME`|Format is YYYY-MM-DD HH:MI:SS
> `TIMESTAMP`|Number of seconds since the UNIX epoch (‘1970-01-01 00:00:00’ UTC)
> `YEAR`|Stores year in 2 digit (70-69 represents 1970-2069) or 4 digit format (1901-2155)

> ### Character and string
> **Datatype**|**Description**
> -----|-----
> `CHAR`|Fixed length string with maximum length of 8,000 characters
> `VARCHAR`|Variable length string with maximum length of 8,000 characters
> `VARCHAR(max)`|Variable length string with 'max' characters
> `TEXT`|Variable length string with maximum size of 2GB data

> ### Unicode character and string
> **Datatype**|**Description**
> -----|-----
> `NCHAR`|Fixed length string with maximum length of 4,000 characters
> `NVARCHAR`|Variable length string with maximum length of 4,000 characters
> `NVARCHAR(max)`|Variable length string with 'max' characters
> `NTEXT`|Variable length string with maximum size of 1GB data

> ### Unicode character and string
> **Datatype**|**Description**
> -----|-----
> `BINARY`|Fixed length with maximum length of 8,000 bytes
> `VARBINARY`|Variable length with maximum length of 4,000 bytes
> `VARBINARY(max)`|Variable string with 'max' bytes
> `IMAGE`|Variable length storage with maximum size of 2GB binary data

> ### Miscellaneous
> **Datatype**|**Description**
> -----|-----
> `CLOB`|Character large objects that can hold up to 2GB
> `BLOB`|Binary large objects
> `XML`|Stores XML data
> `JSON`|Stores JSON data


## CONSTRAINTS

**Constraint**|**Description**
-----|-----
`PRIMARY KEY`|Unique identifier
`AUTO_INCREMENT`|Integer value is automatically added and incremented
`UNIQUE`|Value must be unique
`NOT NULL`|Value cannot be NULL
`DEFAULT`|Initialized with default value
