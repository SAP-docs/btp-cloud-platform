<!-- loio6921b788f7e64e599fb0871623def46d -->

# IF\_BALI\_FREE\_TEXT\_GETTER

If a free text is read from an application log, an object instance of interface `IF_BALI_FREE_TEXT_GETTER` is returned. It contains the interface `IF_BALI_ITEM_GETTER`.

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

\(from IF\_BALI\_ITEM\_GETTER\)



</td>
<td valign="top">

Category of the item

Contains fixed value: IF\_BALI\_CONSTANTS=\>C\_CATEGORY\_FREE\_TEXT



</td>
</tr>
<tr>
<td valign="top">

LOG\_ITEM\_NUMBER

\(from IF\_BALI\_ITEM\_GETTER\)



</td>
<td valign="top">

Serial number which is the position of the free text in the log



</td>
</tr>
<tr>
<td valign="top">

SEVERITY

\(from IF\_BALI\_ITEM\_GETTER\)



</td>
<td valign="top">

Severity of the free text \('Error', 'Warning', etc\)



</td>
</tr>
<tr>
<td valign="top">

DETAIL\_LEVEL

\(from IF\_BALI\_ITEM\_GETTER\)



</td>
<td valign="top">

Detail level of the free text \(number between '1' and '9' or ' '\)



</td>
</tr>
<tr>
<td valign="top">

TIMESTAMP

\(from IF\_BALI\_ITEM\_GETTER\)



</td>
<td valign="top">

UTC time stamp of the free text creation



</td>
</tr>
</table>

**Public Methods**



Get the content of the free text:

**GET\_MESSAGE\_TEXT \(from interface IF\_BALI\_ITEM\_GETTER\)**


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

MESSAGE\_TEXT



</td>
<td valign="top">

Content of the free text



</td>
</tr>
</table>

