<!-- loio9b7a0d1e35524abba3b6fcb206851b95 -->

# XLSX

The XCO XLSX module offers a set of standard abstractions and APIs to programmatically work with XLSX workbooks and their worksheets \(e.g. coming form an uploaded Microsoft Excel .XLSX file\).



The XCO XLSX module exposes three external APIs:

-   XCO\_CP\_XLSX: Access to general abstractions used throughout the XCO XLSX module

-   XCO\_CP\_XLSX\_SELECTION: Access to selection pattern builders used to build selection patterns

-   XCO\_CP\_XLSX\_READ\_ACCESS: Access to abstractions used when reading the content of an XLSX worksheet




<a name="loio9b7a0d1e35524abba3b6fcb206851b95__section_opf_4gh_wtb"/>

## Document handles

The starting point for any programmatic interaction with an XLSX workbook and its worksheets is obtaining a handle for the containing document via XCO\_CP\_XLSX=\>DOCUMENT. As of now, document handles can be obtained for the complete file content of an .XLSX file, which must be provided as an XSTRING:

> ### Sample Code:  
> ```abap
> DATA lv_file_content TYPE xstring.
>  
> " LV_FILE_CONTENT must be populated with the complete file content of the .XLSX file
> " whose content shall be processed programmatically.
>  
> DATA(lo_document) = xco_cp_xlsx=>document->for_file_content( lv_file_content ).
> ```

The obtained document handle then allows to obtain a read access, which is the starting point for accessing the cell contents of the worksheets contained in the document [XLSX Read Access](xlsx-read-access-5359a35.md).



<a name="loio9b7a0d1e35524abba3b6fcb206851b95__section_rzl_zgh_wtb"/>

## Coordinates

Within the XCO XLSX module, a worksheet is regarded as a space with two dimensions, with the first dimension being the column and the second dimension being the row. Consequently, a cell in a worksheet is uniquely determined by providing values for its column and row. A coordinate \(an object of type CL\_XCO\_XLSX\_COORDINATE\) uniquely fixes a value for a given dimension, for example, for a value for a column or row. In office suites, e.g. Microsoft Excel, alphabetic values are used to identify columns and numeric values are used to identify rows. The XCO XLSX module provides support for both variants so that alphabetic as well as numeric values can be used freely when values are provided for columns and rows.

-   Alphabetic coordinates: A, B, C, … Z, AA, AB, ...ZZ, AAA, AAB, ...

-   Numeric coordinates: 1, 2, 3, ...


Coordinates can be obtained via XCO\_CP\_XLSX=\>COORDINATE for both alphabetic and numeric values and once obtained, both the alphabetic as well as the numeric value can be retrieved for a coordinate. This also provides an easy way to translate between alphabetic and numeric coordinate values, for example:

> ### Sample Code:  
> ```abap
> DATA(lo_coordinate_1) = xco_cp_xlsx=>coordinate->for_alphabetic_value( 'AA' ).
>  
> " LV_COORD_1_NUMERIC_VALUE will be an integer with value 27.
> DATA(lv_coord_1_numeric_value) = lo_coordinate_1->get_numeric_value( ).
>  
> " LV_COORD_1_ALPHABETIC_VALUE will be a string with value AA.
> DATA(lv_coord_1_alphabetic_value) = lo_coordinate_1->get_alphabetic_value( ).
>  
> DATA(lo_coordinate_2) = xco_cp_xlsx=>coordinate->for_numeric_value( 27 ).
>  
> " LV_COORD_2_NUMERIC_VALUE will be an integer with value 27.
> DATA(lv_coord_2_numeric_value) = lo_coordinate_2->get_numeric_value( ).
>  
> " LV_COORD_2_ALPHABETIC_VALUE will be a string with value AA.
> DATA(lv_coord_2_alphabetic_value) = lo_coordinate_2->get_alphabetic_value( ).
> ```

It's possible to derive new coordinates from existing coordinates such as objects of type CL\_XCO\_XLSX\_COORDINATE, by using the SHIFT method to either increment or decrement the value of the coordinate \(depending on the sign of the provided offset\).



<a name="loio9b7a0d1e35524abba3b6fcb206851b95__section_dpc_rhh_wtb"/>

## Selection patterns

Selections are a central concept within the XCO XLSX module. A selection is based on a selection pattern which encapsulates a prescription according to which individual cells are identified in a given worksheet which then form the selection. To illustrate the concepts and offered selection patterns consider the following exemplary portion of an XLSX worksheet:


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
<th valign="top">

D



</th>
<th valign="top">

E



</th>
<th valign="top">

F



</th>
<th valign="top">

...



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
<td valign="top">

 



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

1



</td>
<td valign="top">

2



</td>
<td valign="top">

3



</td>
<td valign="top">

4



</td>
<td valign="top">

 



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

3



</td>
<td valign="top">

 



</td>
<td valign="top">

5



</td>
<td valign="top">

6



</td>
<td valign="top">

7



</td>
<td valign="top">

8



</td>
<td valign="top">

 



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

4



</td>
<td valign="top">

 



</td>
<td valign="top">

9



</td>
<td valign="top">

10



</td>
<td valign="top">

11



</td>
<td valign="top">

12



</td>
<td valign="top">

 



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

5



</td>
<td valign="top">

 



</td>
<td valign="top">

13



</td>
<td valign="top">

14



</td>
<td valign="top">

15



</td>
<td valign="top">

16



</td>
<td valign="top">

 



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

6



</td>
<td valign="top">

 



</td>
<td valign="top">

 



</td>
<td valign="top">

 



</td>
<td valign="top">

 



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

...



</td>
<td valign="top">

 



</td>
<td valign="top">

 



</td>
<td valign="top">

 



</td>
<td valign="top">

 



</td>
<td valign="top">

 



</td>
<td valign="top">

 



</td>
<td valign="top">

 



</td>
</tr>
</table>

For the purposes of the following code samples, it's assumed that except for the cell values shown above, all other cells of the worksheet are initial. Supported selection patterns can be built via selection pattern builders which are obtainable via XCO\_CP\_XLSX\_SELECTION=\>PATTERN\_BUILDER.



<a name="loio9b7a0d1e35524abba3b6fcb206851b95__section_u2c_33h_wtb"/>

## Simple from-to selection patterns

A simple from-to selection pattern allows to define static boundary values for columns and rows. It's not required to specify a boundary value for each dimension, hence both bounded and unbounded selections are possible. Consider the following characteristic examples:

> ### Sample Code:  
> ```abap
> " The selection pattern LO_PATTERN_1 will be a bounded rectangle, matching values
> " 6, 7, 10 and 11 of the above worksheet.
> DATA(lo_pattern_1) = xco_cp_xlsx_selection=>pattern_builder->simple_from_to(
>   )->from_column( xco_cp_xlsx=>coordinate->for_alphabetic_value( 'C' )
>   )->to_column( xco_cp_xlsx=>coordinate->for_alphabetic_value( 'D' )
>   )->from_row( xco_cp_xlsx=>coordinate->for_numeric_value( 3 )
>   )->to_row( xco_cp_xlsx=>coordinate->for_numeric_value( 4 )
>   )->get_pattern( ).
>  
> " The selection pattern LO_PATTERN_2 will be unbounded at the bottom, matching
> " values 6, 7, 10, 11, 14 and 15 of the above worksheet.
> DATA(lo_pattern_2) = xco_cp_xlsx_selection=>pattern_builder->simple_from_to(
>   )->from_column( xco_cp_xlsx=>coordinate->for_alphabetic_value( 'C' )
>   )->to_column( xco_cp_xlsx=>coordinate->for_alphabetic_value( 'D' )
>   )->from_row( xco_cp_xlsx=>coordinate->for_numeric_value( 3 )
>   )->get_pattern( ).
>  
> " The selection pattern LO_PATTERN_3 will be unbounded at the bottom and at the
> " right, matching values 6, 7, 8, 10, 11, 12, 14, 15 and 16 of the above worksheet.
> DATA(lo_pattern_3) = xco_cp_xlsx_selection=>pattern_builder->simple_from_to(
>   )->from_column( xco_cp_xlsx=>coordinate->for_alphabetic_value( 'C' )
>   )->from_row( xco_cp_xlsx=>coordinate->for_numeric_value( 3 )
>   )->get_pattern( ).
>  
> " The selection pattern LO_PATTERN_4 is completely unbounded, matching all cells of the
> " worksheet, hence also all values of the above worksheet.
> DATA(lo_pattern_4) = xco_cp_xlsx_selection=>pattern_builder->simple_from_to(
>   )->get_pattern( ).
> ```

