<!-- loio9bd0c84342324479a30cd76cdd6379af -->

# Prepared Statements with Parameter Markers

Like in HANA SQL, statement texts can contain unnamed parameter markers \( ‘?’ \).



These statements can be prepared once and executed multiple times using different value bindings at execution time. A simple example is the following SQL statement with four input parameters:

> ### Sample Code:  
> ```sql
> Select * from "ZData"."OrderItems"
> where "OrderId" = ? or "OrderId" IN ( ?, ?, ? )
> 
> ```

The data types of the parameter markers are restricted to simple DDIC/ODBC types and no table-like input is supported.

