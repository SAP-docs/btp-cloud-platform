<!-- loio40319b1d61284004ad309c42786056f5 -->

# IF\_BALI\_EXCEPTION\_GETTER

If an exception is read from an application log, an object instance of interface `IF_BALI_EXCEPTION_GETTER` is returned. It contains the interface `IF_BALI_ITEM_GETTER`.

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

Contains fixed value: IF\_BALI\_CONSTANTS=\>C\_CATEGORY\_EXCEPTION

</td>
</tr>
<tr>
<td valign="top">

LOG\_ITEM\_NUMBER

\(from IF\_BALI\_ITEM\_GETTER\)

</td>
<td valign="top">

Serial number which is the position of the exception in the log

</td>
</tr>
<tr>
<td valign="top">

SEVERITY

\(from IF\_BALI\_ITEM\_GETTER\)

</td>
<td valign="top">

Severity of the exception \('Error', 'Warning', etc\)

</td>
</tr>
<tr>
<td valign="top">

DETAIL\_LEVEL

\(from IF\_BALI\_ITEM\_GETTER\)

</td>
<td valign="top">

Detail level of the exception \(number between '1' and '9' or ' '\)

</td>
</tr>
<tr>
<td valign="top">

TIMESTAMP

\(from IF\_BALI\_ITEM\_GETTER\)

</td>
<td valign="top">

UTC time stamp of the exception creation

</td>
</tr>
<tr>
<td valign="top">

EXCEPTION\_CLASS

</td>
<td valign="top">

Name of the ABAP exception class

</td>
</tr>
<tr>
<td valign="top">

EXCEPTION\_ID\_NAME

</td>
<td valign="top">

Name of the Text ID of the ABAP exception

</td>
</tr>
</table>

**Public Methods**



Get the message short text of the exception \(the output of method GET\_TEXT of the ABAP exception object\):

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

Message short text of the exception in the logon language

</td>
</tr>
</table>

