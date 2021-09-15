<!-- loiof8387789309344baafcf9a05bbe8059c -->

# CL\_BALI\_FREE\_TEXT\_SETTER \(Interface IF\_BALI\_FREE\_TEXT\_SETTER\)

To add a new free text to an application log, an object of class `CL_BALI_FREE_TEXT_SETTER` is used. The public interface of the instance methods is `IF_BALI_FREE_TEXT_SETTER`. It contains the interface `IF_BALI_ITEM_SETTER`.

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

CATEGORY

\(from IF\_BALI\_ITEM\_SETTER\)



</td>
<td>

Category of the item

Contains fixed value: IF\_BALI\_CONSTANTS=\>C\_CATEGORY\_FREE\_TEXT



</td>
</tr>
</table>

**Public Methods**



Create an instance of the free text class and set the text and the severity:

<a name="loiof8387789309344baafcf9a05bbe8059c__table_xkf_sjb_xlb"/>**CREATE \(static\)**


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

SEVERITY



</td>
<td>

\(Optional\): Severity of the message \('Error', 'Warning', etc\)

Default: IF\_BALI\_CONSTANTS=\>C\_SEVERITY\_STATUS



</td>
</tr>
<tr>
<td>

TEXT



</td>
<td>

Free text



</td>
</tr>
<tr>
<td colspan="2">

**Returning parameter**



</td>
</tr>
<tr>
<td>

FREE\_TEXT



</td>
<td>

Free text object: A reference to interface IF\_BALI\_FREE\_TEXT\_SETTER



</td>
</tr>
</table>



Set the free text and severity:

<a name="loiof8387789309344baafcf9a05bbe8059c__table_y1j_lvn_xlb"/>**SET\_TEXT**


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

SEVERITY



</td>
<td>

\(Optional\): Severity of the message \('Error', 'Warning', etc\)

Default: IF\_BALI\_CONSTANTS=\>C\_SEVERITY\_STATUS



</td>
</tr>
<tr>
<td>

TEXT



</td>
<td>

Free text



</td>
</tr>
<tr>
<td colspan="2">

**Returning parameter**



</td>
</tr>
<tr>
<td>

NEW\_FREE\_TEXT



</td>
<td>

Reference to current free text object



</td>
</tr>
</table>



Set the level of detail of the free text:

<a name="loiof8387789309344baafcf9a05bbe8059c__table_jqx_pvn_xlb"/>**SET\_DETAIL\_LEVEL**


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

**Importing parameter**



</td>
</tr>
<tr>
<td>

DETAIL\_LEVEL



</td>
<td>

Detail level of the free text

Allowed values: Number between '1' and '9' or ' '



</td>
</tr>
<tr>
<td colspan="2">

**Returning parameter**



</td>
</tr>
<tr>
<td>

NEW\_FREE\_TEXT



</td>
<td>

Reference to current free text object



</td>
</tr>
</table>



Get all free text values:

<a name="loiof8387789309344baafcf9a05bbe8059c__table_qfw_xvn_xlb"/>**GET\_ALL\_VALUES**


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

DETAIL\_LEVEL



</td>
<td>

Detail level of the free text

Number between '1' and '9' or ' '



</td>
</tr>
<tr>
<td>

SEVERITY



</td>
<td>

Severity of the free text \('Error', 'Warning', etc\)



</td>
</tr>
<tr>
<td>

TEXT



</td>
<td>

Content of the free text



</td>
</tr>
</table>



> ### Note:  
> If the severity of the free text contains a value which is not allowed, it is changed to `IF_BALI_CONSTANTS=>C_SEVERITY_DEFAULT`. Allowed values of the severity can be found in interface `IF_BALI_CONSTANTS`.
> 
> If the detail level of the free text contains a value which is not allowed, it is changed to `IF_BALI_CONSTANTS=>C_DETAIL_LEVEL_DEFAULT`. Allowed values of the detail level are a number between '1' and '9' and ' '.

