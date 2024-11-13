<!-- loio532dbeb42d074c53a255192c6567cc75 -->

# ABAP CDS: SQL-Based Scalar Functions

In the SQL dialect of the ABAP SQL service, you can use the system views `SYS.FUNCTIONS` and `SYS.FUNCTION_PARAMETERS` to discover CDS SQL-based scalar functions and retrieve their metadata.



## Motivation and Background

When you are using SQL services to access ABAP-managed data, you might want to use CDS SQL-based scalar functions. SQL-based scalar functions are scalar functions that are evaluated by an SQL environment.

However, the CDS scalar functions don't have a representation in the metadata access functions of ODBC. The CDS scalar functions are **not** represented in the system views `SYS.VIEWS` and `SYS.VIEW_PARAMETERS`, either, which are used for metadata retrieval for the SQL service \(see [Retrieving Table Metadata Using System Tables](retrieving-table-metadata-using-system-tables-9cb1891.md)\).

Therefore, for the SQL service, the system views `SYS.FUNCTIONS` and `SYS.FUNCTION_PARAMETERS` are available so that metadata of CDS SQL-based scalar functions can be exposed.



<a name="loio532dbeb42d074c53a255192c6567cc75__section_w24_b1x_hbc"/>

## Metadata Views SYS.FUNCTIONS and SYS.FUNCTION\_PARAMETERS

The system view `SYS.FUNCTIONS` exposes the function name and description of all SQL-based scalar functions for which the flag *Auto Exposure* has been set. This flag applies to all SQL-based scalar functions released by SAP for auto exposure; you can also set it for your own custom SQL-based scalar functions. The system view `SYS.FUNCTION_PARAMETERS` exposes detail information about the parameters of the SQL-based scalar functions.

The system views `SYS.FUNCTIONS` and `SYS.FUNCTION_PARAMETERS` are automatically exposed with the CDS name and can be used in requests to the SQL service without any restrictions. No additional authorizations and no further explicit declarations are needed. The system views are intended for scalar functions for specialized conversions or system-wide valid common expressions, for example, without exposing application data.

The system views are exposed with their CDS name with mixed case; there is no possibility to define an alias name. They don't belong to a schema in the SQL service, but they are accessed like built-in CDS scalar functions \(for example, `CONCAT`\) without a schema qualification.



<a name="loio532dbeb42d074c53a255192c6567cc75__section_jjh_fgr_nbc"/>

## Constraints

With the SQL service, you can't use scalar functions that have parameters of a generic ABAP type such as `NUMERIC` or that use reference types.



<a name="loio532dbeb42d074c53a255192c6567cc75__section_ibt_5bx_hbc"/>

## Code Samples

Using this code sample, you can discover available CDS SQL-based scalar functions that are automatically exposed in your system:

> ### Sample Code:  
> ```
> SQL> select FUNCTION_NAME, DESCRIPTION 
>      FROM SYS.FUNCTIONS S 
>      WHERE S.FUNCTION_TYPE = 'SCALAR' 
>        AND S.SCHEMA_NAME   = ''
> 
> ```

> ### Note:  
> To find automatically exposed functions \(which must be accessed without schema name qualification\), you must use the filter `SCHEMA_NAME = ''`. To make sure that you only get the scalar functions, use the filter `FUNCTION_TYPE = 'SCALAR'`.

The following code sample illustrates how you can get information about the parameters of the demo scalar function `DEMO_CDS_DECFLOAT_RATIO`:

> ### Sample Code:  
> ```
> SQL> select PARAMETER_NAME, PARAMETER_TYPE, DDIC_TYPE_NAME, ODBC_DATA_TYPE, ODBC_COLUMN_SIZE 
> FROM SYS.FUNCTIONS S 
> INNER JOIN SYS.FUNCTION_PARAMETERS P ON S.SCHEMA_NAME = P.SCHEMA_NAME and S.FUNCTION_NAME = P.FUNCTION_NAME 
> WHERE S.FUNCTION_TYPE = 'SCALAR' 
> AND S.SCHEMA_NAME   = '' 
> AND S.FUNCTION_NAME = 'DEMO_CDS_DECFLOAT_RATIO'
> +-------------------------------+---------------+---------------+---------------+-----------------+
> 
> | PARAMETER_NAME                | PARAMETER_TYPE| DDIC_TYPE_NAME| ODBC_DATA_TYPE| ODBC_COLUMN_SIZE|
> 
> +-------------------------------+---------------+---------------+---------------+-----------------+
> | base                          | IN            | D34N          | -360          | 34              |
> | portion                       | IN            | D34N          | -360          | 34              |
> |                               | RETURN        | D34N          | -360          | 34              |
> +-------------------------------+---------------+---------------+---------------+-----------------+
> 
> SQLRowCount returns 0
> 3 rows fetched
> 
> ```

In the following code sample, the demo scalar function `DEMO_CDS_DECFLOAT_RATIO` is applied to calculate a ratio:

> ### Sample Code:  
> ```
> SQL> select DEMO_CDS_DECFLOAT_RATIO( base => CAST( 200 AS DECIMAL) , portion => CAST( 50 AS DECIMAL) ) FROM SYS.DUMMY
> +-------------------------------------------+
> |                                           |
> +-------------------------------------------+
> | 25                                        |
> +-------------------------------------------+
> 
> SQLRowCount returns 0
> 1 rows fetched
> 
> ```

