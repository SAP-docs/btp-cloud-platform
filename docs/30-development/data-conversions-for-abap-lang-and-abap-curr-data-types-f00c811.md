<!-- loiof00c81191b154f96ac4875b552cb5603 -->

# Data Conversions for abap.lang and abap.curr Data Types

There’s a special handling of ABAP data types `LANG` and `CURR` in the ODBC driver.



<a name="loiof00c81191b154f96ac4875b552cb5603__section_knj_whn_4wb"/>

## abap.lang Data Type

In ABAP tables, `abap.lang` data is stored as single-byte Unicode character \(for example, `D` for German or `E` for English\). However, in external interfaces \(for example, the SAP logon screen\), the language is typically shown as two-character string \(for example, `DE` for German or `EN` for English\). The table `T002` in the ABAP back-end system defines the mapping between these values.

If you're using one of the `Typemap=semantic*` settings, `abap.lang` values in the result set of a query are automatically mapped to the 2-character strings. Conversely, if you're using `abap.lang` values as input parameters, you must provide them as 2-character strings. The same SQL queries return different `abap.lang` values and need different `abap.lang` input values if `Typemap=native` is used.



## abap.curr Data Type

The `abap.curr` data type has been developed in times where no decimal floating point data type existed. For historic reasons, on database level, `abap.curr` data is stored in fixed-point decimal values. These values can only be interpreted correctly if the corresponding `abap.cuky` value is known. The fixed-point decimal values need to be shifted depending on its currency key. For an innocent or generic ODBC application that doesn't know the ABAP shifting algorithm, it comes handy that the ODBC driver for ABAP directly returns the shifted `abap.curr` values. As a price, a fixed-point decimal data type can no longer hold values for all possible currencies. Therefore, the ODBC driver for ABAP returns shifted `abap.curr` values as decimal floating point \(ODBC data type `SQL_DECFLOAT`\) if one of the `Typemap=semantic*` settings is used.

The following example uses `Typemap=semantic`:

> ### Sample Code:  
> ```sql
> SQL> SELECT LANG, CUKY, CURR from ZData.TestView
> 
> +------+------+-------------------------------------------+
> | LANG | CUKY | CURR                                      |
> +------+------+-------------------------------------------+
> | EN   | USD  | 9999999999999.99                          |
> | DE   | EUR  | 0.01                                      |
> | LT   | BHD  | 1234.5                                    |
> +------+------+-------------------------------------------+
> 
> ```

The following example uses `Typemap=native`:

> ### Sample Code:  
> ```sql
> SQL> SELECT LANG, CUKY, CURR from ZData.TestView
> 
> +------+------+------------------+
> | LANG | CUKY | CURR             |
> +------+------+------------------+
> | E    | USD  | 9999999999999.99 |
> | D    | EUR  | 0.01             |
> | X    | BHD  | 12345.00         |
> +------+------+------------------+
> 
> ```

The examples here demonstrate different query results with and without active language conversion and currency shift. Note the changed values for column `LANG`, the change in data type for column `CURR`, and the shifted decimal point in the currency value for currency `BHD`. Currency values for currencies `USD` and `EUR` are stored unshifted in the ABAP database tables.

It’s also possible to use shifted `abap.curr` values as input values for SQL queries if they correspond to predicates on a CDS entity column. However, you can’t use shifted `abap.curr` values as input parameters for CDS entities with parameters. In this case, the corresponding `abap.cuky` value can’t be automatically determined.

