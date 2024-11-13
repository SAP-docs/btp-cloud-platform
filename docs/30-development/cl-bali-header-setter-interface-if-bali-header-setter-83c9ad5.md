<!-- loio83c9ad55ceb040a8bf3827a573773f43 -->

# CL\_BALI\_HEADER\_SETTER \(Interface IF\_BALI\_HEADER\_SETTER\)

Class `CL_BALI_HEADER_SETTER` is used to set the header attributes of an application log, such as the log object, subobject, and the external identifier. The public interface of the instance methods is `IF_BALI_HEADER_SETTER`.

**Public Methods**



Create an instance of the header class with the settings of the descriptor \(object, subobject and external identifier\):

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

OBJECT

</td>
<td valign="top">

Object of the log

</td>
</tr>
<tr>
<td valign="top">

SUBOBJECT

</td>
<td valign="top">

Subobject of the log

If no subobjects were defined for the log object, the parameter should be empty

</td>
</tr>
<tr>
<td valign="top">

EXTERNAL\_ID

</td>
<td valign="top">

\(Optional\): External identifier of the log

Default: ' '

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Returning parameter**

</td>
</tr>
<tr>
<td valign="top">

HEADER

</td>
<td valign="top">

Header object: A reference to interface IF\_BALI\_HEADER\_SETTER

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Exceptions \(inherit from CX\_BALI\_RUNTIME\)**

</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_NOT\_POSSIBLE

</td>
<td valign="top">

ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>OBJECT\_NOT\_ALLOWED:

Access to the log object is not allowed

</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_INVALID\_PARAMETER

</td>
<td valign="top">

The log object or subobject of the header doesn't exist

</td>
</tr>
</table>



Set object, subobject and external identifier of the log:

**SET\_DESCRIPTOR**


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

OBJECT

</td>
<td valign="top">

Object of the log

</td>
</tr>
<tr>
<td valign="top">

SUBOBJECT

</td>
<td valign="top">

Subobject of the log

</td>
</tr>
<tr>
<td valign="top">

EXTERNAL\_ID

</td>
<td valign="top">

\(Optional\): External identifier of the log

Default: ' '

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Returning parameter**

</td>
</tr>
<tr>
<td valign="top">

NEW\_HEADER

</td>
<td valign="top">

Reference to current header object

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Exceptions \(inherit from CX\_BALI\_RUNTIME\)**

</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_NOT\_POSSIBLE

</td>
<td valign="top">

ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>OBJECT\_NOT\_ALLOWED:

Access to the log object is not allowed

</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_INVALID\_PARAMETER

</td>
<td valign="top">

The log object or subobject of the header doesn't exist

</td>
</tr>
</table>



Set the expiry date and attributes:

**SET\_EXPIRY**


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

EXPIRY\_DATE

</td>
<td valign="top">

Date when the log expires and can be deleted. If the parameter is initial, the expiry date remains unchanged; the default value of the expiry date is the creation date of the log + 7 days.

</td>
</tr>
<tr>
<td valign="top">

KEEP\_UNTIL\_EXPIRY

</td>
<td valign="top">

\(Optional\): If set: It is not allowed to delete the log before the expiry date

Default: Not set

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Returning parameter**

</td>
</tr>
<tr>
<td valign="top">

NEW\_HEADER

</td>
<td valign="top">

Reference to current header object

</td>
</tr>
</table>



Set the log context using a data dictionary structure:

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

**Returning parameters**

</td>
</tr>
<tr>
<td valign="top">

NEW\_HEADER

</td>
<td valign="top">

Reference to current header object

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Exceptions \(inherit from `CX_BALI_RUNTIME`\)**

</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_INVALID\_PARAMETER

</td>
<td valign="top">

-   Field `CONTEXT` is not based on a database table or structure which is defined in the data dictionary

-   The total size of field `CONTEXT` is longer than 256 characters




</td>
</tr>
</table>



Get all header values:

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

OBJECT

</td>
<td valign="top">

Object of the log

</td>
</tr>
<tr>
<td valign="top">

SUBOBJECT

</td>
<td valign="top">

Subobject of the log

</td>
</tr>
<tr>
<td valign="top">

EXTERNAL\_ID

</td>
<td valign="top">

External identifier of the log

</td>
</tr>
<tr>
<td valign="top">

EXPIRY\_DATE

</td>
<td valign="top">

Date when the log expires and can be deleted

</td>
</tr>
<tr>
<td valign="top">

KEEP\_UNTIL\_EXPIRY

</td>
<td valign="top">

If set: It is not allowed to delete the log before the expiry date

</td>
</tr>
<tr>
<td valign="top">

CONTEXT\_DATA

</td>
<td valign="top">

Structure and content of the context. `CONTEXT_DATA` has the following fields:

-   `STRUCTURE_NAME`: Name of the data dictionary structure which was used for the context data

-   `CONTENT`: The content of the context data, stored in a character field with a length of 256 characters




</td>
</tr>
</table>

