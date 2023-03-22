<!-- loio37e7f19ed112458683f9a39521e62fdd -->

# The Driver-Specific SQL\_DECFLOAT Type

For the decimal floating-point types, the ODBC driver for ABAP has its own ODBC SQL data type `SQL_DECFLOAT=-360` defined.



## Motivation

The ODBC standard doesn’t define a decimal floating-point type. However, there are databases like the SAP HANA database or the ABAP system itself \(if it’s viewed as a database\) that support such types. The main reason for using these types is to avoid rounding problems that would occur when using the double floating-point type with radix 2. ABAP applications often use decimal floating-point data for business data where such rounding could cause problems.

Note the rounding artifacts in the following query result:

> ### Sample Code:  
> ```sql
> SQL> select cast (10000 as double) * cast (1.11 as double) as c_DOUBLE,
>             cast (10000 as DECIMAL) * cast (1.11 as DECIMAL) as c_D34N
>      from sys.dummy
> 
> +------------------------------------+----------------------------+
> | C_DOUBLE                           | C_D34N                     |                   
> +------------------------------------+----------------------------+
> | 11100.000000000001818989403545856  | 11100.00                   |                         
> +------------------------------------+----------------------------+
> 
> ```



<a name="loio37e7f19ed112458683f9a39521e62fdd__section_oth_s3n_4wb"/>

## ODBC SQL Data Type `SQL_DECFLOAT=-360`

The ODBC standard allows that ODBC drivers define their own driver-specific data types if needed. The ODBC driver for ABAP has taken this way for the decimal floating-point types: It has defined its own ODBC SQL data type `SQL_DECFLOAT=-360` with two different octet lengths corresponding to the `abap.d16n` and `abap.d34n` data types. ODBC applications that want to retrieve such `SQL_DECFLOAT` data must use default target data type `SQL_C_CHAR` or `SQL_C_WCHAR` to return the data in readable string format.

