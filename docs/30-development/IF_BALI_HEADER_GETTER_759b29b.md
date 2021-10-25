<!-- loio759b29b4509841bcb381212621bef9c2 -->

# IF\_BALI\_HEADER\_GETTER

If the header attributes of an application log are read, they are returned in an object which uses interface `IF_BALI_HEADER_GETTER`.

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

LOG\_TIMESTAMP



</td>
<td valign="top">

UTC time stamp of the log \(usually the creation time\)



</td>
</tr>
<tr>
<td valign="top">

LOG\_USER



</td>
<td valign="top">

Log user \(usually the user who created the log\)



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
</table>

**Public Methods**



Get description text of the log object in the logon language:

<a name="loio759b29b4509841bcb381212621bef9c2__table_xkf_sjb_xlb"/>**GET\_OBJECT\_DESCRIPTION**


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

**Returning parameter**



</td>
</tr>
<tr>
<td valign="top">

OBJECT\_DESCRIPTION



</td>
<td valign="top">

Description of the object in the logon language



</td>
</tr>
</table>



Get description text of log subobject in the logon language:

<a name="loio759b29b4509841bcb381212621bef9c2__table_ork_czn_xlb"/>**GET\_SUBOBJECT\_DESCRIPTION**


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

**Returning parameter**



</td>
</tr>
<tr>
<td valign="top">

SUBOBJECT\_DESCRIPTION



</td>
<td valign="top">

Description of the subobject in the logon language



</td>
</tr>
</table>

