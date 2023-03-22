<!-- loio6a3ad0a106b74d738bd6c92b212d7636 -->

# Supported JOIN Syntax

The supported `JOIN` syntax in the SQL dialect of the ABAP SQL service is similar to HANA SQL.



The commonly known ANSI SQL clauses `INNER JOIN`, `LEFT OUTER JOIN`, `RIGHT OUTER JOIN`, and `CROSS JOIN` are supported. For a `LEFT OUTER JOIN`, you can also add the SAP HANA-specific `LEFT OUTER MANY TO ONE JOIN` clause.

Instead of using explicit `JOIN` clauses, you can also use a comma-separated list of tables in the `FROM` clause to express an `INNER JOIN` or a `CROSS JOIN`. This feature isn't supported in ABAP SQL, but in the SQL dialect of the ABAP SQL service it is.

Here are some examples:

> ### Sample Code:  
> ```sql
> select A.DUMMY FROM SYS.DUMMY A 
> CROSS JOIN SYS.DUMMY B
> 
> select A.DUMMY FROM SYS.DUMMY A , SYS.DUMMY B
> 
> select A.DUMMY FROM SYS.DUMMY A 
> LEFT OUTER MANY TO ONE JOIN SYS.DUMMY B
> ON A.DUMMY = B.DUMMY
> 
> ```

