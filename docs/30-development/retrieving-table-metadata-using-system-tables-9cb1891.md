<!-- loio9cb1891bd6d54285b1e0981fe793c1fa -->

# Retrieving Table Metadata Using System Tables

In the SQL dialect of the ABAP SQL service, you can use system tables to retrieve table metadata. For example, the system table `SYS.VIEWS` provides data similar to the ODBC function `SQLTables()`, `SYS.COLUMNS` provides data similar to what you get using `SQLColumns()`. With `SYS.VIEW_PARAMETERS`, you can get view parameters.



## Motivation

In ODBC, object metadata can be retrieved using ODBC functions like `SQLTables()` or `SQLColumns()`. However, in SQL services, view entities with parameters can also be exposed and ODBC has no clear concept for these objects. Therefore, the SQL service also provides a set of system tables where metadata can be retrieved using SQL.

The system tables are automatically exposed and contain information about the objects that can be accessed in the current ODBC connection to the ABAP back end. The objects visible in an ODBC connection depend on the ABAP user privileges and on the service path used to open the ODBC connection \(with a communication or a business user\).



<a name="loio9cb1891bd6d54285b1e0981fe793c1fa__section_vyw_wz5_4wb"/>

## SYS.VIEWS

The system table `SYS.VIEWS` works similar to the ODBC function `SQLTables()` and lists all CDS view entities visible in the current ODBC connection including the system tables themselves. The column `HAS_PARAMETERS` can be used to determine whether a view has parameters:

> ### Sample Code:  
> ```sql
> SQL> select schema_name, view_name from SYS.VIEWS where schema_name = 'SYS'
> 
> +-------------------------------+-------------------------------+
> | SCHEMA_NAME                   | VIEW_NAME                     |
> +-------------------------------+-------------------------------+
> | SYS                           | DUMMY                         |
> | SYS                           | M_CONNECTION_INFO             |
> | SYS                           | VIEWS                         |
> | SYS                           | VIEW_COLUMNS                  |
> | SYS                           | VIEW_PARAMETERS               |
> +-------------------------------+-------------------------------+
> 
> ```



<a name="loio9cb1891bd6d54285b1e0981fe793c1fa__section_ggy_4z5_4wb"/>

## SYS.VIEW\_COLUMNS

The system table `SYS.VIEW_COLUMNS` lists column information for the exposed entities containing both ODBC and ABAP metadata:

> ### Sample Code:  
> ```sql
> SQL> select COLUMN_NAME, ODBC_DATA_TYPE OD,
>             ODBC_BUFFER_LENGTH OBL, DDIC_TYPE_NAME, DDIC_LENGTH
>      from SYS.VIEW_COLUMNS
>      where schema_name = 'SYS' and view_name = 'VIEW_COLUMNS'
>      order by column_position
> 
> +--------------------+-----+-----+---------------+------------
> | COLUMN_NAME        | OD  | OBL | DDIC_TYPE_NAME| DDIC_LENGTH|
> +--------------------+-----+-----+---------------+------------+
> | SCHEMA_NAME        | -8  | 60  | CHAR          | 30         |
> | VIEW_NAME          | -8  | 60  | CHAR          | 30         |
> | COLUMN_NAME        | -8  | 60  | CHAR          | 30         |
> | SCHEMA_NAME_UPPER  | -8  | 60  | CHAR          | 30         |
> | VIEW_NAME_UPPER    | -8  | 60  | CHAR          | 30         |
> | COLUMN_NAME_UPPER  | -8  | 60  | CHAR          | 30         |
> | COLUMN_POSITION    | 4   | 4   | INT4          | 10         |
> | DESCRIPTION        | -8  | 500 | CHAR          | 250        |
> | IS_KEY             | -8  | 10  | CHAR          | 5          |
> | ODBC_DATA_TYPE     | 5   | 2   | INT2          | 5          |
> | ODBC_TYPE_NAME     | -8  | 8   | CHAR          | 4          |
> | ODBC_COLUMN_SIZE   | 4   | 4   | INT4          | 10         |
> | ODBC_DECIMAL_DIGITS| 5   | 2   | INT2          | 5          |
> | ODBC_BUFFER_LENGTH | 4   | 4   | INT4          | 10         |
> | ODBC_NUM_PREC_RADIX| 5   | 2   | INT2          | 5          |
> | ODBC_NULLABLE      | 5   | 2   | INT2          | 5          |
> | DDIC_TYPE_NAME     | -8  | 8   | CHAR          | 4          |
> | DDIC_LENGTH        | 4   | 4   | INT4          | 10         |
> | DDIC_DECIMALS      | 5   | 2   | INT2          | 5          |
> +--------------------+-----+-----+---------------+------------+
> 
> ```



<a name="loio9cb1891bd6d54285b1e0981fe793c1fa__section_pzn_tz5_4wb"/>

## SYS.VIEW\_PARAMETERS

The system table `SYS.VIEW_PARAMETERS` contains ODBC and ABAP metadata for view parameters \(`HAS_PARAMETERS = ‘TRUE’` in `SYS.VIEWS`\). For an example, see [Named Parameter Syntax on Views with Parameters](named-parameter-syntax-on-views-with-parameters-77b7d7b.md).



<a name="loio9cb1891bd6d54285b1e0981fe793c1fa__section_wn3_pz5_4wb"/>

## Other System and Monitoring Tables

`SYS.DUMMY` is a dummy table with one row and works like the corresponding SAP HANA database table. Many of the SQL examples throughout this documentation use this dummy table.

The monitoring view `SYS.M_CONNECTION_INFO` contains information about the current ODBC connection \(for example, ABAP user name, alias, client, SQL service name, and EPP information\).

> ### Note:  
> You can't use the system tables `SYS.VIEWS`, `SYS.VIEW_COLUMNS`, and `SYS.VIEW_PARAMETERS` to retrieve metadata about CDS SQL-based scalar functions. For CDS scalar functions, use the system tables `SYS.FUNCTIONS` and `SYS.FUNCTION_PARAMETERS`.

**Related Information**  


[ABAP CDS: SQL-Based Scalar Functions](abap-cds-sql-based-scalar-functions-532dbeb.md "In the SQL dialect of the ABAP SQL service, you can use the system views SYS.FUNCTIONS and SYS.FUNCTION_PARAMETERS to discover CDS SQL-based scalar functions and retrieve their metadata.")

