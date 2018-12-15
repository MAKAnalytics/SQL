# SQL
Collection of SQL scripts for reference

# TABLE OF CONTENTS
1. [DATABASES](#databases)
2. [Create a new database](#create-a-new-database)
3. [Remove a database](#remove-a-database)
4. [TABLES](#tables)
5. [Create a new table](#create-a-new-table)
6. [Remove a table](#remove-a-table)
7. [FINDING DATA](#finding-data)
8. [Select](#select)
9. [Distinct](#distinct)
10. [Where](#where)
11. [Order by](#order-by)
12. [Top](#top)
13. [Like](#like)
14. [In](#in)
15. [Between](#between)
16. [Null](#null)
17. [As](#as)
18. [Union](#union)
19. [Intersect](#intersect)
20. [Except](#except)
21. [Any|All](#anyall)
22. [Group by](#group-by)
23. [Having](#having)
24. [With](#with)
25. [DATATYPES](#datatypes)
26. [Numeric](#numeric)
27. [Date and time](#date-and-time)
28. [Character and string](#character-and-string)
29. [Unicode character and string](#unicode-character-and-string)
30. [Binary](#binary)
31. [Miscellaneous](#miscellaneous)
32. [CONSTRAINTS](#constraints)

## DATABASES<a name="databases"></a>
> ### Create a new database<a name="create-a-new-database"></a>
> ```sql
> CREATE DATABASE IF NOT EXISTS database_name
> ```

> ### Remove a database<a name="remove-a-database"></a>
> ```sql
> DROP DATABASE IF EXISTS database_name
> ```


## TABLES<a name="tables"></a>
> ### Create a new table<a name="create-a-new-table"></a>
> ```sql
> CREATE TABLE IF NOT EXISTS table_name (
>   column_a Datatype Constraints,
>   column_b Datatype Constraints,
> );
> ```

> ### Remove a table<a name="remove-a-table"></a>
> ```sql
> DROP TABLE IF EXISTS table_name
> ```

## FINDING DATA<a name="finding-data"></a>
> ### SELECT<a name="select"></a>
> Select all records from a table:
> ```sql
> SELECT * FROM table_name;
> ```
> Select columns 1 and 2 from a table:
> ```sql
> SELECT column1, column2 FROM table_name;
> ```

> ### DISTINCT<a name="distinct"></a>
> Returns only unique results from a column:
> ```sql
> SELECT DISTINCT column_name;
> ```

> ### WHERE<a name="where"></a>
> Filters rows based on one or more conditions
> ```sql
> SELECT column1, column2 FROM table_name WHERE condition;
> SELECT * FROM table_name WHERE condition1 AND condition2;
> SELECT * FROM table_name WHERE condition1 OR condition2;
> SELECT * FROM table_name WHERE NOT condition;
> SELECT * FROM table_name WHERE condition1 AND (condition2 OR condition3);
> SELECT * FROM table_name WHERE EXISTS (SELECT column_name FROM table_name WHERE condition);
> ```

> ### ORDER BY<a name="order-by"></a>
> Sorts the result-set in ascending or descending order
> ```sql
> SELECT * FROM table_name ORDER BY column;
> SELECT * FROM table_name ORDER BY column DESC;
> SELECT * FROM table_name ORDER BY column1 ASC, column2 DESC;
> ```

> ### SELECT TOP<a name="top"></a>
> Specify the number of records to return from the top of table
> ```sql
> SELECT TOP number columns_names FROM table_name WHERE condition;
> SELECT TOP percent columns_names FROM table_name WHERE condition;
> ```
> Not all database systems support SELECT TOP. The MySQL equivalent is the LIMIT clause
> ```sql
> SELECT column_names FROM table_name LIMIT offset, count;
> ```

> ### LIKE<a name="like"></a>
> Operator used in a WHERE clause to search for a specific pattern in a column
> % (percent sign) is a wildcard character that represents zero, one, or multiple characters
> _ (underscore) is a wildcard character that represents a single character
> ```sql
> SELECT column_names FROM table_name WHERE column_name LIKE pattern;
> LIKE ‘a%’ (find any values that start with “a”)
> LIKE ‘%a’ (find any values that end with “a”)
> LIKE ‘%or%’ (find any values that have “or” in any position)
> LIKE ‘_r%’ (find any values that have “r” in the second position)
> LIKE ‘a_%_%’ (find any values that start with “a” and are at least 3 characters in length)
> LIKE ‘[a-c]%’ (find any values starting with “a”, “b”, or “c”
> ```

> ### IN<a name="in"></a>
> Operator that allows you to specify multiple values in a WHERE clause
> essentially the IN operator is shorthand for multiple OR conditions
> ```sql
> SELECT column_names FROM table_name WHERE column_name IN (value1, value2, …);
> SELECT column_names FROM table_name WHERE column_name IN (SELECT STATEMENT);
> ```

> ### BETWEEN<a name="between"></a>
> Operator selects values within a given range inclusive
> ```sql
> SELECT column_names FROM table_name 
> WHERE column_name BETWEEN value1 AND value2;
> SELECT * FROM Products 
> WHERE (column_name BETWEEN value1 AND value2) AND NOT column_name2 IN (value3, value4);
> SELECT * FROM Products 
> WHERE column_name BETWEEN 01/07/1999 AND 03/12/1999;
> ```

> ### NULL<a name="null"></a>
> Values in a field with no value
> ```sql
> SELECT * FROM table_name WHERE column_name IS NULL;
> SELECT * FROM table_name WHERE column_name IS NOT NULL;
> ```

> ### AS<a name="as"></a>
> Aliases that are used to assign a temporary name to a table or column
> ```sql
> SELECT column_name AS alias_name FROM table_name;
> SELECT column_name FROM table_name AS alias_name;
> SELECT column_name AS alias_name1, column_name2 AS alias_name2;
> SELECT column_name1, column_name2 + ‘, ‘ + column_name3 AS alias_name;
> ```

> ### UNION<a name="union"></a>
> Set operator used to combine the result-set of two or more SELECT statements
> Each SELECT statement within UNION must have the same number of columns
> The columns must have similar data types
> The columns in each SELECT statement must also be in the same order
> ```sql
> SELECT columns_names FROM table1 UNION SELECT column_name FROM table2;
> UNION operator only selects distinct values, UNION ALL will allow duplicates
> ```

> ### INTERSECT<a name="intersect"></a>
> Set operator which is used to return the records that two SELECT statements have in common
> Generally used the same way as UNION above
> ```sql
> SELECT columns_names FROM table1 INTERSECT SELECT column_name FROM table2;
> ```

> ### EXCEPT<a name="except"></a>
> Set operator used to return all the records in the first SELECT statement that are not found in the second SELECT statement
> Generally used the same way as **UNION** above
> ```sql
> SELECT columns_names FROM table1 EXCEPT SELECT column_name FROM table2;
> ```

> ### ANY|ALL<a name="anyall"></a>
> Operator used to check subquery conditions used within a WHERE or HAVING clauses
> The ANY operator returns true if any subquery values meet the condition
> The ALL operator returns true if all subquery values meet the condition
> ```sql
> SELECT columns_names FROM table1 WHERE column_name operator (ANY|ALL) 
>   (SELECT column_name FROM table_name WHERE condition);
> ```

> ### GROUP BY<a name="group-by"></a>
> Statement often used with aggregate functions (COUNT, MAX, MIN, SUM, AVG) to group the result-set by one or more columns
> ```sql
> SELECT column_name1, COUNT(column_name2) FROM table_name 
> WHERE condition `GROUP BY` column_name1 
> ORDER BY COUNT(column_name2) DESC;
> ```

> ### HAVING<a name="having"></a>
> This clause was added to SQL because the WHERE keyword could not be used with aggregate functions
> ```sql
> SELECT COUNT(column_name1), column_name2 FROM table 
> GROUP BY column_name2 
> HAVING COUNT(column_name1) > 5;
> ```

> ### WITH<a name="with"></a>
> Often used for retrieving hierarchical data or re-using temp result set several times in a query. Also referred to as "Common Table Expression"
> ```sql
> WITH RECURSIVE cte AS (
>   SELECT c0.* FROM categories AS c0 
>   WHERE id = 1 # Starting point
>   UNION ALL
>   SELECT c1.* FROM categories AS c1 
>   JOIN cte ON c1.parent_category_id = cte.id
> )
> SELECT * FROM cte
> ```

## DATATYPES<a name="datatypes"></a>
> ### Numeric<a name="numeric"></a>
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

> ### Date and time<a name="date-and-time"></a>
> **Datatype**|**Description**
> -----|-----
> `DATE`|Format is YYYY-MM-DD
> `TIME`|Format is HH:MI:SS
> `DATETIME`|Format is YYYY-MM-DD HH:MI:SS
> `TIMESTAMP`|Number of seconds since the UNIX epoch (‘1970-01-01 00:00:00’ UTC)
> `YEAR`|Stores year in 2 digit (70-69 represents 1970-2069) or 4 digit format (1901-2155)

> ### Character and string<a name="character-and-string"></a>
> **Datatype**|**Description**
> -----|-----
> `CHAR`|Fixed length string with maximum length of 8,000 characters
> `VARCHAR`|Variable length string with maximum length of 8,000 characters
> `VARCHAR(max)`|Variable length string with 'max' characters
> `TEXT`|Variable length string with maximum size of 2GB data

> ### Unicode character and string<a name="unicode-character-and-string"></a>
> **Datatype**|**Description**
> -----|-----
> `NCHAR`|Fixed length string with maximum length of 4,000 characters
> `NVARCHAR`|Variable length string with maximum length of 4,000 characters
> `NVARCHAR(max)`|Variable length string with 'max' characters
> `NTEXT`|Variable length string with maximum size of 1GB data

> ### Binary<a name="binary"></a>
> **Datatype**|**Description**
> -----|-----
> `BINARY`|Fixed length with maximum length of 8,000 bytes
> `VARBINARY`|Variable length with maximum length of 4,000 bytes
> `VARBINARY(max)`|Variable string with 'max' bytes
> `IMAGE`|Variable length storage with maximum size of 2GB binary data

> ### Miscellaneous<a name="miscellaneous"></a>
> **Datatype**|**Description**
> -----|-----
> `CLOB`|Character large objects that can hold up to 2GB
> `BLOB`|Binary large objects
> `XML`|Stores XML data
> `JSON`|Stores JSON data


## CONSTRAINTS<a name="constraints"></a>
> **Constraint**|**Description**
> -----|-----
> `PRIMARY KEY`|Unique identifier
> `AUTO_INCREMENT`|Integer value is automatically added and incremented
> `UNIQUE`|Value must be unique
> `NOT NULL`|Value cannot be NULL
> `DEFAULT`|Initialized with default value
