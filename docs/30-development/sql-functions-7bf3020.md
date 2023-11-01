<!-- loio7bf302022e7a493eadf0998850c194d5 -->

# SQL Functions

Most of the supported built-in scalar and aggregate ABAP SQL functions can be used, but there are some limitations.



## General Comments

Since the SQL dialect of the ABAP SQL service is eventually processed by the ABAP SQL engine, most of the supported built-in scalar ABAP SQL functions can be used.

In some of the date/time functions, ABAP data type names are reflected in the function names, as in the following example:

> ### Sample Code:  
> ```sql
> SQL> SELECT date'20150102'                      AS C_DATN,
>             ADD_DAYS( date'20150102', 5 )       AS C_DATN_P_5, 
>             DATN_ADD_DAYS( date'20150102', 10 ) AS C_DATN_P_10,
>             DATS_FROM_DATN( date'20150102')     AS C_DATS
> FROM SYS.DUMMY
> 
> +----------+----------+----------+----------+
> | C_DATN   | C_DATN_5 | C_DATN_10| C_DATS   |
> +----------+----------+----------+----------+
> | 20150102 | 20150107 | 20150120 | 20150102 |
> +----------+----------+----------+----------+
> 
> ```

The functions `DATS_FROM_DATN`, `DATS_TO_DATN`, `BINTOHEX`, and `HEXTOBIN` can also be used for type casting.

Apart from scalar functions, ABAP SQL aggregate functions and ABAP SQL windowing functions can also be used in the SQL dialect of the ABAP SQL service.

It’s not possible to access associations using path expressions in the SQL dialect of the ABAP SQL service. Columns of associated entities can only be accessed if they're explicitly exposed using a column name in the CDS view entity.



<a name="loio7bf302022e7a493eadf0998850c194d5__section_sgx_fcz_qwb"/>

## Limitations for Built-In Functions

For the SQL dialect of the ABAP SQL service, the following limitations apply:

**String Functions**


<table>
<tr>
<th valign="top">

Function

</th>
<th valign="top">

Supported

</th>
<th valign="top">

Comments

</th>
</tr>
<tr>
<td valign="top">

LIKE\_REGEXPR

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Only supported as comparison operator, the `case_sensitive` parameter is not supported.

Different syntax: `LIKE_REGEXPR pcre`

</td>
</tr>
<tr>
<td valign="top">

LOCATE\_REGEXPR

</td>
<td valign="top">

Yes

</td>
<td valign="top">

The `case_sensitive` parameter is not supported.

Different syntax: `LOCATE_REGEXPR( pcre IN value [FROM start] [OCCURRENCE occ] [GROUP group] )`

</td>
</tr>
<tr>
<td valign="top">

LOCATE\_REGEXPR\_AFTER

</td>
<td valign="top">

Yes

</td>
<td valign="top">

The `case_sensitive` parameter is not supported.

Different syntax: `LOCATE_REGEXPR( AFTER pcre IN value [FROM start] [OCCURRENCE occ] [GROUP group] )`

</td>
</tr>
<tr>
<td valign="top">

OCCURENCES\_REGEXPR

</td>
<td valign="top">

Yes

</td>
<td valign="top">

The `case_sensitive` parameter is not supported.

Different syntax: `OCCURRENCES_REGEXPR( pcre IN value )`

</td>
</tr>
<tr>
<td valign="top">

REPLACE\_REGEXPR

</td>
<td valign="top">

Yes

</td>
<td valign="top">

The `case_sensitive` parameter is not supported.

Different syntax: `REPLACE_REGEXPR( pcre IN sql_exp1 WITH sql_exp2 [FROM start] [OCCURRENCE occ])`

</td>
</tr>
<tr>
<td valign="top">

SUBSTRING\_REGEXPR

</td>
<td valign="top">

Yes

</td>
<td valign="top">

The `case_sensitive` parameter is not supported.

Different syntax: `SUBSTRING_REGEXPR( pcre IN value [FROM start] [OCCURRENCE occ] [GROUP group] )`

</td>
</tr>
</table>

**Time Zone Functions**


<table>
<tr>
<th valign="top">

Function

</th>
<th valign="top">

Supported

</th>
<th valign="top">

Commens

</th>
</tr>
<tr>
<td valign="top">

ABAP\_SYSTEM\_TIMEZONE

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Only with default parameters, named parameters are not supported.

</td>
</tr>
<tr>
<td valign="top">

ABAP\_USER\_TIMEZONE

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Only with default parameters, named parameters are not supported.

</td>
</tr>
</table>

The following conversion functions are not supported:

-   UNIT\_CONVERSION

-   CURRENCY\_CONVERSION




<a name="loio7bf302022e7a493eadf0998850c194d5__section_qkv_kcz_qwb"/>

## More Information

For more information about the ABAP SQL functions, see the ABAP SQL documentation.

