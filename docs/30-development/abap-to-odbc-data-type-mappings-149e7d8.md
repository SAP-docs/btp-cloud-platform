<!-- loio149e7d8017314322b14fdfebb06098d6 -->

# ABAP to ODBC Data Type Mappings

The ODBC driver for ABAP allows you to configure the mapping of ABAP data types to ODBC SQL data types.



To configure this mapping, you can use the connection parameter `Typemap`. Regardless of the ODBC SQL data type reported by the ODBC driver, the ODBC application is still free to use an ODBC C data type of its choice to retrieve a given ODBC SQL data type.



## Typemap=semantic

In most cases, you want to retrieve the ABAP data in a way that’s easy to consume. With the `Typemap=semantic` configuration, the ODBC driver can do the following:

-   Map all date like data types like `abap.dats` and `abap.datn` to ODBC type `SQL_DATE`/ `SQL_TYPE_DATE`

-   Map all time like data types like `abap.tims` and `abap.timn` to ODBC type `SQL_DATE/SQL_TYPE_DATE`

-   Map all decimal floating point-like data types like `abap.d16n`, `abap.d34n`, `abap.d16r`, `abap.d34r`, `abap.d16d`, and `abap.d34d` to ODBC type `SQL_DECFLOAT`

-   Perform an automatic decimal shift for type `abap.curr` and maps this data type also to ODBC type `SQL_DECFLOAT`

-   Perform an ISO conversion for type `abap.lang` and maps this data type to ODBC type `SQL_WCHAR` with length 2




<a name="loio149e7d8017314322b14fdfebb06098d6__section_n5f_z1n_4wb"/>

## Typemap=semanticDatsTimsAsWchar

For some ODBC applications that want to safely access the ABAP data, the `Typemap=semantic` configuration might have the problem that not all data in the old `abap.dats` and `abap.tims` columns can be mapped to a date. The ABAP system doesn’t prevent that some applications store date/time literals in those columns \(for example, the string `TODAY` in an `abap.dats` column\).

To ensure that these use cases work without data loss, a slightly different `Typemap=semanticDatsTimsAsWchar` is available. This type mapping is similar to the semantic type mapping, with the exception that the ABAP data type `abap.dats` is mapped to `SQL_WCHAR` with length 8 and ABAP data type`abap.tims` is mapped to `SQL_WCHAR` with length 6. As a result, no conversions happen, and no potential conversion errors occur.



<a name="loio149e7d8017314322b14fdfebb06098d6__section_g5t_y1n_4wb"/>

## Typemap=native

Other applications might want to read data from an ABAP system as-is without any semantic conversion. With the `Typemap=native` configuration, the ODBC driver does the following:

-   Map data type `abap.dats` to ODBC type `SQL_WCHAR` with length 8

-   Map data type `abap.datn` to ODBC type `SQL_DATE/SQL_TYPE_DATE`

-   Map data type `abap.tims` to ODBC type `SQL_WCHAR` with length 6

-   Map data type `abap.timn` to ODBC type `SQL_TIME/SQL_TYPE_TIME`

-   Map data types `abap.d16n` and `abap.d34n` to ODBC type `SQL_DECFLOAT`

-   Map data types `abap.d16r` and `abap.d34r` to ODBC type `SQL_BINARY`

-   Map data types `abap.d16d` and `abap.d34d` to ODBC type `SQL_DECIMAL`

-   Not shift `abap.curr` data and maps of this type to ODBC type `SQL_DECIMAL`

-   Return ABAP type `abap.lang` as is and map it to ODBC type `SQL_WCHAR` with length 1


All other ABAP data types are mapped to their corresponding ODBC SQL types independent of the typemap setting, such as the following, for example:


<table>
<tr>
<th valign="top">

ABAP Data Type

</th>
<th valign="top">

Mapped ODBC SQL Type

</th>
</tr>
<tr>
<td valign="top">

`INT1/INT2`

</td>
<td valign="top">

`SQL_SMALLINT`

</td>
</tr>
<tr>
<td valign="top">

`INT4`

</td>
<td valign="top">

`SQL_INTEGER`

</td>
</tr>
<tr>
<td valign="top">

`INT8`

</td>
<td valign="top">

`SQL_BIGINT`

</td>
</tr>
<tr>
<td valign="top">

`DEC`

</td>
<td valign="top">

`SQL_NUMERIC`

</td>
</tr>
<tr>
<td valign="top">

`UTCL`

</td>
<td valign="top">

`SQL_TIMESTAMP/SQL_TYPE_TIMESTAMP`

</td>
</tr>
</table>

