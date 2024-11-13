<!-- loiof6be5a9b0d124920b51c626f2e7669cf -->

# CL\_BALI\_EXCEPTION\_SETTER \(Interface IF\_BALI\_EXCEPTION\_SETTER\)

To add a new exception to an application log, an object of class `CL_BALI_EXCEPTION_SETTER` is used. The public interface of the instance methods is `IF_BALI_EXCEPTION_SETTER`. It contains the interface `IF_BALI_ITEM_SETTER`.

**Public Attributes**


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

CATEGORY

\(from IF\_BALI\_ITEM\_SETTER\)

</td>
<td valign="top">

Category of the item

Contains fixed value: IF\_BALI\_CONSTANTS=\>C\_CATEGORY\_EXCEPTION

</td>
</tr>
</table>

**Public Methods**



Create an instance of the exception class. Set the reference of the ABAP exception which is stored in the exception item and its severity:

**CREATE \(static\)**


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top" colspan="2">

**Importing parameters**

</td>
</tr>
<tr>
<td valign="top">

SEVERITY

</td>
<td valign="top">

\(Optional\): Severity of the message \('Error', 'Warning', etc\)

Default: IF\_BALI\_CONSTANTS=\>C\_SEVERITY\_STATUS

</td>
</tr>
<tr>
<td valign="top">

EXCEPTION

</td>
<td valign="top">

Reference to ABAP exception class instance

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Returning parameter**

</td>
</tr>
<tr>
<td valign="top">

EXCEPTION\_OBJ

</td>
<td valign="top">

Exception object: A reference to interface IF\_BALI\_EXCEPTION\_SETTER

</td>
</tr>
</table>



Set the ABAP exception class instance and severity:

**SET\_EXCEPTION**


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top" colspan="2">

**Importing parameters**

</td>
</tr>
<tr>
<td valign="top">

SEVERITY

</td>
<td valign="top">

\(Optional\): Severity of the message \('Error', 'Warning', etc\)

Default: IF\_BALI\_CONSTANTS=\>C\_SEVERITY\_STATUS

</td>
</tr>
<tr>
<td valign="top">

EXCEPTION

</td>
<td valign="top">

Reference to ABAP exception class instance

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Returning parameter**

</td>
</tr>
<tr>
<td valign="top">

NEW\_EXCEPTION\_OBJ

</td>
<td valign="top">

Reference to current application log exception object

</td>
</tr>
</table>



Set the level of detail of the exception:

**SET\_DETAIL\_LEVEL**


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top" colspan="2">

**Importing parameter**

</td>
</tr>
<tr>
<td valign="top">

DETAIL\_LEVEL

</td>
<td valign="top">

Detail level of the exception

Allowed values: Number between '1' and '9' or ' '

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Returning parameter**

</td>
</tr>
<tr>
<td valign="top">

NEW\_EXCEPTION\_OBJ

</td>
<td valign="top">

Reference to current application log exception object

</td>
</tr>
</table>



Set the exception context using a data dictionary structure:

**SET\_CONTEXT**


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top" colspan="2">

**Importing parameter**

</td>
</tr>
<tr>
<td valign="top">

CONTEXT

</td>
<td valign="top">

Structure with the context data

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Returning parameter**

</td>
</tr>
<tr>
<td valign="top">

NEW\_EXCEPTION\_OBJ

</td>
<td valign="top">

Reference to the current application log exception object

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Exceptions \(inherit from CX\_BALI\_RUNTIME\)**

</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_INVALID\_PARAMETER

</td>
<td valign="top">

-   Field `CONTEXT` is not based on a database table or structure that is defined in the data dictionary

-   The total size of field `CONTEXT` is longer than 256 characters




</td>
</tr>
</table>



Get all exception values:



**GET\_ALL\_VALUES**


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top" colspan="2">

**Exporting parameters**

</td>
</tr>
<tr>
<td valign="top">

DETAIL\_LEVEL

</td>
<td valign="top">

Detail level of the exception \(number between '1' and '9' or ' '\)

</td>
</tr>
<tr>
<td valign="top">

SEVERITY

</td>
<td valign="top">

Severity of the exception \('Error', 'Warning', etc\)

</td>
</tr>
<tr>
<td valign="top">

EXCEPTION

</td>
<td valign="top">

Reference to ABAP exception class instance

</td>
</tr>
<tr>
<td valign="top">

CONTEXT\_DATA

</td>
<td valign="top">

Structure and content of the context. `CONTEXT_DATA` has the following fields:

-   `STRUCTURE_NAME`: Name of the data dictionary structure which was used for the context data

-   `CONTENT`: The content of the context data. The content is stored in a character field with a length of 256 characters




</td>
</tr>
</table>



Check whether the exception can pass an item filter:

**CHECK\_PASSING\_ITEM\_FILTER \(from IF\_BALI\_ITEM\_SETTER\)**


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top" colspan="2">

**Importing parameter**

</td>
</tr>
<tr>
<td valign="top">

ITEM\_FILTER

</td>
<td valign="top">

Reference to the item filter that is being checked

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Returning parameter**

</td>
</tr>
<tr>
<td valign="top">

FILTER\_PASSED

</td>
<td valign="top">

If set, the exception can pass the item filter

</td>
</tr>
</table>



> ### Note:  
> If the severity of the exception contains a value which is not allowed, it is changed to `IF_BALI_CONSTANTS=>C_SEVERITY_DEFAULT`. Allowed values of the severity can be found in interface `IF_BALI_CONSTANTS`.
> 
> If the detail level of the exception contains a value which is not allowed, it is changed to `IF_BALI_CONSTANTS=>C_DETAIL_LEVEL_DEFAULT`. Allowed values of the detail level are a number between '1' and '9' and ' '.

