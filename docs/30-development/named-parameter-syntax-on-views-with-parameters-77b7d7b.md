<!-- loio77b7d7b8ba9542c494427f237e56c7f3 -->

# Named Parameter Syntax on Views with Parameters

The SQL dialect of the ABAP SQL service supports named parameter syntax on views with parameters.



> ### Note:  
> The named parameter syntax is also supported in HANA SQL. However, the SQL dialect of the ABAP SQL service doesn’t support positioned parameter syntax.

Here’s a simple example with a CDS entity with one parameter to illustrate how it works:

> ### Sample Code:  
> ```sql
> @AbapCatalog.viewEnhancementCategory: [#NONE]
> @AccessControl.authorizationCheck: #NOT_ALLOWED
> @EndUserText.label: 'Test entity with parameter'
> 
> define view entity ZENTITYWITHPARAM with parameters
>   im_int: abap.int4
> as select from svers {
>   key version as keyCol,
>   $parameters.im_int as IntCol
> }
> 
> ```

Let’s also assume you've exposed this entity in your service definition with external name `ZEntityWithParam` and with corresponding service binding `ZData`.

After activating all ABAP objects, the system views will now show the following entries:

> ### Sample Code:  
> ```sql
> SQL> select HAS_PARAMETERS from SYS.VIEWS
>       WHERE schema_name = 'ZData'
>         and view_name   = 'ZEntityWithParam'
> 
> +---------------+
> | HAS_PARAMETERS|
> +---------------+
> | TRUE          |
> +---------------+
> 
> SQL> select PARAMETER_NAME, ODBC_DATA_TYPE, DDIC_TYPE_NAME, DDIC_LENGTH
>        from SYS.VIEW_PARAMETERS
>       WHERE schema_name = 'ZData'
>         and view_name   = 'ZEntityWithParam'
> 
> +----------------+---------------+---------------+------------+
> | PARAMETER_NAME | ODBC_DATA_TYPE| DDIC_TYPE_NAME| DDIC_LENGTH|
> +----------------+---------------+---------------+------------+
> | im_int         | 4             | INT4          | 4          |
> +----------------+---------------+---------------+------------+
> 
> SQL> select COLUMN_NAME, ODBC_DATA_TYPE, DDIC_TYPE_NAME, DDIC_LENGTH
>        from SYS.VIEW_COLUMNS
>       WHERE schema_name = 'ZData'
>         and view_name   = 'ZEntityWithParam'
> 
> +----------------+---------------+---------------+------------+
> | COLUMN_NAME    | ODBC_DATA_TYPE| DDIC_TYPE_NAME| DDIC_LENGTH|
> +----------------+---------------+---------------+------------+
> | keyCol         | -8            | CHAR          | 72         |
> | IntCol         | 4             | INT4          | 4          |
> +----------------+---------------+---------------+------------+
> 
> ```

Now, you can run SQL queries on the new entity with named parameter syntax:

> ### Sample Code:  
> ```sql
> SQL> select * from ZData.ZEntityWithParam ( im_int => 4711 )
> 
> +---------------------------------+
> | keyCol         | IntCol         |
> +----------------+----------------+
> | 7xx            | 4711           |
> +---------------------------------+
> 
> ```

