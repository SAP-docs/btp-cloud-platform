<!-- loio759b29b4509841bcb381212621bef9c2 -->

# IF\_BALI\_HEADER\_GETTER

If the header attributes of an application log are read, they are returned in an object which uses interface `IF_BALI_HEADER_GETTER`.

**Public Attributes**


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

LOG\_TIMESTAMP



</td>
<td>

UTC time stamp of the log \(usually the creation time\)



</td>
</tr>
<tr>
<td>

LOG\_USER



</td>
<td>

Log user \(usually the user who created the log\)



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

**Public Methods**



Get description text of the log object in the logon language:

<a name="loio759b29b4509841bcb381212621bef9c2__table_xkf_sjb_xlb"/>**GET\_OBJECT\_DESCRIPTION**


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

**Returning parameter**



</td>
</tr>
<tr>
<td>

OBJECT\_DESCRIPTION



</td>
<td>

Description of the object in the logon language



</td>
</tr>
</table>



Get description text of log subobject in the logon language:

<a name="loio759b29b4509841bcb381212621bef9c2__table_ork_czn_xlb"/>**GET\_SUBOBJECT\_DESCRIPTION**


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

**Returning parameter**



</td>
</tr>
<tr>
<td>

SUBOBJECT\_DESCRIPTION



</td>
<td>

Description of the subobject in the logon language



</td>
</tr>
</table>

