<!-- loio83c9ad55ceb040a8bf3827a573773f43 -->

# CL\_BALI\_HEADER\_SETTER \(Interface IF\_BALI\_HEADER\_SETTER\)

Class `CL_BALI_HEADER_SETTER` is used to set the header attributes of an application log, such as the log object, subobject, and the external identifier. The public interface of the instance methods is `IF_BALI_HEADER_SETTER`.

**Public Methods**



Create an instance of the header class with the settings of the descriptor \(object, subobject and external identifier\):

<a name="loio83c9ad55ceb040a8bf3827a573773f43__table_xkf_sjb_xlb"/>**CREATE \(static\)**


<table>
<tr>
<th>

Name



</th>
<th>

Description



</th>
</tr>
<tr>
<td colspan="2">

**Importing parameters**



</td>
</tr>
<tr>
<td>

OBJECT



</td>
<td>

Object of the log



</td>
</tr>
<tr>
<td>

SUBOBJECT



</td>
<td>

Subobject of the log



</td>
</tr>
<tr>
<td>

EXTERNAL\_ID



</td>
<td>

\(Optional\): External identifier of the log

Default: ' '



</td>
</tr>
<tr>
<td colspan="2">

**Returning parameter**



</td>
</tr>
<tr>
<td>

HEADER



</td>
<td>

Header object: A reference to interface IF\_BALI\_HEADER\_SETTER



</td>
</tr>
<tr>
<td colspan="2">

**Exceptions \(inherit from CX\_BALI\_RUNTIME\)**



</td>
</tr>
<tr>
<td>

CX\_BALI\_NOT\_POSSIBLE



</td>
<td>

ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>OBJECT\_NOT\_ALLOWED:

Access to the log object is not allowed



</td>
</tr>
<tr>
<td>

CX\_BALI\_INVALID\_PARAMETER



</td>
<td>

The log object or subobject of the header doesn't exist



</td>
</tr>
</table>



Set object, subobject and external identifier of the log:

<a name="loio83c9ad55ceb040a8bf3827a573773f43__table_ism_nzh_xlb"/>**SET\_DESCRIPTOR**


<table>
<tr>
<th>

Name



</th>
<th>

Description



</th>
</tr>
<tr>
<td colspan="2">

**Importing parameters**



</td>
</tr>
<tr>
<td>

OBJECT



</td>
<td>

Object of the log



</td>
</tr>
<tr>
<td>

SUBOBJECT



</td>
<td>

Subobject of the log



</td>
</tr>
<tr>
<td>

EXTERNAL\_ID



</td>
<td>

\(Optional\): External identifier of the log

Default: ' '



</td>
</tr>
<tr>
<td colspan="2">

**Returning parameter**



</td>
</tr>
<tr>
<td>

NEW\_HEADER



</td>
<td>

Reference to current header object



</td>
</tr>
<tr>
<td colspan="2">

**Exceptions \(inherit from CX\_BALI\_RUNTIME\)**



</td>
</tr>
<tr>
<td>

CX\_BALI\_NOT\_POSSIBLE



</td>
<td>

ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>OBJECT\_NOT\_ALLOWED:

Access to the log object is not allowed



</td>
</tr>
<tr>
<td>

CX\_BALI\_INVALID\_PARAMETER



</td>
<td>

The log object or subobject of the header doesn't exist



</td>
</tr>
</table>



Set the expiry date and attributes:

<a name="loio83c9ad55ceb040a8bf3827a573773f43__table_yfn_5zh_xlb"/>**SET\_EXPIRY**


<table>
<tr>
<th>

Name



</th>
<th>

Description



</th>
</tr>
<tr>
<td colspan="2">

**Importing parameters**



</td>
</tr>
<tr>
<td>

EXPIRY\_DATE



</td>
<td>

Date when the log expires and can be deleted. If the parameter is initial, the expiry date remains unchanged; the default value of the expiry date is the creation date of the log + 7 days.



</td>
</tr>
<tr>
<td>

KEEP\_UNTIL\_EXPIRY



</td>
<td>

\(Optional\): If set: It is not allowed to delete the log before the expiry date

Default: Not set



</td>
</tr>
<tr>
<td colspan="2">

**Returning parameter**



</td>
</tr>
<tr>
<td>

NEW\_HEADER



</td>
<td>

Reference to current header object



</td>
</tr>
</table>



Get all header values:

<a name="loio83c9ad55ceb040a8bf3827a573773f43__table_lbw_d13_xlb"/>**GET\_ALL\_VALUES**


<table>
<tr>
<th>

Name



</th>
<th>

Description



</th>
</tr>
<tr>
<td colspan="2">

**Exporting parameters**



</td>
</tr>
<tr>
<td>

OBJECT



</td>
<td>

Object of the log



</td>
</tr>
<tr>
<td>

SUBOBJECT



</td>
<td>

Subobject of the log



</td>
</tr>
<tr>
<td>

EXTERNAL\_ID



</td>
<td>

External identifier of the log



</td>
</tr>
<tr>
<td>

EXPIRY\_DATE



</td>
<td>

Date when the log expires and can be deleted



</td>
</tr>
<tr>
<td>

KEEP\_UNTIL\_EXPIRY



</td>
<td>

If set: It is not allowed to delete the log before the expiry date



</td>
</tr>
</table>

