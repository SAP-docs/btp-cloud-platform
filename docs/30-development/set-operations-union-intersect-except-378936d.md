<!-- loio378936dadaaf413b94970fe08eba9ffb -->

# Set Operations UNION, INTERSECT, EXCEPT

Like in ABAP SQL and HANA SQL, you can use the standard set operations `UNION`, `INTERSECT`, and `EXCEPT` to combine result sets of multiple queries in one query.



Here are some examples:

> ### Sample Code:  
> ```sql
> select DUMMY FROM SYS.DUMMY A EXCEPT SELECT 'X' FROM SYS.DUMMY B
> 
> select DUMMY FROM SYS.DUMMY EXCEPT SELECT 'X' FROM SYS.DUMMY
> 
> ```

In cases where the same table name is used in multiple `UNION ALL` branches, the ABAP SQL engine requires that these tables are given different alias names.

