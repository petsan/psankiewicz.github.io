# SQL (Structured Query Language)

## Create a database

CREATE DATABASE database_name

## Delete a database

DROP DATABASE database_name

## Create a table in a dababase

CREATE TABLE "table_name"

("column_1" "data_type_for_column_1", "column_2" "data_type_for_column_2", ... )

## SELECT

### Select data from a table

SELECT column_name(s) FROM table_name

### Select all data from a table

SELECT * FROM table_name

### Select only distinct data from a table

SELECT DISTINCT column_name(s) FROM table_name

### Select only certain data from a table

SELECT column_name(s) FROM table_name
WHERE column operator value
      AND column operator value
      OR column operator value
      AND (... OR ...)
      ...

### Operators

=	    Equal

<>	    Not equal

\>	    Greater than

<	    Less than

\>=	    Greater than or equal

<=	    Less than or equal

BETWEEN	    Between an inclusive range

LIKE	    Search for a pattern.

ASC	     Ascending alpha-numerical order

DSC	    Descending alpha-numerical order

GROUP BY	    group of column values

AVG(column)	    Returns the average value of a column

COUNT(column)	    Returns the number of rows (without a NULL value) of a column

MAX(column)	    Returns the highest value of a column

MIN(column)	    Returns the lowest value of a column

SUM(column)	    Returns the total sum of a column

A "%" sign can be used to define wildcards (missing letters in the pattern) both before and after the pattern.
