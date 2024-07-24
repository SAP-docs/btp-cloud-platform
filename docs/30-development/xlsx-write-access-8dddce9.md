<!-- loio8dddce9fd9954e72a09d2b39d22db995 -->

# XLSX Write Access

The starting point for programmatically writing the content of an XLSX document is to get a write access for the document. Find out how this is done.



## Context

You can create a new, empty XLSX document and get write access for it like this:

> ### Sample Code:  
> ```abap
> DATA(lo_write_access) = xco_cp_xlsx=>document->empty( )->write_access( ).
> ```

An empty XLSX document consists of one worksheet named `Sheet1` which you can access via

> ### Sample Code:  
> ```abap
> 
> DATA(lo_worksheet) = lo_write_access->get_workbook(
>   )->worksheet->at_position( 1 ).
> ```

You can populate it with data using the means described below. Once the worksheet has been filled as desired, you can get the corresponding file content of the document as an XSTRING via

> ### Sample Code:  
> ```abap
> DATA(lv_file_content) = lo_write_access->get_file_content( ).
> ```

Adding a new worksheet works like this:

> ### Sample Code:  
> ```abap
> DATA(lo_worksheet) = lo_write_access->get_workbook(
>   )->add_new_sheet( ).
> ```

You can provide a name for the sheet by filling the optional parameter `iv_name`.



<a name="loio8dddce9fd9954e72a09d2b39d22db995__section_xlz_dmn_1vb"/>

## Writing Data via a Stream

The first way how you can write data into a worksheet is by selecting a collection of cells based on a selection pattern \(see also the section *Selection patterns* here: [XLSX](xlsx-9b7a0d1.md)\) via the method `SELECT` on `IF_XCO_XLSX_WA_WORKSHEET`. Accessing the cells contained in the selection is done following a stream-based approach, which means that a dedicated stream is obtained for the selection that will provide sequential access to the individual blocks of the selection. One kind of stream is currently offered:

-   Row stream: A row stream provides access to the selection one row at a time, traversing the selection from top to bottom




### Row streams

Row streams are best used when the structure of the data that should be written is statically known. The primary use case is to write the rows of an internal table into a corresponding portion of the worksheet \(as identified by a selection\). The following operations are offered for row streams:

-   Write From: The write from operation takes a reference to an internal table as the input whose rows will be written to the selected rows in the worksheet \(upon running the operation\)

Consider the following example of how a write from operation can be obtained and run:

> ### Sample Code:  
> ```abap
> " A selection pattern that was obtained via XCO_CP_XLSX_SELECTION=>PATTERN_BUILDER.
> DATA lo_selection_pattern TYPE REF TO if_xco_xlsx_slc_pattern.
>  
> " The write access to the worksheet.
> DATA lo_worksheet TYPE REF TO if_xco_xlsx_wa_worksheet.
>  
> " The type definition for the internal table.
> TYPES:
>   BEGIN OF ts_row,
>     first_name   TYPE string,
>     last_name    TYPE string,
>     day_of_birth TYPE d,
>   END OF ts_row,
>  
>   tt_row TYPE STANDARD TABLE OF ts_row WITH DEFAULT KEY.
>  
> DATA lt_rows TYPE tt_row.
>  
> lo_worksheet->select( lo_selection_pattern
>   )->row_stream(
>   )->operation->write_from( REF #( lt_rows )
>   )->execute( ).
>  
> " At this point, the rows of internal table LT_ROWS will have been written into the
> " worksheet selection.
> ```



<a name="loio8dddce9fd9954e72a09d2b39d22db995__section_q2s_54n_1vb"/>

## Writing Data via a Cursor

An alternative to writing data into a worksheet via selections and streams is to get a cursor for a worksheet write access using the method `CURSOR` on `IF_XCO_XLSX_WA_WORKSHEET`. Just as with desktop office suites, you can position a cursor on any given cell \(identified by coordinate values for both the column and row of the cell\). Afterwards, you can move it around the worksheet freely via the methods on `IF_XCO_XLSX_WA_CURSOR`:

-   You can use the methods `MOVE_UP`, `MOVE_RIGHT`, `MOVE_DOWN` and `MOVE_LEFT` to move the cursor relative to its current position by the given number of steps
-   You can use the methods `SET_COLUMN` and `SET_ROW` to set the new column or row for the cursor
-   Method `GET_CELL` provides access to the cell at the current position of the cursor

The following example illustrates how the current date and time \(stored in ABAP variables `LV_DATE` and `LV_TIME`\) can be written into a worksheet:

> ### Sample Code:  
> ```abap
> " The write access to the worksheet.
> DATA lo_worksheet TYPE REF TO if_xco_xlsx_wa_worksheet.
>  
> DATA(lo_cursor) = lo_worksheet->cursor(
>   io_column = xco_cp_xlsx=>coordinate->for_alphabetic_value( 'B' )
>   io_row    = xco_cp_xlsx=>coordinate->for_numeric_value( 2 )
> ).
>  
> " Write the current date.
> lo_cursor->get_cell( )->value->write_from( 'Date:' ).
>  
> DATA(lv_date) = CONV d( xco_cp=>sy->date( )->as( xco_cp_time=>format->abap )->value ).
> lo_cursor->move_right( )->get_cell( )->value->write_from( lv_date ).
>  
> " Write the current time.
> lo_cursor->move_down( )->move_left( )->get_cell( )->value->write_from( 'Time:' ).
>  
> DATA(lv_time) = CONV t( xco_cp=>sy->time( )->as( xco_cp_time=>format->abap )->value ).
> lo_cursor->move_right( )->get_cell( )->value->write_from( lv_time ).
> ```

For an otherwise empty worksheet, this will produce the following content:

****


<table>
<tr>
<th valign="top">

 

</th>
<th valign="top">

A

</th>
<th valign="top">

B

</th>
<th valign="top">

C

</th>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

2

</td>
<td valign="top">

 

</td>
<td valign="top">

Date:

</td>
<td valign="top">

$LV\_DATE$

</td>
</tr>
<tr>
<td valign="top">

3

</td>
<td valign="top">

 

</td>
<td valign="top">

Time:

</td>
<td valign="top">

$LV\_TIME$

</td>
</tr>
</table>

where $LV\_DATE$ is the current date and $LV\_TIME$ is the current time.



<a name="loio8dddce9fd9954e72a09d2b39d22db995__section_fl3_tpn_1vb"/>

## Value Transformations

When writing the value of an individual cell \(via `IF_XCO_XLSX_WA_CELL_VALUE`\) or of a complete row \(as part of a row stream operation\) it's possible to apply transformations to the value, which will affect what XLSX value is written to the cell in the worksheet. Technically, a value transformation that you can get using the method `XCO_CP_XLSX_WRITE_ACCESS=>VALUE_TRANSFORMATION` contains a transformation routine that can be applied to

-   Values of individual cells \(in case the value transformation implements the interface `IF_XCO_XLSX_WA_VT_CELL_VALUE`\)
-   Values of rows \(in case the value transformation implements the interface `IF_XCO_XLSX_WA_VT_ROW_VALUE`\)

The following value transformations are currently offered:

-   Best effort

The default value transformation is the best effort value transformation. Value transformations can be set explicitly via the following methods:

-   Method `SET_VALUE_TRANSFORMATION` of `IF_XCO_XLSX_WA_CELL_VALUE` when the value of an individual cell is written
-   Method `SET_VALUE_TRANSFORMATION` of `IF_XCO_XLSX_WA_RS_OP_WRITE_FRM` when row values are written as part of the write from row stream operation



### "Best effort" value transformation

The **best effort** value transformation is based on an inspection \(based on ABAP runtime type services\) of the ABAP field that should be written to a given cell. Based on the type determined for the ABAP field, a transformation is applied to the value before it's written to the cell of the worksheet. The **best effort** value transformation provides support for the following types of ABAP fields:

-   Type `ABAP_BOOL`: When an ABAP field of type `ABAP_BOOL` is written to a cell, a boolean value will be written to the worksheet
-   D: When an ABAP field of type D is written to a cell, a date value will be written to the worksheet
-   T: When an ABAP field of type T is written to a cell, a time value will be written to the worksheet
-   Data element `MSEHI`: When an ABAP field typed against data element `MSEHI` is written to a cell, the external value of the corresponding unit of measurement as determined by conversion routine `CUNIT` will be written to the worksheet
-   Data element `SPRAS`: When an ABAP field typed against data element`SPRAS` is written to a cell, the external value of the corresponding language as determined by conversion routine `ISOLA` will be written to the worksheet
-   C, N and `STRING`: When an ABAP field of type C, N or `STRING` is written to a cell, a string value will be written to the worksheet
-   I, INT8 and P: When an ABAP field of type I, INT8 or P is written to a cell, a numeric value will be written to the worksheet

If an attempt is made to write an ABAP field of any other type to a cell of a worksheet using the best effort value transformation, you can expect a runtime error.

