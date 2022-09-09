<!-- loio5359a35b78334d5fb94a69dbd710d52a -->

# XLSX Read Access

The starting point for programmatically reading the content of an XLSX document is to obtain a read access for the document. This document shows how this is done.

> ### Caution:  
> Note that when data is read from a given XLSX document via the XCO XLSX module, the data is provided in exactly the way it's stored within the XLSX document. This implies that no security or any other kind of additional validations are performed against the data contained in the worksheets of the XLSX workbook when it's accessed by the means described below. Please ensure that when the read data is further processed by application logic \(for example, stored in a database table or shown in a Fiori app\), dedicated checks are in place to guard your application against potentially malicious content \(such as string values in an XLSX worksheet containing JavaScript code\).

Consider the following:

> ### Sample Code:  
> ```abap
> DATA lv_file_content TYPE xstring.
>  
> " LV_FILE_CONTENT must be populated with the complete file content of the .XLSX file
> " whose content shall be processed programmatically.
>  
> DATA(lo_read_access) = xco_cp_xlsx=>document->for_file_content( lv_file_content
>   )->read_access( ).
> ```

Once obtained, the next step is to obtain the read access for the worksheet which contains the data that shall be read. It's possible to identify a worksheet based on its name or position:

> ### Sample Code:  
> ```abap
> " Read access for the worksheet at position 1, i.e. the first worksheet in the workbook.
> DATA(lo_first_worksheet) = lo_read_access->get_workbook(
>   )->worksheet->at_position( 1 ).
>  
> " Read access for the worksheet with name INVOICES.
> DATA(lo_invoices_worksheet) = lo_read_access->get_workbook(
>   )->worksheet->for_name( 'INVOICES' ).
> ```



<a name="loio5359a35b78334d5fb94a69dbd710d52a__section_xjb_djh_wtb"/>

## Accessing data via a stream

The first way to gain access to the data stored in a worksheet is by selecting a collection of cells based on a selection pattern \(see [XLSX](xlsx-9b7a0d1.md)=\> *Selection patterns*. This is done via method SELECT on IF\_XCO\_XLSX\_RA\_WORKSHEET. Accessing the cells contained in the selection is done following a stream-based approach, meaning a dedicated stream is obtained for the selection which will provide sequential access to the individual blocks of the selection. Two kinds of streams are offered:

-   Cell stream: A cell stream provides access to the selection one cell at a time, traversing the selection from left to right and top to bottom

-   Row stream: A row stream provides access to the selection one row at a time, traversing the selection from top to bottom




### Cell streams

Cell streams are intended for dynamic reading scenarios where it's required to process each cell individually. As such, the following operations are offered for cell streams:

-   Visit: The visit operation takes a visitor implementation as the input \(an object of type IF\_XCO\_XLSX\_RA\_CS\_VISITOR\) which defines the logic that shall be performed for each cell. This construction follows the `Visitor` design pattern.


Consider the following example of how a visit operation can be obtained and executed:

> ### Sample Code:  
> ```abap
> " A selection pattern that was obtained via XCO_CP_XLSX_SELECTION=>PATTERN_BUILDER.
> DATA lo_selection_pattern TYPE REF TO if_xco_xlsx_slc_pattern.
>  
> " The read access to the worksheet.
> DATA lo_worksheet TYPE REF TO if_xco_xlsx_ra_worksheet.
>  
> " The implementation of the visitor, e.g. a dedicated local class containing the
> " logic that shall be performed for each visited cell.
> DATA lo_visitor TYPE REF TO if_xco_xlsx_ra_cs_visitor.
>  
> lo_worksheet->select( lo_selection_pattern
>   )->cell_stream(
>   )->operation->visit( lo_visitor
>   )->if_xco_xlsx_ra_operation~execute( ).
> ```



### Row streams

Row streams are best used when the structure of the data that shall be read is statically known. The primary use case is to read a portion of a worksheet \(as identified by a selection\) into an internal table. As such, the following operations are offered for row streams:

-   Write To: The write to operation takes a reference to an internal table as the input to which the selected data shall be written \(upon execution of the operation\)


Consider the following example of how a write to operation can be obtained and executed:

> ### Sample Code:  
> ```abap
> " A selection pattern that was obtained via XCO_CP_XLSX_SELECTION=>PATTERN_BUILDER.
> DATA lo_selection_pattern TYPE REF TO if_xco_xlsx_slc_pattern.
>  
> " The read access to the worksheet.
> DATA lo_worksheet TYPE REF TO if_xco_xlsx_ra_worksheet.
>  
> " The type definition resembling the structure of the rows in the worksheet selection.
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
>   )->operation->write_to( REF #( lt_rows )
>   )->if_xco_xlsx_ra_operation~execute( ).
>  
> " At this point, the internal table LT_ROWS will contain the rows from the worksheet
> " selection.
> ```



<a name="loio5359a35b78334d5fb94a69dbd710d52a__section_htf_hkh_wtb"/>

## Accessing data via a cursor

An alternative to accessing the data in a worksheet via selections and stream is to obtain a cursor for a worksheet read access via method CURSOR on IF\_XCO\_XLSX\_RA\_WORKSHEET. Just as with desktop office suites, a cursor can first be positioned on any given cell \(identified by coordinate values for both the column and row of the cell\). Afterwards, it can be moved around the worksheet freely via the methods on IF\_XCO\_XLSX\_RA\_CURSOR:

-   Methods MOVE\_UP, MOVE\_RIGHT, MOVE\_DOWN and MOVE\_LEFT can be used to move the cursor relative to its current position by the given number of steps

-   Methods SET\_COLUMN and SET\_ROW can be used to set the new column or row for the cursor

-   Method HAS\_CELL can be used to determine if the underlying worksheet contains a cell for the current position of the cursor. If so, it can be accessed via method GET\_CELL


The following example illustrates how the string values of the cells in column A starting at row 5 can be read out until the first row is encountered for which the worksheet has no cell or the cell has no value:

> ### Sample Code:  
> ```abap
> " The read access to the worksheet.
> DATA lo_worksheet TYPE REF TO if_xco_xlsx_ra_worksheet.
>  
> DATA(lo_cursor) = lo_worksheet->cursor(
>   io_column = xco_cp_xlsx=>coordinate->for_alphabetic_value( 'A' )
>   io_row    = xco_cp_xlsx=>coordinate->for_numeric_value( 5 )
> ).
>  
> WHILE lo_cursor->has_cell( ) EQ abap_true
>     AND lo_cursor->get_cell( )->has_value( ) EQ abap_true.
>   DATA(lo_cell) = lo_cursor->get_cell( ).
>  
>   DATA(lv_string_value) = ``.
>   lo_cell->get_value(
>     )->set_transformation( xco_cp_xlsx_read_access=>value_transformation->string_value
>     )->write_to( REF #( lv_string_value ) ).
>  
>   " At this point LV_STRING_VALUE contains the string value of the cell
>   " at the current position of the cursor.
>  
>   " Move the cursor down one row.
>   lo_cursor->move_down( ).
> ENDWHILE.
> ```



<a name="loio5359a35b78334d5fb94a69dbd710d52a__section_vrx_qkh_wtb"/>

## Value transformations

When accessing the value of an individual cell \(via IF\_XCO\_XLSX\_RA\_CELL\_VALUE\) or of a complete row \(as part of a row stream operation\), it's possible to apply transformations to the value, which will affect how the cell value is written to an ABAP data field. Technically, a value transformation \(obtainable via XCO\_CP\_XLSX\_READ\_ACCESS=\>VALUE\_TRANSFORMATION\) encapsulates a transformation routine that can be applied to

-   Values of individual cells \(in case the value transformation implements the interface IF\_XCO\_XLSX\_RA\_VT\_CELL\_VALUE\)

-   Values of rows \(in case the value transformation implements the interface IF\_XCO\_XLSX\_RA\_VT\_ROW\_VALUE\)


The following value transformations are currently offered:

-   Identity

-   String value

-   Best effort


The default value transformation is the best effort value transformation. It can be overwritten using

-   Method SET\_VALUE\_TRANSFORMATION of IF\_XCO\_XLSX\_RA\_CELL\_VALUE when the value of an individual cell is read

-   Method SET\_VALUE\_TRANSFORMATION of IF\_XCO\_XLSX\_RA\_RS\_OP\_WRITE\_TO when row values are read and written to an internal table as part of the write to row stream operation




### 'Identity' value transformation

The 'identity' value transformation doesn't apply any modification to the XLSX type or value of a cell. As such, the ABAP field that the cell value shall be written to must be fully compliant with the type and value of the cell as it's stored in the XLSX file.



### 'String value' value transformation

The 'string value' value transformation gets the stringified value of any cell such that it can always be safely written to an ABAP field of type STRING.



### 'Best effort' value transformation

The 'best effort' value transformation is based on an inspection \(based on ABAP runtime type services\) of the ABAP field that a given cell value shall be written to. Based on the type determined for the target ABAP field a transformation is applied to the cell value. The 'best effort' value transformation behaves just as the 'identity' value transformation except for the following types of ABAP fields:

-   D: When a cell value is written to an ABAP date field the value of the cell is interpreted as a date and it is converted to the ABAP date format

-   T: When a cell value is written to an ABAP time field the value of the cell is interpreted as a time and it is converted to the ABAP time format

-   Data element MSEHI: When a cell value is written to an ABAP field typed against data element MSEHI the cell value is interpreted as the external value for a unit of measurement which is converted to the internal ABAP format using conversion routine CUNIT

-   Data element SPRAS: When a cell value is written to an ABAP field typed against data element SPRAS the cell value is interpreted as the external value for a language which is converted to the internal ABAP format using conversion routine ISOLA


