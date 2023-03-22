<!-- loioe812afecfb264f06bb6efb4eff66cd84 -->

# Literals and ODBC Escape Sequences

Literal values can be used in the SQL dialect of the ABAP SQL service similar to HANA SQL.



For numeric literals, you can add an explicit type cast to enforce a specific data type in the result set. For character-like data types, you can enclose the literals in single quotes. A prefix `N` is optional. Raw \(binary\) literals must be enclosed in single quotes with prefix `x`. In the single quotes, you provide the hex string representation of the raw value. For `DATE`/`TIME`/`TIMESTAMP` \(`abap.datn`/`abap.timn`/`abap.utcl`\) literals, the prefixes `date`, `time`, or `timestamp` can be used.

Here's an example:

> ### Sample Code:  
> ```sql
> SQL> SELECT 'HELLO'                                  AS C_CHAR5,
>             x'123456ABCDEF'                          AS C_RAW6,
>             date'2015-01-02'                         AS C_DATN,
>             time'11:55:00'                           AS C_TIMN,
>             timestamp '2015-01-02 11:55:00.1234567'  AS C_UTCL
> FROM SYS.DUMMY
> 
> +--------+-------------+---------+---------+----------------------------+
> | C_CHAR5| C_RAW6      | C_DATN  | C_TIMN  | C_UTCL                     |
> +--------+-------------+---------+---------+----------------------------+
> | HELLO  | 123456ABCDEF| 20150102| 115500  | 2015-01-02T11:55:00,1234567|
> +--------+-------------+---------+---------+----------------------------+
> ```

As an alternative for `DATE`/`TIME`/`TIMESTAMP`, you can use ODBC escape sequences, which are also supported in HANA SQL:

> ### Sample Code:  
> ```sql
> SQL> SELECT {d '2015-01-02'}                    AS C_DATN,
>             {t '11:55:00'}                      AS C_TIMN,
>             {ts '2015-01-02 11:55:00.1234567'}  AS C_UTCL
> FROM SYS.DUMMY
> 
> +---------+---------+----------------------------+
> | C_DATN  | C_TIMN  | C_UTCL                     |
> +---------+---------+----------------------------+
> | 20150102| 115500  | 2015-01-02T11:55:00,1234567|
> +---------+---------+----------------------------+
> 
> ```

