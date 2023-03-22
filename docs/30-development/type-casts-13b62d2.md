<!-- loio13b62d2839134cc494dcb9eb90b242ac -->

# Type Casts

You can also use type casts in the SQL dialect of the ABAP SQL service.



You can always insert type casts in ABAP CDS style directly in the definition of your exposed CDS entities. However, sometimes you may want to insert type casts in your SQL queries, for example, to make some data types better consumable or readable in standard ODBC applications.

The supported type casts in the SQL dialect of the ABAP SQL service are more HANA SQL-like. It’s only possible to cast to a limited number of ABAP types. The general form of a type cast is the following, where `<expression>` can be an SQL expression, a literal value, or a column:

> ### Sample Code:  
> ```sql
> CAST( <expression> AS <data type> )
> ```

`<data type>` can be one of the data types from the second column of the following table:


<table>
<tr>
<th valign="top">

 



</th>
<th valign="top">

Data Type in Cast



</th>
<th valign="top">

Corresponding ABAP Data Type



</th>
</tr>
<tr>
<td valign="top">

Integer data types



</td>
<td valign="top">

`SMALLINT`, `INTEGER`, `BIGINT`



</td>
<td valign="top">

`abap.int2`, `abap.int4`, `abap.int8`



</td>
</tr>
<tr>
<td valign="top">

Fixed-point decimal types



</td>
<td valign="top">

`DECIMAL( p, s )` where `p` <= 31 and `s` <= 14



</td>
<td valign="top">

`abap.dec(p,s)`



</td>
</tr>
<tr>
<td valign="top">

Double



</td>
<td valign="top">

`DOUBLE`



</td>
<td valign="top">

`abap.double`



</td>
</tr>
<tr>
<td valign="top">

Character-like types



</td>
<td valign="top">

`CHAR(n)` where `n` <=255

Synonyms: `VARCHAR(n)`, `NVARCHAR(n)`



</td>
<td valign="top">

`abap.char(n)`



</td>
</tr>
<tr>
<td valign="top">

Decimal floating point types



</td>
<td valign="top">

`DECIMAL`, `SMALLDECIMAL`



</td>
<td valign="top">

`abap.df34n`, `abap.df16n`



</td>
</tr>
</table>

A character string can be cast to an abap.string using the `TO_CLOB( <expression> )` function. A binary string can be cast to an `abap.xstring` using the `TO_BLOB( <expression> )` function. There are no special casts to date, time, or timestamp data types and also no type casts for some of the ABAP-specific data types like `abap.numc`, `abap.curr`,`abap.cuky`, and so on.

Here's an example:

> ### Sample Code:  
> ```sql
> select      CAST( 4711 AS SMALLINT ) AS C_INT2,
>             CAST( 4711 AS INTEGER ) AS C_INT4,
>             CAST( 1E-1200 AS DECIMAL) AS C_DF34N,
>             CAST( 1.234 AS DECIMAL(10,3))  AS C_DEC103,
>             CAST( 2.5 AS DOUBLE) AS C_DOUBLE
> FROM SYS.DUMMY
> 
> ```

