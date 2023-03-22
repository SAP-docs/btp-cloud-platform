<!-- loioadb1201971b64a0f973ebd9b7e9973e7 -->

# Common Table Expressions and Derived Tables

Common table expressions \(CTE\) can be used to define temporary view objects using a `WITH` clause at the beginning of a query that can later be used multiple times in the full select part.



Here's an example:

> ### Sample Code:  
> ```sql
> WITH A AS ( SELECT SCHEMA_NAME S, VIEW_NAME V FROM SYS.VIEWS )
> SELECT * FROM A WHERE A.S = 'SYS'
> UNION ALL
> SELECT * FROM A WHERE A.S = 'ZData'
> 
> ```

Recursive SQL in CTEs isn't supported.

As an alternative to CTEs, derived table clauses can be directly used in the `FROM` clause of a query, as in the following example:

> ### Sample Code:  
> ```sql
> SELECT * FROM ( SELECT SCHEMA_NAME S, VIEW_NAME V FROM SYS.VIEWS ) A
> WHERE A.S = 'SYS'
> 
> ```

While CTEs are also supported in ABAP SQL, derived table clauses are only supported in the SQL dialect of the ABAP SQL service.

Both queries with CTEs and with derived tables work a little different regarding case sensitivity of object names. Whenever you define a name in double quotes for the CTE or derived table itself or for returned column names, you must use the name in double quotes throughout the whole SQL statement, as in the following example:

> ### Sample Code:  
> ```sql
> SELECT * FROM ( SELECT SCHEMA_NAME "s", VIEW_NAME V FROM SYS.VIEWS ) "a"
> WHERE "a"."s" = 'SYS'
> 
> ```

The following query doesn't work because the double quotes are not used consistently:

> ### Sample Code:  
> ```sql
> SELECT * FROM ( SELECT SCHEMA_NAME "s", VIEW_NAME V FROM SYS.VIEWS ) "a"
> WHERE A.S = 'SYS'
> 
> ```

