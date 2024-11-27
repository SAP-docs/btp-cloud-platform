<!-- loio69da3f86a5e24bd986d3125db1fe9238 -->

# API for Consumption of Business Rules

The purpose of the CL\_FDT\_FUNCTION\_PROCESS\_API is to enable consumption of BRF+ \(Business Rule Framework plus\) rules within the ABAP Cloud development environment. It acts as a bridge between your application and BRF+ functions\(rules\).

The following table shows methods in CL\_FDT\_FUNCTION\_PROCESS\_API class:


<table>
<tr>
<th valign="top">

Method

</th>
<th valign="top">

Parameter

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top" rowspan="4">

`Get_Content_List`

This method is used to get the list of context elements for BRFplus function.

</td>
<td valign="top">

Importing: `IV_FUNCTION_ID`

</td>
<td valign="top">

ID of the function to be processed.

</td>
</tr>
<tr>
<td valign="top">

Importing: `V_TIMESTAMP`:

</td>
<td valign="top">

The timestamp parameter specifies the data retrieval or function evaluation time. Without a timestamp, the function returns the context list at the current date and time.

</td>
</tr>
<tr>
<td valign="top">

Importing: `IV_TRACE_GENERATION` 

</td>
<td valign="top">

This Boolean indicates that the trace should be generated with a lean trace or not.

</td>
</tr>
<tr>
<td valign="top">

Exporting: `ET_CONTEXT_LIST`

</td>
<td valign="top">

The exporting parameter is a table containing the function's context list, which includes the id, name, and data object type of each context.

</td>
</tr>
<tr>
<td valign="top" rowspan="6">

`GET_CONTEXT_VALUE`

This method is used to get the value of the context object of a BRFplus function in a referenced object.

</td>
<td valign="top">

Importing: `IV_FUNCTION_ID` 

</td>
<td valign="top">

ID of the function to be processed.

</td>
</tr>
<tr>
<td valign="top">

Importing:`IV_DATA_OBJECT` 

</td>
<td valign="top">

A character-like parameter that specifies the name or ID of the data object involved in the function call.

</td>
</tr>
<tr>
<td valign="top">

Importing: `IV_TIMESTAMP` 

</td>
<td valign="top">

The timestamp parameter specifies the point in time for data retrieval or function evaluation. If no timestamp is provided, the function returns the context value at the current date and time.

</td>
</tr>
<tr>
<td valign="top">

Importing: `IV_TRACE_GENERATION` 

</td>
<td valign="top">

This Boolean indicates that the trace should be generated with a lean trace or not.

</td>
</tr>
<tr>
<td valign="top">

Exporting: `EV_DATA` 

</td>
<td valign="top">

This parameter exports the data object's actual value after function execution. Its type "ANY" indicates flexibility to handle any data type, expanding the function's return possibilities.

</td>
</tr>
<tr>
<td valign="top">

Exporting: `ER_DATA`

</td>
<td valign="top">

This exporting parameter references the data object, enabling its manipulation or examination beyond the function call.

</td>
</tr>
<tr>
<td valign="top" rowspan="7">

`GET_DATA_OBJECT_REFERENCE`

This method is used to get the data reference of a context object in BRFplus function.

</td>
<td valign="top">

Importing: `IV_FUNCTION_ID`

</td>
<td valign="top">

ID of the function to be processed.

</td>
</tr>
<tr>
<td valign="top">

Importing: `IV_DATA_OBJECT`:

</td>
<td valign="top">

Importing: IV\_DATA\_OBJECT: A character-like parameter that specifies the name or ID of the data object involved in the function call.

</td>
</tr>
<tr>
<td valign="top">

Importing: `IV_DATA_OBJECT` 

</td>
<td valign="top">

A character-like parameter that specifies the name or ID of the data object involved in the function call.

</td>
</tr>
<tr>
<td valign="top">

Importing: `IV_TIMESTAMP` 

</td>
<td valign="top">

Importing: IV\_TIMESTAMP: The timestamp parameter specifies a specific point in time for data retrieval or function evaluation. If no timestamp is provided, all function context in a referenced object at the current date and time is returned.

</td>
</tr>
<tr>
<td valign="top">

Importing: `IV_TRACE_GENERATION` 

</td>
<td valign="top">

Importing: IV\_TRACE\_GENERATION: This Boolean indicates that the trace should be generated with a lean trace or not.

</td>
</tr>
<tr>
<td valign="top">

Exporting:

`EV_DATA_OBJECT_NAME`

</td>
<td valign="top">

This parameter exports the technical name of the data object involved in the operation, providing metadata such as its name or identifier.

</td>
</tr>
<tr>
<td valign="top">

Exporting `ER_DATA` 

</td>
<td valign="top">

This exporting parameter provides a reference to the data object. It does not contain an actual value but rather a pointer to the data object.

</td>
</tr>
<tr>
<td valign="top" rowspan="7">

`MOVE_DATA_TO_DATA_OBJECT`

This method is used to pass data from external source to BRFplus function’s context.

</td>
<td valign="top">

Importing: `IR_DATA` 

</td>
<td valign="top">

This is a reference to any ABAP data object. It allows the method to directly interact with ABAP data objects provided by the calling program, offering a flexible interface for data processing.

</td>
</tr>
<tr>
<td valign="top">

Importing: `IV_FUNCTION_ID` 

</td>
<td valign="top">

ID of the function to be processed.

</td>
</tr>
<tr>
<td valign="top">

Importing: `IV_DATA_OBJECT`:

</td>
<td valign="top">

A character-like parameter that specifies the name or ID of the data object involved in the function call.

</td>
</tr>
<tr>
<td valign="top">

Importing: `IV_TIMESTAMP` 

</td>
<td valign="top">

The timestamp parameter is used to define a specific point in time for the data retrieval or function evaluation. If no time stamp is provided, then it takes current date and time.

</td>
</tr>
<tr>
<td valign="top">

Importing: `IV_TRACE_GENERATION`

</td>
<td valign="top">

This Boolean indicates that the trace should be generated with a lean trace or not.

</td>
</tr>
<tr>
<td valign="top">

Importing: `IV_HAS_DDIC_BINDING` 

</td>
<td valign="top">

Indicates whether the data passed to the method confirms to a DDIC \(Data Dictionary\) structure as defined in BRF+.

</td>
</tr>
<tr>
<td valign="top">

Exporting: `ER_DATA` 

</td>
<td valign="top">

This exporting parameter exports a reference to a BRFplus data object. This allows the method to return a data object that can be further manipulated or evaluated outside the method.

</td>
</tr>
<tr>
<td valign="top" rowspan="6">

`PROCESS `

With this method, a BRFplus function can be processed. You can specify a timestamp for the function to be processed so you can simulate the system behavior as it would have been at that point. Also, you can decide whether the trace for the function execution shall be saved in database for later reference or not.

</td>
<td valign="top">

Importing: `IV_FUNCTION_ID` 

</td>
<td valign="top">

ID of the function to be processed.

</td>
</tr>
<tr>
<td valign="top">

Importing: `IV_TIMESTAMP`

</td>
<td valign="top">

The timestamp parameter is used to define a specific point in time for the data retrieval or function evaluation. If no time stamp is provided, the result of the function at the current date and time is returned.

</td>
</tr>
<tr>
<td valign="top">

Importing: `IV_TRACE_MODE`

</td>
<td valign="top">

Indicates the modes of trace. By default, mode is ‘L’ \(Lean Trace\).

</td>
</tr>
<tr>
<td valign="top">

Importing: `: IV_SAVE_TRACE`

</td>
<td valign="top">

Indicates whether the trace generated for current processing of the Function should be saved in database.

</td>
</tr>
<tr>
<td valign="top">

Importing:`IT_ID_VALUE` 

</td>
<td valign="top">

Table of ID/value pairs \(ID/reference to value for each context element\). From a performance perspective, this is the most efficient way of triggering the processing of BRFplus. Also, using this parameter requires that you know the IDs of the context elements that you want to pass.

</td>
</tr>
<tr>
<td valign="top">

Exporting: `EA_RESULT`

</td>
<td valign="top">

Exporting: EA\_RESULT:

A variable of a type that is compatible with the result data object of the BRFplus function. You can get an ABAP data object of this type \(a reference\) by calling method`CL_FDT_FUNCTION_PROCESS_API ->IF_FDT_FUNCTION_PROCESS_API~GET_DATA_OBJECT_REFERENCE`.

</td>
</tr>
</table>

